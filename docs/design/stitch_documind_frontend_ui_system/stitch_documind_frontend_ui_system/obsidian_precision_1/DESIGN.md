---
name: Obsidian Precision
colors:
  surface: '#0f131e'
  surface-dim: '#0f131e'
  surface-bright: '#353945'
  surface-container-lowest: '#0a0e19'
  surface-container-low: '#171b27'
  surface-container: '#1b1f2b'
  surface-container-high: '#262a36'
  surface-container-highest: '#313441'
  on-surface: '#dfe2f2'
  on-surface-variant: '#c7c4d7'
  inverse-surface: '#dfe2f2'
  inverse-on-surface: '#2c303c'
  outline: '#908fa0'
  outline-variant: '#464554'
  surface-tint: '#c0c1ff'
  primary: '#c0c1ff'
  on-primary: '#1000a9'
  primary-container: '#8083ff'
  on-primary-container: '#0d0096'
  inverse-primary: '#494bd6'
  secondary: '#5de6ff'
  on-secondary: '#00363e'
  secondary-container: '#00cbe6'
  on-secondary-container: '#00515d'
  tertiary: '#4edea3'
  on-tertiary: '#003824'
  tertiary-container: '#00885d'
  on-tertiary-container: '#000703'
  error: '#ffb4ab'
  on-error: '#690005'
  error-container: '#93000a'
  on-error-container: '#ffdad6'
  primary-fixed: '#e1e0ff'
  primary-fixed-dim: '#c0c1ff'
  on-primary-fixed: '#07006c'
  on-primary-fixed-variant: '#2f2ebe'
  secondary-fixed: '#a2eeff'
  secondary-fixed-dim: '#2fd9f4'
  on-secondary-fixed: '#001f25'
  on-secondary-fixed-variant: '#004e5a'
  tertiary-fixed: '#6ffbbe'
  tertiary-fixed-dim: '#4edea3'
  on-tertiary-fixed: '#002113'
  on-tertiary-fixed-variant: '#005236'
  background: '#0f131e'
  on-background: '#dfe2f2'
  surface-variant: '#313441'
typography:
  headline-lg:
    fontFamily: Inter
    fontSize: 32px
    fontWeight: '600'
    lineHeight: 40px
    letterSpacing: -0.02em
  headline-lg-mobile:
    fontFamily: Inter
    fontSize: 24px
    fontWeight: '600'
    lineHeight: 32px
    letterSpacing: -0.01em
  headline-md:
    fontFamily: Inter
    fontSize: 24px
    fontWeight: '600'
    lineHeight: 32px
    letterSpacing: -0.01em
  headline-sm:
    fontFamily: Inter
    fontSize: 20px
    fontWeight: '600'
    lineHeight: 28px
    letterSpacing: -0.01em
  title-md:
    fontFamily: Inter
    fontSize: 16px
    fontWeight: '600'
    lineHeight: 24px
    letterSpacing: -0.005em
  title-sm:
    fontFamily: Inter
    fontSize: 14px
    fontWeight: '600'
    lineHeight: 20px
  body-lg:
    fontFamily: Inter
    fontSize: 16px
    fontWeight: '400'
    lineHeight: 24px
  body-md:
    fontFamily: Inter
    fontSize: 14px
    fontWeight: '400'
    lineHeight: 20px
  body-sm:
    fontFamily: Inter
    fontSize: 12px
    fontWeight: '400'
    lineHeight: 16px
  code-lg:
    fontFamily: JetBrains Mono
    fontSize: 14px
    fontWeight: '500'
    lineHeight: 20px
  code-md:
    fontFamily: JetBrains Mono
    fontSize: 12px
    fontWeight: '400'
    lineHeight: 16px
  code-sm:
    fontFamily: JetBrains Mono
    fontSize: 11px
    fontWeight: '400'
    lineHeight: 14px
  label-md:
    fontFamily: Inter
    fontSize: 12px
    fontWeight: '500'
    lineHeight: 16px
  label-sm:
    fontFamily: JetBrains Mono
    fontSize: 11px
    fontWeight: '500'
    lineHeight: 14px
    letterSpacing: 0.02em
rounded:
  sm: 0.25rem
  DEFAULT: 0.5rem
  md: 0.75rem
  lg: 1rem
  xl: 1.5rem
  full: 9999px
spacing:
  gutter: 1rem
  gutter-desktop: 1.5rem
  margin: 1rem
  margin-desktop: 2rem
  space-xs: 0.25rem
  space-sm: 0.5rem
  space-md: 1rem
  space-lg: 1.5rem
  space-xl: 2rem
---

## Brand & Style

