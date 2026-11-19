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
  tertiary: '#ffb783'
  on-tertiary: '#4f2500'
  tertiary-container: '#d97721'
  on-tertiary-container: '#452000'
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
  tertiary-fixed: '#ffdcc5'
  tertiary-fixed-dim: '#ffb783'
  on-tertiary-fixed: '#301400'
  on-tertiary-fixed-variant: '#703700'
  background: '#0f131e'
  on-background: '#dfe2f2'
  surface-variant: '#313441'
typography:
  headline-xl:
    fontFamily: Inter
    fontSize: 2.25rem
    fontWeight: '600'
    lineHeight: 2.75rem
    letterSpacing: -0.025em
  headline-xl-mobile:
    fontFamily: Inter
    fontSize: 1.75rem
    fontWeight: '600'
    lineHeight: 2.25rem
    letterSpacing: -0.02em
  headline-lg:
    fontFamily: Inter
    fontSize: 1.5rem
    fontWeight: '600'
    lineHeight: 2rem
    letterSpacing: -0.02em
  headline-md:
    fontFamily: Inter
    fontSize: 1.25rem
    fontWeight: '600'
    lineHeight: 1.75rem
    letterSpacing: -0.015em
  body-lg:
    fontFamily: Inter
    fontSize: 1rem
    fontWeight: '400'
    lineHeight: 1.5rem
    letterSpacing: -0.011em
  body-md:
    fontFamily: Inter
    fontSize: 0.875rem
    fontWeight: '400'
    lineHeight: 1.375rem
    letterSpacing: -0.006em
  body-sm:
    fontFamily: Inter
    fontSize: 0.75rem
    fontWeight: '400'
    lineHeight: 1.125rem
    letterSpacing: 0em
  code-inline:
    fontFamily: JetBrains Mono
    fontSize: 0.8125rem
    fontWeight: '400'
    lineHeight: 1.25rem
    letterSpacing: -0.01em
  data-metric:
    fontFamily: JetBrains Mono
    fontSize: 1.125rem
    fontWeight: '500'
    lineHeight: 1.5rem
    letterSpacing: -0.02em
  badge-label:
    fontFamily: JetBrains Mono
    fontSize: 0.6875rem
    fontWeight: '500'
    lineHeight: 0.875rem
    letterSpacing: 0.02em
rounded:
  sm: 0.125rem
  DEFAULT: 0.25rem
  md: 0.375rem
  lg: 0.5rem
  xl: 0.75rem
  full: 9999px
spacing:
  gutter: 1rem
  gutter-desktop: 1.5rem
  margin: 1rem
  margin-desktop: 2rem
  space-xs: 0.25rem
  space-sm: 0.5rem
  space-md: 0.75rem
  space-lg: 1rem
  space-xl: 1.5rem
---

## Brand & Style

This design system delivers a calm, razor-sharp developer aesthetic modeled after high-focus engineering environments like Linear and Supabase. Designed for technical practitioners interacting with dense analytical workflows, document retrieval, and contextual AI insights, the interface prioritizes clarity, informational density, and ergonomic visual focus over ornamental design flourishes.

Key visual attributes include:
- **Disciplined Dark Mode**: A deep obsidian foundation paired with structural midnight surfaces to prevent eye strain during sustained technical sessions.
- **Architectonic Precision**: Sharp visual boundaries, strict rhythmic grids, and tactical hierarchy. Every container edge and element margin serves information parsing.
- **Subdued Restraint**: No arbitrary gradients, blurred backdrops, or faux-glassmorphic materials. Depth is managed strictly through discrete surface tonality and hairline dividers.

## Colors

The palette establishes an engineered tonal structure anchored in deep, blue-tinted dark values and punctuated by deliberate functional semantics:

- **Foundation & Surfaces**:
  - `canvas-background`: `#0B0F1A` (Root background canvas)
  - `surface`: `#121829` (Primary panel and card base)
  - `surface-raised`: `#18203A` (Elevated modules, popovers, dropdowns, and modal dialogs)
  - `border-subtle`: `#1F2A44` (Hairline structural delimiters, table rules, and outlines)

- **Interactive Primary**:
  - `primary`: `#6366F1` (Actions, active focus rings, critical indicators)
  - `primary-hover`: `#818CF8` (Hover state for primary actions)
  - `primary-content`: `#FFFFFF` (High-contrast label text on primary fills)

- **Semantic Accents**:
  - `accent`: `#22D3EE` (Citation indicators, technical highlights, active token tags)
  - `success`: `#10B981` (Verification states, operational health, parsed nodes)
  - `warning`: `#F59E0B` (Ambiguity, rate warning, indexing lags)
  - `danger`: `#EF4444` (Parsing errors, destructive actions, failed queries)

- **Typography & Content**:
  - `text-primary`: `#E5E7EB` (Headings, primary values, body content)
  - `text-muted`: `#94A3B8` (Metadata, placeholders, timestamps, secondary labels)

## Typography

The typographic hierarchy couples **Inter** for operational prose, navigation, and structural headings with **JetBrains Mono** for developer primitives: citations, analytical metrics, telemetry readouts, status badges, and code snippets.

