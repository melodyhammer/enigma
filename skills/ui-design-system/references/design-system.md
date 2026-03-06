# Design System Tokens — Full Reference

## CSS Custom Properties

```css
:root {
  /* Surfaces */
  --surface-primary: #0a0a0a;
  --surface-elevated: #1a1a1a;
  --surface-canvas: #E0DEE6;
  --surface-input: #000000;

  /* Text */
  --text-primary: #ffffff;
  --text-secondary: #a0a0a0;
  --text-on-light: #0a0a0a;

  /* Borders */
  --border-default: #333333;
  --border-light: #555555;
  --border-canvas: #0a0a0a;

  /* Accent / Metric Colors */
  --color-signal: #A80012;      /* Red — errors, critical */
  --color-indicator: #F88785;   /* Amber/pink — warnings */
  --color-status: #08C89F;      /* Green — success, active */
  --color-alert: #FD6A3D;       /* Coral — urgent notifications */
  --color-process: #4EBCFF;     /* Blue — in-progress, info */

  /* Extended palette (dot grids, data viz) */
  --color-red-dark: #A80012;
  --color-red-mid: #D4453A;
  --color-orange: #FD6A3D;
  --color-peach: #F88785;
  --color-yellow: #F5C542;
  --color-yellow-dark: #E8B830;
  --color-green: #08C89F;
  --color-green-mid: #2DB87A;
  --color-green-dark: #1A7A5A;
  --color-blue: #4EBCFF;
  --color-blue-mid: #3A8FD4;
  --color-blue-dark: #2A6CB0;
  --color-purple: #8B5CF6;
  --color-purple-dark: #6D28D9;

  /* Typography */
  --font-mono: "Berkeley Mono", "SF Mono", "Monaco", "Cascadia Code", "Fira Code", monospace;
  --font-body: "Inter", -apple-system, BlinkMacSystemFont, sans-serif;

  /* Spacing */
  --space-xs: 4px;
  --space-sm: 8px;
  --space-md: 12px;
  --space-lg: 16px;
  --space-xl: 24px;
  --space-2xl: 32px;
  --space-3xl: 48px;

  /* Radii */
  --radius-none: 0;
  --radius-sm: 2px;
  --radius-full: 50%;
  --radius-pill: 100px;

  /* Transitions */
  --transition-fast: 0.15s ease;
  --transition-default: 0.2s ease;
  --transition-slow: 0.3s ease;
}
```

---

## Typography Scale

```css
/* Component panel label */
.label-panel {
  font-family: var(--font-mono);
  font-size: 14px;
  font-weight: 400;
  color: var(--text-primary);
}

/* Section heading */
.heading-section {
  font-family: var(--font-mono);
  font-size: 16px;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.04em;
  color: var(--text-primary);
}

/* Data value */
.text-data {
  font-family: var(--font-mono);
  font-size: 13px;
  font-weight: 700;
  color: var(--text-primary);
}

/* Metric hex value */
.text-metric {
  font-family: var(--font-mono);
  font-size: 13px;
  font-weight: 700;
  /* color set per metric type */
}

/* Body text */
.text-body {
  font-family: var(--font-mono);
  font-size: 12px;
  font-weight: 400;
  line-height: 1.4;
  color: var(--text-secondary);
}

/* Small label (chips, badges) */
.text-small {
  font-family: var(--font-mono);
  font-size: 11px;
  font-weight: 500;
  text-transform: uppercase;
}

/* Tiny annotation */
.text-tiny {
  font-family: var(--font-mono);
  font-size: 10px;
  font-weight: 400;
  color: var(--text-secondary);
}
```

---

## Elevation System

Depth is expressed through **geometric offset stacking**, not blur shadows.

```css
/* Level 0 — Flat */
.elevation-0 {
  border: 1px solid var(--border-default);
}

/* Level 1 — Slight depth */
.elevation-1 {
  border: 1px solid var(--border-default);
  position: relative;
}
.elevation-1::after {
  content: '';
  position: absolute;
  inset: 0;
  border: 1px dashed var(--border-light);
  transform: translate(3px, 3px);
  z-index: -1;
}

/* Level 2 — Medium depth */
.elevation-2::after { transform: translate(6px, 6px); border-style: dashed; }
.elevation-2::before { transform: translate(3px, 3px); border-style: dashed; }

/* Level 3 — Deep (multiple offset layers) */
/* Stack 3-4 pseudo-elements or real elements with:
   - 3px incremental offset per layer
   - Alternating dashed/dotted borders
   - Decreasing opacity per layer */
```

---

## Border Patterns

| Style | CSS | Usage |
|-------|-----|-------|
| Solid default | `1px solid var(--border-default)` | Primary card borders |
| Solid canvas | `1px solid var(--border-canvas)` | Components on light bg (chips) |
| Dashed | `1px dashed var(--border-light)` | Elevation layers, chart grids |
| Dotted | `1px dotted var(--border-light)` | Deep elevation layers, subtle dividers |

---

## Icon Grid

Icons are 24×24px geometric outlines. Categories:

**Row 1:** Grid (4-square), Diamond, Grid (9-dot), Menu (3-line), Expand (arrows)
**Row 2:** Wave, Folder, Home, Clock, Puzzle piece
**Row 3:** Skip-back, Fast-forward, Triangle (play), Alert-triangle, Crosshair
**Row 4:** Triangle-up, Triangle-down, Funnel, Expand-full, Collapse
**Row 5:** QR/grid, Barcode, Plus-circle, Gear/settings, Layout

All rendered as:
```css
.icon {
  width: 24px;
  height: 24px;
  stroke: var(--text-primary);
  stroke-width: 1.5px;
  fill: none;
}
```

---

## Metric Callout Legend

Standard legend component used alongside charts and data tables:

```html
<div class="metric-legend">
  <div class="legend-row">
    <span class="legend-swatch" style="background: var(--color-signal)"></span>
    <span class="legend-label">Signal</span>
    <span class="legend-value" style="color: var(--color-signal)">A80012</span>
  </div>
  <div class="legend-row">
    <span class="legend-swatch" style="background: var(--color-indicator)"></span>
    <span class="legend-label">Indicator</span>
    <span class="legend-value" style="color: var(--color-indicator)">F88785</span>
  </div>
  <div class="legend-row">
    <span class="legend-swatch" style="background: var(--color-status)"></span>
    <span class="legend-label">Status</span>
    <span class="legend-value" style="color: var(--color-status)">08C89F</span>
  </div>
  <div class="legend-row">
    <span class="legend-swatch" style="background: var(--color-alert)"></span>
    <span class="legend-label">Alert</span>
    <span class="legend-value" style="color: var(--color-alert)">FD6A3D</span>
  </div>
  <div class="legend-row">
    <span class="legend-swatch" style="background: var(--color-process)"></span>
    <span class="legend-label">Process</span>
    <span class="legend-value" style="color: var(--color-process)">4EBCFF</span>
  </div>
</div>
```

```css
.metric-legend { display: flex; flex-direction: column; gap: 8px; }
.legend-row { display: flex; align-items: center; gap: 12px; }
.legend-swatch { width: 12px; height: 12px; border-radius: 2px; }
.legend-label { font: 400 13px var(--font-mono); color: var(--text-primary); min-width: 80px; }
.legend-value { font: 700 13px var(--font-mono); }
```
