---
name: DocuMind Daylight Spec
colors:
  surface: '#f8f9ff'
  surface-dim: '#ccdbf3'
  surface-bright: '#f8f9ff'
  surface-container-lowest: '#ffffff'
  surface-container-low: '#eff4ff'
  surface-container: '#e6eeff'
  surface-container-high: '#dce9ff'
  surface-container-highest: '#d5e3fc'
  on-surface: '#0d1c2e'
  on-surface-variant: '#464554'
  inverse-surface: '#233144'
  inverse-on-surface: '#eaf1ff'
  outline: '#767586'
  outline-variant: '#c7c4d7'
  surface-tint: '#494bd6'
  primary: '#4648d4'
  on-primary: '#ffffff'
  primary-container: '#6063ee'
  on-primary-container: '#fffbff'
  inverse-primary: '#c0c1ff'
  secondary: '#006781'
  on-secondary: '#ffffff'
  secondary-container: '#8fdfff'
  on-secondary-container: '#00647d'
  tertiary: '#00694c'
  on-tertiary: '#ffffff'
  tertiary-container: '#1e8462'
  on-tertiary-container: '#f5fff7'
  error: '#ba1a1a'
  on-error: '#ffffff'
  error-container: '#ffdad6'
  on-error-container: '#93000a'
  primary-fixed: '#e1e0ff'
  primary-fixed-dim: '#c0c1ff'
  on-primary-fixed: '#07006c'
  on-primary-fixed-variant: '#2f2ebe'
  secondary-fixed: '#b9eaff'
  secondary-fixed-dim: '#81d1f0'
  on-secondary-fixed: '#001f29'
  on-secondary-fixed-variant: '#004d62'
  tertiary-fixed: '#97f5cc'
  tertiary-fixed-dim: '#7bd8b1'
  on-tertiary-fixed: '#002115'
  on-tertiary-fixed-variant: '#00513a'
  background: '#f8f9ff'
  on-background: '#0d1c2e'
  surface-variant: '#d5e3fc'
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
    fontSize: 20px
    fontWeight: '600'
    lineHeight: 28px
    letterSpacing: -0.01em
  headline-sm:
    fontFamily: Inter
    fontSize: 16px
    fontWeight: '600'
    lineHeight: 24px
    letterSpacing: -0.005em
  body-lg:
    fontFamily: Inter
    fontSize: 15px
    fontWeight: '400'
    lineHeight: 22px
  body-md:
    fontFamily: Inter
    fontSize: 13px
    fontWeight: '400'
    lineHeight: 18px
  body-sm:
    fontFamily: Inter
    fontSize: 12px
    fontWeight: '400'
    lineHeight: 16px
  label-lg:
    fontFamily: JetBrains Mono
    fontSize: 13px
    fontWeight: '500'
    lineHeight: 18px
    letterSpacing: -0.01em
  label-md:
    fontFamily: JetBrains Mono
    fontSize: 12px
    fontWeight: '500'
    lineHeight: 16px
    letterSpacing: 0em
  label-sm:
    fontFamily: JetBrains Mono
    fontSize: 11px
    fontWeight: '500'
    lineHeight: 14px
    letterSpacing: 0.01em
  metric-display:
    fontFamily: JetBrains Mono
    fontSize: 28px
    fontWeight: '600'
    lineHeight: 32px
    letterSpacing: -0.02em
rounded:
  sm: 0.125rem
  DEFAULT: 0.25rem
  md: 0.375rem
  lg: 0.5rem
  xl: 0.75rem
  full: 9999px
spacing:
  gutter: 1rem
  gutter-desktop: 1.25rem
  margin: 1rem
  margin-desktop: 1.5rem
  space-xs: 0.25rem
  space-sm: 0.5rem
  space-md: 0.75rem
  space-lg: 1rem
  space-xl: 1.5rem
---

## Brand & Style

This design system delivers a clinical, high-density evaluation dashboard engineered for machine learning practitioners, retrieval-augmented generation (RAG) architects, and benchmark engineers. The aesthetic draws inspiration from high-craft developer platforms like Linear and Supabase, prioritizing data clarity, low latency visual parsing, and exact metric representation over decorative distraction.