Implementation guidelines:
- Apply `font-feature-settings: "cv02", "cv03", "cv04", "cv11"` to Inter for elevated legibility on complex UI panels.
- JetBrains Mono must always render with tabular numbers (`tnum`) enabled to prevent layout shifting across dynamic updates, progress monitors, and streaming tokens.
- Maintain high contrast between primary labels (`#E5E7EB`) and supporting metadata (`#94A3B8`), avoiding intermediate gray tones that reduce glanceability.

## Layout & Spacing

The system enforces a dense, utilitarian 12-column grid designed for data-heavy split-view environments (e.g., document view alongside generative inference streams).

- **Grid Architecture**:
  - **Desktop (>= 1280px)**: 12-column fluid grid, 24px outer margins, 24px gutters. Workspaces leverage persistent sidebar navigation (240px fixed) with fluid workbench partitions.
  - **Tablet (768px - 1279px)**: 8-column layout, 16px margins, 16px gutters. Secondary inspector rails collapse into drawer overlays.
  - **Mobile (< 768px)**: 4-column layout, 16px margins, 12px gutters. Primary inspection and reading tools stack sequentially.

- **Spacing Cadence**:
  Internal layout follows a strict 4px/8px modular rhythm. Micro-gaps (`space-xs`, `space-sm`) govern form rows, inline pill groups, and label-to-input relations. Macro-spacers (`space-lg`, `space-xl`) define container segment boundaries and major workspace dividers.

## Elevation & Depth

Depth is conveyed through **tonal planes** and **crisp 1px containment borders** (`#1F2A44`), strictly rejecting blurred skeuomorphism, ambient colored drop-shadows, and glassmorphic layers.

- **Level 0 (Canvas Base)**: `#0B0F1A` default workspace backdrop.
- **Level 1 (Card & Content Blocks)**: `#121829` bounded by a 1px solid border of `#1F2A44`. Zero box-shadow; structure is solely defined by contrast between `#0B0F1A` and `#121829`.
- **Level 2 (Popovers, Flyouts, Context Menus)**: `#18203A` with `#1F2A44` border. A disciplined, dark drop-shadow is applied strictly for boundary separation over active text: `0 4px 16px rgba(0, 0, 0, 0.45)`.
- **Level 3 (Modal Dialogs & Critical Focus Overlays)**: `#18203A` surface centered over an unblurred, darkened backdrop mask (`#0B0F1A` at 80% opacity), paired with `0 12px 32px rgba(0, 0, 0, 0.65)` shadow.

## Shapes

Shape geometry is deliberately compact, providing an industrial instrument feel. Curved forms are used with restraint to keep visual flow orderly and structured:

- **Cards & Primary Modules**: 12px (`0.75rem`) border-radius.
- **Inputs & Action Buttons**: 8px (`0.5rem`) border-radius.
- **Citation Chips, Status Badges, & Metrics**: 6px (`0.375rem`) border-radius.
- **Inner Nested Elements**: When nesting badges or chips inside containers or inputs, radius offsets must align gracefully (parent - padding = child), avoiding awkward geometric tension.

## Components

### Buttons
- **Primary**: Background `#6366F1`, text `#FFFFFF`, 8px radius, Inter font (weight 500), horizontal padding `12px`, vertical padding `8px`. Hover: `#818CF8`. Active: `#4F46E5`.
- **Secondary / Outline**: Background transparent, border 1px solid `#1F2A44`, text `#E5E7EB`. Hover: background `#18203A`, border `#6366F1`.
- **Destructive**: Background transparent, border 1px solid `#EF4444`, text `#EF4444`. Hover: background rgba(239, 68, 68, 0.1).

### Inputs & Text Areas
- Background `#121829`, border 1px solid `#1F2A44`, radius 8px, height 36px (compact default). Text `#E5E7EB`, placeholder `#94A3B8`.
- Focus state: Border color `#6366F1`, paired with a non-diffuse focus ring `0 0 0 1px #6366F1`.

### Citation Chips & Badges
- **Citation Chip**: Background `rgba(34, 211, 238, 0.08)`, border 1px solid `rgba(34, 211, 238, 0.25)`, text `#22D3EE`, radius 6px, font JetBrains Mono (weight 500, tabular figures). Padding `2px 6px`. Hover: border `#22D3EE`, background `rgba(34, 211, 238, 0.16)`.
- **Status Badges**:
  - Verified/Healthy: Background `rgba(16, 185, 129, 0.1)`, border 1px solid `rgba(16, 185, 129, 0.25)`, text `#10B981`.
  - Attention/Warning: Background `rgba(245, 158, 11, 0.1)`, border 1px solid `rgba(245, 158, 11, 0.25)`, text `#F59E0B`.

### Cards & Panels
- Background `#121829`, border 1px solid `#1F2A44`, radius 12px, padding `16px` or `24px`. No shadow in idle state.
- Card Header: Separated by a 1px solid divider of `#1F2A44` when structuring dense metric dashboards.

### Lists & Key-Value Pairs
- List rows feature subtle border-bottom dividers (`1px solid #1F2A44`).
- Hover state across interactive rows transitions background color to `#18203A`.
- Metric numbers and index positions render in JetBrains Mono (`#E5E7EB` or `#22D3EE`).

### Checkboxes & Radios
- Size 16x16px, background `#121829`, border 1px solid `#1F2A44`, radius 4px (checkbox) or 50% (radio).
- Checked: Fill `#6366F1`, border `#6366F1`, checkmark stroke `#FFFFFF`.