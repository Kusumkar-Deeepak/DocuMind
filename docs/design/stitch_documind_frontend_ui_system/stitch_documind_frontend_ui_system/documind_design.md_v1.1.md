# DocuMind – Design System Specification (v1.1)

## 1. Visual Philosophy
Calm, developer-focused, high-density interface inspired by Linear and Supabase. Subtle 1px borders, restrained indigo glows, and strict typography hierarchy. No decorative gradients, glassmorphism, or ungrounded UI components. Every metric, field, and button is strictly backed by the endpoints and tables in `docs/SPEC.md`.

## 2. Color Palette & Design Tokens

### Dark Mode (Primary Default)
| Token | Hex Value | Purpose |
|---|---|---|
| `bg-background` | `#0B0F1A` | Canvas & app background |
| `bg-surface` | `#121829` | Cards, sidebars, content containers, tables |
| `bg-surface-raised` | `#18203A` | Modals, elevated dialogs, hover rows, popovers |
| `border-subtle` | `#1F2A44` | Structural 1px dividers and component borders |
| `color-primary` | `#6366F1` | Primary CTA buttons (with pure white text `#FFFFFF`), active tabs |
| `color-primary-hover` | `#818CF8` | Primary button & link hover state |
| `color-accent` | `#22D3EE` | Neural nodes, active citations, streaming pulse |
| `color-success` | `#10B981` | Ready status badges, verified benchmark hits |
| `color-warning` | `#F59E0B` | Ingestion warnings, rate limit alerts |
| `color-danger` | `#EF4444` | Failed ingestion status, deletion actions |
| `text-primary` | `#E5E7EB` | Headings, primary content, active labels |
| `text-muted` | `#94A3B8` | Subtitles, table headers, timestamps, secondary labels |

### Light Mode (Variant)
| Token | Hex Value | Purpose |
|---|---|---|
| `bg-background` | `#F8FAFC` | Daylight canvas & app background |
| `bg-surface` | `#FFFFFF` | Cards, sidebar, tables, panels |
| `bg-surface-raised` | `#F1F5F9` | Elevated controls, hover rows, dialogs |
| `border-subtle` | `#E2E8F0` | Structural 1px borders & dividers |
| `color-primary` | `#6366F1` | Primary CTA buttons (with white text `#FFFFFF`) |
| `color-primary-hover` | `#4F46E5` | Primary hover state |
| `color-accent` | `#0891B2` | High-contrast cyan/teal accent for daytime |
| `text-primary` | `#0F172A` | Primary text and headings |
| `text-muted` | `#475569` | Secondary text, table headers, metadata |

## 3. Typography
- **UI & System:** `Inter`, -apple-system, sans-serif
- **Code, Citations, Metrics & Badges:** `JetBrains Mono`, monospace (with `font-variant-numeric: tabular-nums`)
- **Type Scale:**
  - 12px: Citations, metadata, timestamps, badge labels
  - 14px: Body copy, inputs, table cells, navigation links
  - 16px: Subheadings, modal titles, form labels
  - 20px: Card titles, section headers
  - 24px: View headings
  - 32px: Auth title, high-level metrics

## 4. Spacing & Radius Rules
- 8px base grid (`8px`, `16px`, `24px`, `32px`, `48px`)
- Card & container radius: `12px`
- Inputs, buttons & select triggers: `8px`
- Badges, citation chips & pills: `6px`

## 5. Motion & Animation Rules
- **Page Transitions:** `fade + 8px slide-up` in 250ms ease-out.
- **Interactive Lift:** `translateY(-2px)` with 150ms ease-out on buttons & interactive cards.
- **Skeleton Shimmer:** Smooth linear gradient sweep across placeholder bones (`background-size: 200% 100%`).
- **Streaming Caret:** Monospace blinking cursor at 500ms `step-end`.
- **Message Enter Animation:** New chat messages enter with fade and 4px slide-up in 200ms.
- **Count-Up Metrics:** Numerical KPI cards animate up from 0 on initial mount.
- **One-Time Chart Entrance:** SVG / canvas charts grow or draw paths once on view load.
- **Processing Badge Pulse:** Ingestion status badge runs an opacity/scale pulse on its indicator dot while in `processing`.
- **Accessibility:** All transitions and keyframe animations collapse to 0ms when `@media (prefers-reduced-motion: reduce)` is detected.

## 6. Accessibility
- All text meets or exceeds WCAG 2.1 AA 4.5:1 contrast against its background surface.
- Visible focus rings using `ring-2 ring-indigo-500 ring-offset-2 ring-offset-[#0B0F1A]`.
- All controls operable via standard keyboard shortcuts (`Tab`, `Enter`, `Escape`, arrow navigation).

## 7. Component & View States
Every screen architecture must account for 4 distinct visual states:
1. **Loading State:** Structured skeleton shimmer placeholders replacing tables, metrics, and cards.
2. **Empty State:** Centered icon, clear explanation, and primary action button (e.g., "No documents uploaded yet", "No evaluation runs recorded").
3. **Error State:** Banner or card with distinct `#EF4444` border and clear diagnostic message from the API error payload `{ "error": { "code": "STRING", "message": "STRING" } }`.
4. **Success State:** Action confirmation via toast notification (e.g., "Member created successfully", "Document deleted").
