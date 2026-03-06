---
name: ui-design-system
description: >
  Build UI components following the Enigma geometric design system. Use when the user asks to
  "build a component", "create a UI element", "implement the design system", "add a card",
  "add a form", "style a button", "create a chart", "add a loader", "implement an accordion",
  "build a dropdown", "add a banner", "create a toast", "implement chips", "add a slider",
  "create a toggle", "build a list view", "add an avatar", "implement checkboxes",
  "create elevation shadows", "add icons", "build a page layout", or discusses front-end
  component development for Enigma products. Also triggers when the user references
  "the design system", "Enigma UI", "geometric UI", "dark mode components", or asks
  to match the Enigma component style.
version: 1.0.0
---

# Enigma UI Design System — Component Skill

You are building UI components following the Enigma geometric design system. This system uses a **dark-panel, monospace-first, geometric** aesthetic — minimal wireframe-style components on dark backgrounds with precise color accents.

**Reference image:** `~/Downloads/hf_20260303_155856_52adcb64-70bf-42e4-be0c-b35c754886a2.png`

Before writing any code, consult the reference files in `references/` for exact tokens, component specs, and patterns.

---

## Design Principles

1. **Dark panels, light canvas** — Components live on `#0a0a0a` / `#1a1a1a` dark cards. The page canvas is light lavender (`#E0DEE6`). This creates strong figure-ground contrast.
2. **Geometric & monospace** — All type is monospace. Icons are geometric/minimal (squares, triangles, circles, arrows). No rounded-friendly or playful aesthetics.
3. **Wireframe precision** — Borders are thin (`1px`), corners are sharp or minimally rounded (`2px`). Components feel like technical schematics, not consumer UI.
4. **Five accent colors** — Signal Red, Indicator Amber, Status Green, Alert Coral, Process Blue. Used sparingly for data callouts, status dots, and metric badges. Never for large fills.
5. **Elevation through layering** — Depth shown via stacked offset cards with dashed/dotted borders, not drop shadows. Shadows are geometric, not blurred.

---

## Color Tokens

### Surfaces
| Token | Hex | Usage |
|-------|-----|-------|
| `--surface-primary` | `#0a0a0a` | Card backgrounds, panels, dark containers |
| `--surface-elevated` | `#1a1a1a` | Elevated panels, dropdowns, modals |
| `--surface-canvas` | `#E0DEE6` | Page background (light lavender) |
| `--surface-input` | `#000000` | Form inputs, text fields |

### Text
| Token | Hex | Usage |
|-------|-----|-------|
| `--text-primary` | `#ffffff` | Headings, labels on dark surfaces |
| `--text-secondary` | `#a0a0a0` | Descriptions, placeholders |
| `--text-on-light` | `#0a0a0a` | Text on canvas/light backgrounds |

### Borders
| Token | Hex | Usage |
|-------|-----|-------|
| `--border-default` | `#333333` | Card borders, dividers on dark |
| `--border-light` | `#555555` | Subtle separators within panels |
| `--border-canvas` | `#0a0a0a` | Borders on light canvas background |

### Accent Colors (Metric Callouts)
| Token | Hex | Name | Usage |
|-------|-----|------|-------|
| `--color-signal` | `#A80012` | Signal Red | Errors, critical alerts, destructive actions |
| `--color-indicator` | `#F88785` | Indicator Amber | Warnings, attention-needed states |
| `--color-status` | `#08C89F` | Status Green | Success, active, healthy states |
| `--color-alert` | `#FD6A3D` | Alert Coral | Notifications, urgent but non-critical |
| `--color-process` | `#4EBCFF` | Process Blue | In-progress, informational, links |

### Additional Dot/Grid Colors (from Cards & List components)
Used in card color grids, list indicators, and data visualizations:
- Reds: `#A80012`, `#D4453A`
- Oranges: `#FD6A3D`, `#F88785`
- Yellows: `#F5C542`, `#E8B830`
- Greens: `#08C89F`, `#2DB87A`, `#1A7A5A`
- Blues: `#4EBCFF`, `#3A8FD4`, `#2A6CB0`
- Purples: `#8B5CF6`, `#6D28D9`
- White: `#ffffff`

---

## Typography