The design system establishes a high-density, technical aesthetic built for engineers, ML practitioners, and platform architects running complex retrieval-augmented generation pipelines. The tone is utilitarian, calm, and uncompromisingly precise—evoking the deep-space clarity of an integrated development environment rather than an enterprise marketing suite.

Visual principles:
- **Restrained Density:** Minimize decorative empty space in favor of compact, structured information architectures. Metrics, vector telemetry, and retrieval traces take center stage.
- **Surface Elevation via Tone:** Depth is achieved strictly through deliberate slate-tinted tonal layering and razor-thin borders, eliminating noisy drop shadows and saturated gradient washes.
- **Technical Typography:** Clear semantic boundaries between human-authored prompts, synthetic model completions, system metadata, and vector metrics using strict sans-serif and monospaced roles.

## Colors

The palette operates on a disciplined dark substrate with high-contrast text and purposeful semantic signals.

### Surface Tiers
- **Background (`#0B0F1A`):** The primary canvas background. Used for full-viewport shells and main canvas planes.
- **Surface (`#121829`):** Ground level for structural containers, panels, navigation sidebars, and persistent inspectors.
- **Surface Raised (`#18203A`):** Elevated level for floating popovers, modal dialogues, interactive dropdown menus, and card headers.

### Borders
- **Border Default (`#1F2A44`):** Crisp 1px division for cards, panels, active search inputs, and table headers.
- **Border Subtler (`#162035`):** Hairline partition for secondary dividers, row borders, and inactive panel segments.

### Semantic & Accents
- **Primary Indigo (`#6366F1`):** Action focus, selected navigation items, and active filter states. Interactive hover transitions to `#818CF8`.
- **Primary Subtle / Glow (`rgba(99, 102, 241, 0.15)`): Confined backdrops for active states and subtle focus glow halos.
- **Accent Cyan (`#22D3EE`):** Retrieval metrics, vector similarity indices, latency counters, and token streaming traces.
- **Success Emerald (`#10B981`):** Successful evaluation runs, healthy ingestion status, and passed assertions.
- **Warning Amber (`#F59E0B`):** Context truncation warnings, high latency alerts, and throttled inference.
- **Danger Rose (`#EF4444`):** Failed retrievals, hallucination alerts, schema mismatches, and critical errors.

### Typography Colors
- **Text (`#E5E7EB`):** High-contrast primary reading text, form values, and active interface labels.
- **Muted Text (`#94A3B8`):** Secondary descriptions, table column headers, prompt metadata, and timestamps.
- **Faint Text (`#64748B`):** Placeholders, disabled states, inactive shortcuts, and bracket delimiters.

## Typography

The typography scale balances rapid scan-speed across technical dashboards with legible code inspection.

- **Proportional UI Text (Inter):** Applied across all primary labels, natural language documentation, conversational prompt inputs, and dialogs. Weights are strictly constrained to 400 (regular), 500 (medium), and 600 (semi-bold) to maintain architectural crispness.
- **Monospace Engine (JetBrains Mono):** Reserved for raw prompt traces, chunk payloads, embedding dimensions, JSON manifests, and performance metrics (e.g., token consumption, inference latency, recall@k).
- **Tabular Figures:** Monospace metrics and code roles must enforce tabular numerical alignments to prevent jumping numbers during continuous real-time vector streaming and latency tracking.

## Layout & Spacing

The layout model is governed by an 8px base rhythm (with 4px half-step sub-units for high-density controls).

### Grid and Workspace Architecture
- **Multi-Pane IDE Layout:** The platform operates on a rigid pane system rather than a fluid marketing grid: fixed collapsible navigation rail (240px desktop, 64px collapsed), fixed or resizable sidebar inspection panel (360px), and an elastic primary central canvas.
- **Breakpoints:**
  - **Desktop (>= 1280px):** 3-pane configuration active simultaneously (navigation, workspace canvas, telemetry inspector). Outer margins set to `margin-desktop`, pane gutter at `gutter-desktop`.
  - **Tablet (768px - 1279px):** Two-pane configuration. Telemetry inspector collapses into an overlay drawer or toggled bottom sheet. Outer canvas margins reduce to `margin`.
  - **Mobile (< 768px):** Single-column stacked mode. Side navigation collapses to an off-canvas drawer. Dense data tables switch to horizontally scrollable viewports with sticky header indices.
- **Data Densities:**
  - *Comfortable:* `space-md` gaps within document review views.
  - *Compact:* `space-xs` and `space-sm` gaps for raw chunk inspectors, execution logs, and evaluation test runs.

## Elevation & Depth

