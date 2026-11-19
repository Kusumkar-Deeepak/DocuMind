# DocuMind – Project Specification

*A multi-tenant RAG platform with a built-in evaluation dashboard. Python (FastAPI) runs the AI workers; Node.js runs everything else.*

**How to use this document:** save it as `docs/SPEC.md` in the repo root. It is the single source of truth. AI coding agents must build only what is written here.

## 1. Goal

Organizations upload documents and ask questions about them. Answers are grounded in the documents and carry citations. The platform also measures its own answer quality, so every claim on the resume is backed by a number.

**Why this project:** it combines auth, multi-tenancy, queues, hybrid retrieval, caching, rate limiting, observability, evaluation and deployment in one product. Most student RAG projects stop at 'chat with a PDF'.

## 2. Architecture

| Service | Tech | Owns |
| --- | --- | --- |
| **web** | React, Vite, TypeScript, Tailwind, Framer Motion, Recharts | UI only. Talks only to the Node API |
| **api** | Node.js 20, Express, TypeScript, Prisma | Auth, organizations, roles, document metadata, conversations, messages, rate limiting, SSE proxy |
| **rag** | Python 3.11, FastAPI, SQLAlchemy | Parsing, chunking, embeddings, hybrid retrieval, reranking, answer generation, evaluation |
| **worker** | Python, RQ (Redis Queue) | Background ingestion and evaluation jobs |
| **db** | PostgreSQL 16 + pgvector | One database, separate table ownership per service |
| **cache** | Redis 7 | Rate limit counters, query cache, job queue |
| **llm** | Ollama (default) or a hosted API | Generation, embeddings, judge |

**Ownership rule:** each service writes only to its own tables. Services talk over HTTP, never through each other's tables.

```
Browser ──> api (Node) ──HTTP + internal token──> rag (FastAPI) ──> Ollama / LLM API
               │                                     │
               │                                     ├──> Redis (cache, queue) ──> worker
               └──> PostgreSQL (pgvector) <──────────┘
```

**Two kinds of calls from api to rag:**

- Synchronous: `/internal/query` (streams the answer back over SSE).
- Asynchronous: `/internal/ingest` and `/internal/eval/run` return `202`, the worker does the job, then calls back the Node API to update status.

## 3. Feature scope

### Must have (MVP)

1. Register, login, logout with JWT (access token plus refresh token in an httpOnly cookie)
2. Organizations with roles: `admin` and `member`. An admin creates member accounts directly (no email sending)
3. Document upload (PDF, DOCX, TXT) with live status: `queued`, `processing`, `ready`, `failed`
4. Ingestion: parse, chunk, embed, index in vector and keyword form
5. Hybrid retrieval: vector search plus Postgres full-text (BM25-style) search, merged with Reciprocal Rank Fusion, then reranked
6. Chat with streamed answers and clickable citations (file name and page)
7. Redis query cache and per-user rate limiting
8. Evaluation dashboard: test set, runs, metrics, charts
9. Per-query logging: latency per stage, tokens, cache hit, error
10. Docker Compose for local run, GitHub Actions CI, cloud deployment
11. Also the organization have their right to add the api key of the llm for using the system.

### Should have (only after all Must items pass)

- Dark and light theme toggle
- Export a conversation as Markdown

### Out of scope (do not build)

OAuth or social login, email sending, payments, OCR for scanned PDFs, multi-language support, agents or tool calling, fine-tuning, mobile app, real-time collaboration, admin analytics beyond section 8.

## 4. Tech decisions

| Area | Decision |
| --- | --- |
| Embeddings | `nomic-embed-text` via Ollama (768 dimensions). Dimension is set by config and must match the DB column |
| Generation | `llama3.2:3b` via Ollama by default |
| Provider switch | `LLM_PROVIDER=ollama` or `LLM_PROVIDER=api`. One interface class in the rag service. Nothing else knows which is used |
| Reranker | `cross-encoder/ms-marco-MiniLM-L-6-v2` through `sentence-transformers` (runs on CPU) |
| Chunking | Default 800 characters with 100 overlap. Values live in config so the evaluation can compare them |
| Retrieval | Top 20 vector, top 20 keyword, merge with RRF, rerank, keep top 5 for the prompt |
| Streaming | rag service emits SSE, api proxies it, web renders token by token |
| Judge | Same interface as generation. With Ollama the judge is the same model, so note this bias in the README |

## 5. Data model

### Owned by api (Prisma)

| Table | Key fields |
| --- | --- |
| `users` | id, email (unique), password\_hash, name, created\_at |
| `organizations` | id, name, created\_at |
| `memberships` | id, user\_id, org\_id, role (`admin` or `member`) |
| `documents` | id, org\_id, filename, mime\_type, size\_bytes, status, error\_message, uploaded\_by, created\_at |
| `conversations` | id, org\_id, user\_id, title, created\_at |
| `messages` | id, conversation\_id, role (`user` or `assistant`), content, sources (JSON), latency\_ms, cache\_hit, created\_at |

