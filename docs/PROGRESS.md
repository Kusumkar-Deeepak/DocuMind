# DocuMind Implementation Progress

## Milestone Status
- [ ] **M0: Repo, Docker Compose, Postgres, Redis, health checks**
  - Scope: Repo structure, Docker Compose, PostgreSQL (with pgvector), Redis, API health check (`/api/v1/health` or spec internal health), RAG health check (`/internal/health`).
  - Done criteria: `docker compose up` starts everything, all health endpoints return OK.
- [ ] **M1: Auth, orgs, roles in api**
  - Scope: Register, login, refresh, role guards (`admin`, `member`), members management endpoints in Node API.
  - Done criteria: Register, login, refresh, role guard tests pass.
- [ ] **M2: Upload and ingestion**
  - Scope: Document upload (multipart PDF, DOCX, TXT), storage, background ingestion worker (parse, chunk, embed, pgvector + tsv indexing), callback to Node API for status.
  - Done criteria: A PDF goes from `queued` to `ready` and chunks exist in the DB.
- [ ] **M3: Retrieval and chat**
  - Scope: Hybrid retrieval (vector + tsvector Postgres BM25, RRF merge, cross-encoder rerank), answer generation, citations, SSE streaming to Node API and client.
  - Done criteria: A question returns a streamed, cited answer from the right document.
- [ ] **M4: Cache, rate limit, logging**
  - Scope: Redis query cache, per-user rate limiting (10 req/min), query logging (`query_logs` latency, tokens, cache hit).
  - Done criteria: Repeat question is a cache hit, the 11th request in a minute returns 429.
- [ ] **M5: Evaluation**
  - Scope: Test sets, eval runs, metrics calculation (Hit@5, MRR, Faithfulness, Relevance, Latency p50/p95), comparison matrix.
  - Done criteria: A run completes and the dashboard shows the comparison table.
- [ ] **M6: Frontend integration**
  - Scope: React UI (Vite, Tailwind, Framer Motion, Recharts) implementing all screens and states (loading, empty, error, success) connected to Node API.
  - Done criteria: Every mocked call replaced by a real call, all states handled.
- [ ] **M7: Deploy and polish**
  - Scope: GitHub Actions CI, live deployment / configuration, README with architecture diagram and demo video / screenshots.
  - Done criteria: Live URL, CI green, README with architecture diagram and demo video.

## Active Stubs `TODO(stub)`
*(None currently)*