### Font Stack
```css
font-family: "Berkeley Mono", "SF Mono", "Monaco", "Cascadia Code", "Fira Code", monospace;
```

### Type Scale
| Element | Size | Weight | Style |
|---------|------|--------|-------|
| Component label (e.g., "Geometric Icons") | 14px | 400 | Normal, top-left of panel |
| Panel heading | 13px | 600 | Uppercase or title case |
| Data value / metric | 13px | 700 | Monospace, colored |
| Body text / descriptions | 12px | 400 | `--text-secondary` |
| Small labels (chips, badges) | 11px | 500 | Uppercase |
| Tiny annotations | 10px | 400 | `--text-secondary` |

### Line Height
- Headings: 1.2
- Body: 1.4
- Data/metrics: 1.0 (tight, for alignment)

---

## Component Inventory

### 1. Geometric Icons
A grid of 30+ minimal geometric icons built from basic shapes (squares, triangles, circles, diamonds, arrows, chevrons). Each icon fits a consistent bounding box.

**Grid:** 7 columns × 5 rows
**Icon size:** 24×24px bounding box
**Stroke:** 1.5px, `--text-primary`
**Fill:** None (outline only)
**Categories:** Navigation (arrows, chevrons, expand), Objects (folder, document, chart), Actions (settings/gear, search, plus, grid), Shapes (diamond, triangle, pentagon, hexagon)

### 2. Page Layouts
Three responsive wireframes showing the same content at different breakpoints:

**Page Layout (Desktop):**
- Top bar with 3 dots (window controls) and horizontal nav
- Below: full-width content band
- Below: 2-column grid (sidebar + main) or 3-column grid
- All regions are dark rectangles with thin white borders

**Tablet Layout:**
- Narrower, 2-column content area
- Condensed navigation

**Phone Layout:**
- Single column stack
- Simplified header
- Full-width content blocks

### 3. Elevations
Shows depth through **stacked offset cards** — 4–5 cards layered with slight X/Y offset, each with different border styles:
- Solid border (front)
- Dashed border (middle layers)
- Dotted border (back layers)
- No blur shadows — depth is purely geometric offset

```css
.elevation-1 { border: 1px solid var(--border-default); }
.elevation-2 { border: 1px dashed var(--border-light); transform: translate(4px, 4px); }
.elevation-3 { border: 1px dotted var(--border-light); transform: translate(8px, 8px); }
```

### 4. Accordions
Expandable content panels on dark background:
- Header row with text label + expand/collapse indicator
- Horizontal rule separator between items
- Content area below header when expanded
- Multiple items stacked vertically

```html
<div class="accordion">
  <div class="accordion-item">
    <div class="accordion-header">
      <span class="accordion-label">Section Title</span>
      <span class="accordion-icon">▾</span>
    </div>
    <div class="accordion-content">Content here</div>
  </div>
</div>
```

### 5. Avatar
Circular avatar component with status indicator:
- Large circle with user silhouette icon (head + shoulders)
- Status dot: small colored circle at bottom-right
- Orange/red dot shown in reference (indicating away/busy)
- Sizes: small (32px), medium (48px), large (64px)

### 6. Banner
Full-width notification bars:
- Dark background with text label + close button (×)
- Color dot row: series of small colored squares/circles showing accent palette
- Close button aligned right
- Variants: default (dark), colored accent strip

### 7. Toast
Compact notification with label + color indicators:
- Inline with text "Toast" label
- Small colored squares showing status
- Close button (×)
- Appears at edge of viewport

### 8. Chips
Small tag/label components:
- Outlined style: `border: 1px solid var(--border-canvas); background: transparent`
- Text inside: small monospace label
- Sizes vary by content
- Can be dismissible or static
- Row layout with gap spacing

```html
<div class="chip-group">
  <span class="chip">Chips</span>
  <span class="chip">Banner</span>
  <span class="chip">Chip</span>
  <span class="chip">Chips</span>
</div>
```

### 9. Sliders & Controls
A family of input controls:

**Slider:** Horizontal track with circular thumb, value markers (colored dots along track)
**Toggle:** Small on/off switch with track, labeled states (e.g., "CLICKOOO0", "RUSRGRF", "RHOODRF" — encoded state labels)
**Buttons (inline):** Small circle/oval buttons, filled black or outlined
**Process indicator:** Track with progress position + encoded state label