Visual hierarchy uses flat tonal layering and hairline boundaries rather than dramatic physical drop shadows.

- **Level 0 (Canvas Base):** Plain `#0B0F1A`. No border or shadow.
- **Level 1 (Card & Section Containers):** Filled with `#121829`, bounded by a single 1px solid `#1F2A44` border. No drop shadow.
- **Level 2 (Popovers, Dropdowns, Hovered Cards):** Filled with `#18203A`, bounded by a 1px solid `#1F2A44` border. Supported by a restrained ambient occlusion shadow: `0 8px 24px rgba(0, 0, 0, 0.45)`.
- **Level 3 (Modal Dialogs & Command Palettes):** Surface `#18203A`, bounded by a 1px solid `#1F2A44`, flanked by an outer shadow: `0 16px 40px rgba(0, 0, 0, 0.65)`. Backdrops feature a solid `#0B0F1A` overlay at 80% opacity without Gaussian blur filters.
- **Active Focus & Glow:** Active inputs, focused navigation nodes, and selected pipeline cards emit a 2px outer glow using `rgba(99, 102, 241, 0.15)` paired with a primary border (`#6366F1`).

## Shapes

The design system maintains an intentional geometric hierarchy that maps border-radius directly to structural role:

- **12px Radius (`rounded-lg`):** Reserved for macroscopic spatial boundaries: main layout panels, evaluation test suites, code execution blocks, dialog boxes, and metrics summary cards.
- **8px Radius (Base):** Standard for atomic interactive controls: primary and secondary buttons, text input fields, search filters, and status badges.
- **6px Radius (`rounded-sm`):** Precise sub-elements: retrieval citation chips, semantic token tags, monospaced metadata badges, and inline keybinding indicators.
- **Pill (Full Radius):** Dedicated exclusively to status indicator badges and live state tags.

## Components

### Buttons
- **Primary:** Background `#6366F1`, text `#FFFFFF`, border none, radius 8px, height 36px (compact: 30px). Hover: `#818CF8`. Active: `#4F46E5`.
- **Secondary / Outline:** Background `transparent`, text `#E5E7EB`, 1px border `#1F2A44`, radius 8px. Hover: background `#18203A`, border-color `#6366F1`.
- **Ghost / Minimal:** Background `transparent`, text `#94A3B8`, border none. Hover: background `#121829`, text `#E5E7EB`.

### Input Fields & Search Bars
- Background `#121829`, 1px solid `#1F2A44`, radius 8px, padding `space-sm` `space-md`, text `#E5E7EB`, placeholder `#64748B`.
- **Focus State:** 1px solid `#6366F1`, box-shadow `0 0 0 3px rgba(99, 102, 241, 0.15)`.
- Monospaced variants (for regex matching, embedding filter configs, SQL clauses) adopt `JetBrains Mono` at `code-md`.

### Citation Chips & Chunks
- Inline metadata chips representing RAG document sources and retrieved chunks.
- Background `#18203A`, 1px solid `#1F2A44`, radius 6px, padding `2px 8px`.
- Typography: `code-sm` (`JetBrains Mono`). Hover initiates `#22D3EE` (cyan) border highlight and opens a low-latency preview inspector.

### Status Badges & Pulsing Nodes
- Pill-shaped container (`border-radius: 9999px`), background `#121829`, 1px solid `#1F2A44`, padding `2px 10px`.
- Incorporates a 6px circular indicator dot on the left.
- **States:**
  - *Active Processing / Ingestion:* Emerald (`#10B981`) or Indigo (`#6366F1`) dot with a slow 1.5s radial pulse ring (`box-shadow: 0 0 0 4px rgba(16, 185, 129, 0.2)`).
  - *Idle / Ready:* Static Cyan (`#22D3EE`) dot.
  - *Error / Degradation:* Static Rose (`#EF4444`) dot.

### Cards & Evaluation Run Containers
- Background `#121829`, 1px solid `#1F2A44`, radius 12px, padding `space-lg`.
- Dividers between card header, payload, and footer use 1px solid `#162035`.
- Selected/comparing card state highlights the border with `#6366F1` and adds a subtle top hairline accent.

### Checkboxes & Radio Controls
- Base: 16px square (checkbox) or circle (radio), background `#121829`, 1px solid `#1F2A44`, radius 4px (checkbox) or 50% (radio).
- Selected: background `#6366F1`, border-color `#6366F1`, inner glyph white.

### Lists & Telemetry Tables
- Dense tabular structures with alternating row transitions: default background transparent, hover background `#18203A`.
- Horizontal row border: 1px solid `#162035`. Headers set in `label-sm` with color `#94A3B8`, background `#121829`.