### Owned by rag (SQLAlchemy)

| Table | Key fields |
| --- | --- |
| `chunks` | id, document\_id, org\_id, chunk\_index, page, content, embedding `vector(768)`, tsv `tsvector` |
| `query_logs` | id, org\_id, user\_id, retrieval\_ms, rerank\_ms, generation\_ms, total\_ms, prompt\_tokens, completion\_tokens, cache\_hit, error |
| `eval_sets` | id, org\_id, name, created\_at |
| `eval_questions` | id, eval\_set\_id, question, expected\_answer, expected\_document\_id |
| `eval_runs` | id, eval\_set\_id, config (JSON), status, started\_at, finished\_at |
| `eval_results` | id, eval\_run\_id, question\_id, hit\_at\_5, reciprocal\_rank, faithfulness, relevance, latency\_ms |

**Tenant isolation:** every query on `chunks`, `documents`, `conversations` and eval tables filters by `org_id`. The org id comes from the verified JWT, never from the request body.

## 6. API contracts

### Public API (Node, prefix `/api/v1`)

| Method | Path | Role | Purpose |
| --- | --- | --- | --- |
| POST | `/auth/register` | public | Create user and organization (becomes admin) |
| POST | `/auth/login` | public | Returns access token, sets refresh cookie |
| POST | `/auth/refresh` | cookie | New access token |
| POST | `/auth/logout` | any | Clears cookie |
| POST | `/members` | admin | Create member account |
| GET | `/members` | admin | List members |
| POST | `/documents` | admin | Upload file (multipart), returns 202 |
| GET | `/documents` | any | List documents with status |
| DELETE | `/documents/:id` | admin | Delete document and its chunks |
| GET | `/conversations` | any | List own conversations |
| POST | `/conversations` | any | Create conversation |
| POST | `/conversations/:id/messages` | any | Ask a question, response is an SSE stream |
| GET | `/conversations/:id/messages` | any | History |
| POST | `/eval/sets` | admin | Create test set with questions |
| POST | `/eval/runs` | admin | Start a run with a config |
| GET | `/eval/runs` | admin | List runs with summary metrics |
| GET | `/eval/runs/:id` | admin | Per-question results |
| GET | `/metrics/overview` | admin | Latency, cache hit rate, query count |

**Error format (all endpoints):** `{ "error": { "code": "STRING", "message": "STRING" } }`

### Internal API (FastAPI, never exposed publicly)

Header `X-Internal-Token` is required on every call.

| Method | Path | Purpose |
| --- | --- | --- |
| POST | `/internal/ingest` | Enqueue ingestion for a stored file |
| DELETE | `/internal/documents/:id` | Remove chunks |
| POST | `/internal/query` | Retrieve, rerank, generate, stream SSE |
| POST | `/internal/eval/run` | Enqueue an evaluation run |
| GET | `/internal/health` | Checks DB, Redis and LLM reachability |

Callback from worker to Node: `PATCH /internal/documents/:id/status` with the internal token.

## 7. Core flows

**Ingestion:** upload, Node saves the file to `storage/` and creates a `documents` row (`queued`), Node calls `/internal/ingest`, worker parses, chunks, embeds in batches, inserts chunks, then calls back so status becomes `ready` or `failed` with an error message.

**Query:** Node checks JWT and rate limit, then calls `/internal/query`. The rag service checks the Redis cache (key from org id, normalized question and config version). On a miss it runs both searches, merges, reranks, builds the prompt, streams the answer, then logs timings and tokens. If retrieval returns nothing useful, the answer must say the documents do not contain it. It must not guess.

**Prompt rule:** answer only from the provided context, cite chunk numbers, say so when the context is insufficient.

## 8. Evaluation module

**Inputs:** a test set of at least 50 question and expected-answer pairs, each tagged with the document that contains the answer.

**Metrics per run:**

- Hit@5: was the right document in the top 5 chunks
- MRR: reciprocal rank of the first correct chunk
- Faithfulness: judge scores 1 to 5 on whether the answer is supported by the retrieved context
- Answer relevance: judge scores 1 to 5
- Latency p50 and p95

**Comparisons the dashboard must support:** vector only vs hybrid vs hybrid plus rerank, and at least two chunk sizes. This table is what goes on the resume.

## 9. Design system

**Style:** dark, modern, calm. Think developer tool with a premium finish.