The interface projects precision, technical rigor, and calm authority under daylight working conditions. Visual weight is maintained through calibrated hairline strokes, strict typography hierarchy, and deliberate structural density rather than heavy fills. Every pixel establishes clear spatial relationships between telemetry graphs, chunking metrics, latency curves, and context-retrieval scores.

## Colors

The daylight palette balances high-contrast readability with muted technical backgrounds to prevent eye strain during extended analytical sessions.

- **Canvas Background (`#F8FAFC`)**: Base environment for the dashboard workspace and layout rails.
- **Surface (`#FFFFFF`)**: Clean, crisp containment for evaluation cards, data tables, and run logs.
- **Raised Surface (`#F1F5F9`)**: Subtle elevation for telemetry headers, code blocks, parameter strips, and nested metric groupings.
- **Structural Border (`#E2E8F0`)**: 1px structural boundaries defining the modular grid without visual noise.
- **Primary Indigo (`#6366F1`)**: Interactive states, selected benchmark pipelines, and primary execution controls, paired strictly with pure white text (`#FFFFFF`).
- **Daylight Accent Cyan (`#0E7490`)**: Highlights retrieval vector similarity, dynamic citation pings, and context overlap indicators.
- **State Colors**:
  - Success Emerald (`#047857`): Precision benchmarks met, context recall > 95%, test suites passed.
  - Warning Amber (`#B45309`): Hallucination drift, context truncation warnings, elevated latency thresholds.
  - Danger Ruby (`#B91C1C`): Retrieval pipeline collapse, semantic mismatches, threshold failures.
- **Text & Foreground**:
  - Primary Text (`#0F172A`): Deep slate for primary data readouts, table headers, and structural UI labels.
  - Muted Text (`#475569`): Secondary guidance, metric units, timestamp metadata, and inactive parameters.

## Typography

The type system is divided cleanly between system narrative interface controls and tabular telemetry data:

1. **Inter**: Handles all UI structural framing, navigation, natural language descriptions, and model inference context. Clean optical sizing maintains legibility at dense dashboard scales (`12px` and `13px`).
2. **JetBrains Mono**: Serves as the precision engine for the entire platform. Mandatory for all benchmark fractions (e.g., `0.942 / 1.000`), cosine distance metrics, token latencies (`124ms`), context chunk hashes, code payloads, and tabular dataset figures. All figures must render with tabular proportional numerals (`font-variant-numeric: tabular-nums`).

## Layout & Spacing

The layout is built around a dense, high-utility fluid grid system structured for data-heavy split-pane workflows.

- **Workspace Framing**: Fixed-collapsible left navigation (64px mini / 240px expanded) paired with a responsive fluid viewport that flexes from single-column inspection view (mobile/tablet) to multi-column analytical panels (desktop/wide).
- **Responsive Breakpoints**:
  - **Desktop (>= 1280px)**: 12-column grid or dual-pane 40/60 comparative split (query context vs. retrieval ground truth). Gutters set to `1.25rem` (`gutter-desktop`), outer margin to `1.5rem` (`margin-desktop`).
  - **Tablet (768px - 1279px)**: 8-column layout. Sidebar collapses to icon navigation. Sub-panels stack vertically or utilize horizontal segment tabs. Gutters set to `1rem` (`gutter`).
  - **Mobile (< 768px)**: 4-column layout with vertical flow. Data matrices transition to structured metric cards with horizontal scroll for wide tabular citations.
- **Rhythm**: Standard 4px incremental scale (`space-xs` through `space-xl`) enforces tight grouping between labels and their associated telemetry readouts, preserving high density without crowding.

## Elevation & Depth

In alignment with Supabase and Linear aesthetic paradigms, depth is achieved almost entirely via **tonal layering** and **crisp 1px borders** rather than diffuse drop shadows.

