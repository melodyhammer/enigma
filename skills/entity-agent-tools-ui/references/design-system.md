# Design System — Entity Agent Tools Site

## Color Tokens (CSS Custom Properties)

### Core Palette
| Token | Value | Usage |
|-------|-------|-------|
| `--bg` | `#f5f3f0` | Page background (warm beige) |
| `--fg` | `#0a0a0a` | Primary text, dark elements |
| `--muted` | `#737373` | Secondary text, labels, counter |
| `--border` | `#ddd9d3` | Card borders, dividers, grid lines |
| `--card` | `#ffffff` | Card backgrounds |
| `--accent` | `#10b981` | Emerald green — CTAs, active states, highlights |
| `--accent-dim` | `rgba(16, 185, 129, 0.08)` | Subtle accent tint for backgrounds |

### Hero (Dark Section)
| Token | Value | Usage |
|-------|-------|-------|
| Hero bg | `#0a0a0a` | Section 01 background |
| Hero text | `#ffffff` | Hero heading |
| Hero body | `rgba(255,255,255,0.85)` | Hero paragraph text |
| Glitch color | `#F3EEEA` | p5.js shader output color |
| Vignette | `radial-gradient(ellipse at center, transparent 40%, rgba(0,0,0,0.5) 100%)` | Hero overlay |

### Architecture Stack Gradients
| Layer | Gradient |
|-------|----------|
| Inference | `linear-gradient(135deg, #E8704A, #a855f7)` |
| Orchestration | `linear-gradient(135deg, #6366f1, #3b82f6)` |
| Entity Resolution | `linear-gradient(135deg, var(--accent), #059669)` |
| Foundation | `var(--fg)` (solid black) |

### D3 Graph Node Colors
| Node Type | Color |
|-----------|-------|
| Center (LAC) | `#2D8A6E` |
| Officers | `#D4A853` |
| Funds | `#C9735B` |
| Properties | `#6B9DBF` |
| GP/LP | `#5BA690` |
| States | `#4A6FA5` |

### Utility Colors
| Usage | Value |
|-------|-------|
| Card hover shadow | `rgba(0,0,0,0.1)` |
| Image overlay gradient | `linear-gradient(to top, rgba(0,0,0,0.7), rgba(0,0,0,0.3))` |
| Grid background | `0.04 opacity` lines on `--bg` |
| Nav dot container bg | `rgba(245,243,240,0.85)` |

---

## Typography

### Font Stacks
```css
/* Primary — used for headings, labels, data, code */
font-family: "Berkeley Mono", monospace;

/* Body fallback */
font-family: "Inter", -apple-system, BlinkMacSystemFont, sans-serif;
```

### Font Weights (Self-hosted woff2)
| Weight | File | Usage |
|--------|------|-------|
| 400 (Regular) | `BerkeleyMono-Regular.woff2` | Body text, data values |
| 500 (Medium) | `BerkeleyMono-Medium.woff2` | Labels, emphasis |
| 600 (SemiBold) | `BerkeleyMono-SemiBold.woff2` | Section tags, counter, nav |
| 700 (Bold) | `BerkeleyMono-Bold.woff2` | Headings, stat numbers, section watermarks |

All loaded with `font-display: swap`.

### Type Scale
| Element | Size | Weight | Extra |
|---------|------|--------|-------|
| H1 (hero) | `clamp(48px, 8vw, 84px)` | 700 | uppercase, `letter-spacing: 0.04em` |
| H2 (section) | `clamp(32px, 5vw, 48px)` | 600 | uppercase |
| H3 (card/subsection) | 18px | 600 | uppercase, `letter-spacing: 0.04em` |
| Body | `clamp(14px, 3.5vw, 16px)` | 400 | `line-height: 1.5` |
| Stat values | `clamp(20px, 3vw, 28px)` on tablet, larger on desktop | 700 | monospace |
| Data rows | 13px | 400 | monospace |
| Section watermark | `clamp(48px, 15vw, 180px)` | 700 | opacity 0.06 |
| Counter | 12px | 600 | `var(--muted)` |
| Nav dots | 6px diameter | — | Visual only |

---

## Spacing

### Section Padding
| Breakpoint | Padding |
|------------|---------|
| Desktop (≥1025px) | `80px 48px` |
| Tablet (769–1024px) | `60px 24px` |
| Mobile (≤768px) | `40px 20px` |

### Component Gaps
```
6px   — nav dot spacing, tight inline gaps
10px  — nav container padding
12px  — card internal small gaps, monogram offset
16px  — stat card padding (tablet), standard component gap
20px  — card header padding
24px  — section content gaps, mobile section padding
28px  — medium component spacing
32px  — desktop fixed element offsets (logo, counter)
```

### Grid Gaps
- Stat grid: `1px` (creates line effect)
- Comparison grid: standard CSS grid gap
- Business card grid: responsive gap
- Use case grid: standard gap

---

## Borders & Radius

| Element | Border | Radius |
|---------|--------|--------|
| Cards | `1px solid var(--border)` | `2px` |
| Nav container | `1px solid var(--border)` | `100px` (pill) |
| Nav dots | `1px solid var(--muted)` | `50%` (circle) |
| Buttons | `1px solid var(--border)` | `2px` |
| Stack layers | none | `2px` |

---

## Shadows

| Context | Value |
|---------|-------|
| Card default | none or very subtle |
| Card hover | `0 8px 24px rgba(0,0,0,0.1)` |
| Nav dot active glow | `0 0 6px var(--accent)` |
| D3 center node glow | SVG filter (gaussian blur) |

---

## Animation Tokens

### Scroll Reveal
```css
/* Initial state */
opacity: 0;
transform: translateY(30px);

/* Visible state */
opacity: 1;
transform: translateY(0);
transition: opacity 0.6s cubic-bezier(0.4, 0, 0.2, 1),
            transform 0.6s cubic-bezier(0.4, 0, 0.2, 1);
```

### Card Hover
```css
transition: transform 0.2s ease, box-shadow 0.2s ease;
/* Hover */
transform: translateY(-2px);
box-shadow: 0 8px 24px rgba(0,0,0,0.1);
```

### Image Reveal (Card Header)
```css
.card-bg { opacity: 0; transition: opacity 0.3s ease; }
.biz-card:hover .card-bg { opacity: 1; }
.monogram { opacity: 1; transition: opacity 0.3s ease; }
.biz-card:hover .monogram { opacity: 0; }
```

### Pulse (Live Indicator)
```css
@keyframes pulse {
  0%, 100% { transform: scale(1); opacity: 0.5; }
  50% { transform: scale(1.2); opacity: 1; }
}
animation: pulse 2s ease-in-out infinite;
```

### Scroll Bounce (Hero)
```css
@keyframes scroll-bounce {
  0%, 100% { transform: translateY(0); }
  50% { transform: translateY(8px); }
}
animation: scroll-bounce 2s ease-in-out infinite;
```

### Nav Dot Active
```css
.active {
  background: var(--accent);
  border-color: var(--accent);
  transform: scale(1.3);
  box-shadow: 0 0 6px var(--accent);
}
```

---

## Responsive Breakpoints

| Name | Range | Key Changes |
|------|-------|-------------|
| Desktop | ≥1025px | Full layout, scroll-snap, nav dots visible |
| Tablet | 769–1024px | Reduced stat sizes, 1-col comparison, reduced padding |
| Mobile | ≤768px | No scroll-snap, no nav dots, no scroll indicator, stacked layouts |
| Small | ≤480px | Further reduced fonts, 1-col stats, minimal padding |