| Token | Value |
| --- | --- |
| Background | `#0B0F1A` |
| Surface | `#121829` |
| Surface raised | `#18203A` |
| Border | `#1F2A44` |
| Primary | `#6366F1` (indigo) |
| Primary hover | `#818CF8` |
| Accent | `#22D3EE` (cyan) |
| Success | `#10B981` |
| Warning | `#F59E0B` |
| Danger | `#EF4444` |
| Text | `#E5E7EB` |
| Muted text | `#94A3B8` |

**Typography:** Inter for UI, JetBrains Mono for code, citations and metrics. Scale 12, 14, 16, 20, 24, 32.

**Shape and spacing:** 8px grid, 12px radius on cards, 8px on inputs and buttons, soft 1px borders, subtle glow on primary buttons.

**Animation rules:**

- Page transition: fade plus 8px slide, 250ms
- Buttons and cards: hover lift of 2px with a 150ms ease-out
- Chat: streaming caret blink, message enters with fade and slide
- Loading: skeleton shimmer, never a bare spinner on a page
- Metrics: count-up numbers, charts animate in once
- Document status badge: pulse while `processing`
- Everything respects `prefers-reduced-motion`

**Accessibility:** text contrast at least 4.5:1, visible focus rings, full keyboard use.

## 10. Screens

1. Login and Register (split layout)
2. Dashboard (document count, queries today, average latency, cache hit rate)
3. Documents (drag and drop upload, status table, delete)
4. Chat (conversation list, streamed answers, citation chips opening a source side panel)
5. Evaluation (test set editor, run configurator, results with comparison charts)
6. Members (admin only)
7. Settings (profile, theme)

Every screen needs loading, empty, error and success states.

## 11. Environment variables

| Variable | Used by | Example |
| --- | --- | --- |
| `DATABASE_URL` | api, rag | `postgresql://user:pass@db:5432/documind` |
| `REDIS_URL` | api, rag, worker | `redis://cache:6379` |
| `JWT_ACCESS_SECRET` | api | long random string |
| `JWT_REFRESH_SECRET` | api | long random string |
| `INTERNAL_TOKEN` | api, rag, worker | long random string |
| `RAG_BASE_URL` | api | `http://rag:8000` |
| `API_BASE_URL` | worker | `http://api:4000` |
| `LLM_PROVIDER` | rag | `ollama` or `api` |
| `OLLAMA_BASE_URL` | rag | `http://host.docker.internal:11434` |
| `GEN_MODEL` | rag | `llama3.2:3b` |
| `EMBED_MODEL` | rag | `nomic-embed-text` |
| `EMBED_DIM` | rag | `768` |
| `LLM_API_KEY` | rag | only if provider is `api` |
| `UPLOAD_DIR` | api, worker | `/data/uploads` (shared volume) |
| `VITE_API_URL` | web | `http://localhost:4000/api/v1` |

No secret is ever committed. Provide `.env.example` with placeholders only.

## 12. Folder structure

```
documind/
├── docs/            SPEC.md, DESIGN.md, PROGRESS.md
├── web/             React app
├── api/             Node.js service
├── rag/             FastAPI service and worker
├── docker-compose.yml
├── .env.example
└── .github/workflows/ci.yml
```

## 13. Build order

| Milestone | Scope | Done when |
| --- | --- | --- |
| M0 | Repo, Docker Compose, Postgres, Redis, health checks | `docker compose up` starts everything, all health endpoints return OK |
| M1 | Auth, orgs, roles in api | Register, login, refresh, role guard tests pass |
| M2 | Upload and ingestion | A PDF goes from `queued` to `ready` and chunks exist in the DB |
| M3 | Retrieval and chat | A question returns a streamed, cited answer from the right document |
| M4 | Cache, rate limit, logging | Repeat question is a cache hit, the 11th request in a minute returns 429 |
| M5 | Evaluation | A run completes and the dashboard shows the comparison table |
| M6 | Frontend integration | Every mocked call replaced by a real call, all states handled |
| M7 | Deploy and polish | Live URL, CI green, README with architecture diagram and demo video |

## 14. Rules for AI coding agents

1. Read this file fully before writing code.
2. Build only what this document lists. If something seems missing, ask. Do not invent it.
3. Do not add dependencies that are not needed for a listed feature. Explain each new dependency before installing it.
4. Do not invent library functions or APIs. Check the installed version's documentation or source first.
5. No fake or placeholder implementations presented as finished. Anything stubbed must be marked `TODO(stub)` and listed in `docs/PROGRESS.md`.
6. Work one milestone at a time. Stop after each for review.
7. Never change the design system or the API contracts without asking.
8. Never hardcode secrets or tenant ids.

## 15. Definition of done

- All Must features work end to end on a clean machine using only the README
- Tenant isolation verified with two organizations
- Evaluation table produced from real runs
- CI passes, app deployed with a public URL
- README has architecture diagram, setup steps, screenshots and measured results