- **Flat Baseline**: The root canvas `#F8FAFC` holds the perimeter. Surface cards sit flush at `#FFFFFF` with a continuous `1px solid #E2E8F0` border.
- **Recessed / Secondary Panels**: Code blocks, parameter trays, and table headers use `#F1F5F9` with matching `#E2E8F0` hairline dividers.
- **Shadow Philosophy**: Drop shadows are reserved exclusively for floating or dismissible layers (dropdown menus, command bars, tooltips, and modal inspection dialogs). When required, use a sharp, low-spread ambient shadow:
  - `box-shadow: 0 1px 2px 0 rgba(15, 23, 42, 0.05)` for floating cards.
  - `box-shadow: 0 4px 12px 0 rgba(15, 23, 42, 0.08)` for elevated contextual popovers and command palettes.
- **Focus & Selection**: Interactive focus rings abandon heavy outlines in favor of a crisp `0 0 0 1px #6366F1` stroke paired with a subtle `0 0 0 3px rgba(99, 102, 241, 0.15)` aura.

## Shapes

This design system uses a strict **Soft (`roundedness: 1`)** geometry to echo modern CLI-adjacent and desktop development tools. 

- **Base Radius (0.25rem / 4px)**: Default for input fields, metric tags, chips, buttons, citation badges, and table cells.
- **Container Radius (0.5rem / 8px)**: Applied to evaluation panels, charts, code containers, and modal dialogs (`rounded-lg`).
- **Pill Exceptions**: Avoid fully rounded/pill borders (`9999px`) entirely. Every element—including status chips and execution badges—must maintain structured corner definitions to reinforce architectural engineering precision.

## Components

### Buttons
- **Primary**: Background `#6366F1`, text `#FFFFFF`, border `transparent`. Hover `#4F46E5`. Active `#4338CA`. Height 32px (compact) or 36px (default). Type: `Inter`, 13px weight 500.
- **Secondary / Outline**: Background `#FFFFFF`, text `#0F172A`, border `1px solid #E2E8F0`. Hover `#F1F5F9`.
- **Tertiary / Ghost**: Background `transparent`, text `#475569`, no border. Hover `#F1F5F9`, text `#0F172A`.

### Status Badges & Chips
- Form factor: Compact height (20px or 22px), `padding: 2px 6px`, radius 4px (`rounded`).
- Typography: `JetBrains Mono`, 11px, weight 500, uppercase letter spacing.
- **Success (Context Precision)**: Background `#ECFDF5`, text `#047857`, border `1px solid #A7F3D0`.
- **Warning (Latency / Drift)**: Background `#FFFBEB`, text `#B45309`, border `1px solid #FDE68A`.
- **Danger (Hallucination)**: Background `#FEF2F2`, text `#B91C1C`, border `1px solid #FECACA`.
- **Cyan Accent (Citation Match)**: Background `#ECFEFF`, text `#0E7490`, border `1px solid #A5F3FC`.

### Data Cards & Benchmark Metric Modules
- Container: Background `#FFFFFF`, border `1px solid #E2E8F0`, corner radius 8px (`rounded-lg`).
- Header: Subtle background `#F1F5F9`, border-bottom `1px solid #E2E8F0`, padding `8px 12px`.
- Metric Layout: JetBrains Mono value (`metric-display`) stacked above an Inter muted micro-label (`11px`, `#475569`).

### Input Fields & Parameter Steppers
- Height 32px. Background `#FFFFFF`, border `1px solid #E2E8F0`, corner radius 4px.
- Typography: `JetBrains Mono` for parameter inputs (temperature, top-k, chunk-size), `Inter` for search/query text.
- Focus: Border `#6366F1`, box-shadow `0 0 0 1px #6366F1`.

### Data Tables & Log Traces
- Rows: Clean 36px height. Hover background `#F8FAFC`.
- Border: `1px solid #E2E8F0` horizontal divider only.
- Numerics: Right-aligned `JetBrains Mono` with `tabular-nums` enabled.

### Checkboxes & Radios
- Size: 14px x 14px square/circle with a 1px border `#E2E8F0`.
- Checked state: `#6366F1` fill with sharp white indicator icon.