All controls use `--text-primary` for active elements, `--border-default` for tracks.

### 10. Cards
Dark rectangular containers showing **color dot grids**:
- Card with header area and grid of colored dots/squares
- Dots arranged in rows and columns (8×6 or similar)
- Colors drawn from the full accent palette
- Multiple card variants: full grid, sparse grid, mixed sizes
- `border: 1px solid var(--border-default)`
- `background: var(--surface-primary)`

### 11. Buttons
Multiple button variants:

**Filled:** `background: #000; color: #fff; border: none`
**Outlined:** `background: transparent; border: 1px solid var(--border-canvas); color: var(--text-on-light)`
**Icon buttons:** Small square buttons with geometric icons
**Sizes:** Small (compact), medium (default), large (full-width)
**Dropdown button:** Button with chevron (▾) indicator
**States:** Default, hover, active, disabled

### 12. Checkboxes
- Unchecked: empty square outline
- Checked: filled square with checkmark (✓)
- Variants shown: outlined check, solid fill check, dark fill, colored fill
- Size: 16×16px or 20×20px

### 13. Line Graph / Charts
Data visualization panel on dark background containing:

**Line chart:** Multiple data series with dashed grid lines, solid data lines, varying peaks/valleys
**Bar chart:** Vertical bars of varying height, single color
**Pie/Donut chart:** Circular chart with dashed outline segments

All charts use:
- White lines/fills on dark background
- Dashed grid lines (`border: 1px dashed var(--border-light)`)
- No axis labels shown (minimal style)
- Circular chart uses dashed stroke

### 14. Metric Callouts
Labeled color legend for data visualization:

```
Signal      ■ A80012
Indicator   ■ F88785
Status      ■ 08C89F
Alert       ■ FD6A3D
Process     ■ 4EBCFF
```

Each row: label text (monospace) + colored square swatch + hex value
Used as legends alongside charts and data tables.

### 15. Form
Dark panel with stacked form fields:
- Text inputs: full-width dark fields with light borders
- Labels above inputs
- Submit/action button at bottom (filled dark or accent)
- Field groups with spacing
- Some fields show placeholder text or filled values (lighter bg)

### 16. Drop-downs
Select/dropdown menu component:
- Trigger: button-like element with up/down chevron (▲)
- Menu: dark panel below with list items
- Items have checkmark (✓) for selected state
- Scrollable if many items
- `border: 1px solid var(--border-default)`

### 17. List
Vertical list view with:
- Left: checkmarks or bullet indicators per row
- Center: text content (multiple lines per item)
- Right: colored dot/square grid (status indicators drawn from accent palette)
- Horizontal separator between rows
- Dark background

### 18. Loaders
Multiple loading animation patterns:

**Grid loaders:** Small dot grids that animate (filled/unfilled patterns cycling)
**Spinner:** Circular arrangement of dots with varying opacity (classic spinner)
**Arc loaders:** Partial circle arcs that rotate
**Multiple variants** shown: 3 grid-style + 3 circular-style

Dots use `--text-primary` at varying opacities (0.2–1.0) to create animation frames.

---

## Layout Patterns

### Panel/Card Container
```css
.panel {
  background: var(--surface-primary);
  border: 1px solid var(--border-default);
  padding: 16px;
  position: relative;
}
.panel-label {
  position: absolute;
  top: 8px;
  left: 12px;
  font-size: 14px;
  color: var(--text-primary);
}
.panel-icon {
  position: absolute;
  top: 8px;
  right: 12px;
  /* Small circular icon or indicator */
}
```

Each panel in the design system has:
- A text label top-left (component name)
- A small circle icon top-right (⊘ indicator)
- Content within

### Grid System
- Component showcase uses a flexible grid
- Major rows divide the page horizontally
- Within rows, panels are sized proportionally
- Gutters: ~12px between panels

### Responsive Approach
Based on the three layout wireframes:
- **Desktop:** Multi-column grids, side-by-side panels
- **Tablet:** Reduced columns, some stacking
- **Phone:** Single column, full-width components

---

## File References

- **Full color & typography tokens:** `references/design-system.md` (this section above)
- **Component HTML/CSS patterns:** `references/component-inventory.md`
- **Interaction patterns & animation specs:** `references/interactions.md`
