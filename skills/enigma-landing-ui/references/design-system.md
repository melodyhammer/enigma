# Design System — Enigma Landing Page

## Color Tokens

### Backgrounds
| Token | Value | Usage |
|-------|-------|-------|
| `--bg-primary` | `#000000` | Page background, hero, all sections |
| `--bg-surface` | `#ffffff1a` | Card/panel overlays (white at 10% opacity) |
| `--bg-warm` | `#F3EEEA` | Warm accent backgrounds (rare, used for contrast sections) |
| `--bg-muted` | `#f5f5f5` | Light mode fallback (not used on dark page) |

### Text
| Token | Value | Usage |
|-------|-------|-------|
| `--text-primary` | `#ffffff` | Headings, primary content |
| `--text-secondary` | `#dcdcdc` | Body text, descriptions |
| `--text-muted` | `--color-enigma-gray-200` | Labels, captions, metadata |
| `--text-dim` | `--color-enigma-gray-800` | Disabled/very low emphasis |

### Accents
| Token | Value | Usage |
|-------|-------|-------|
| `--accent-teal` | `--color-enigma-accent-teal` (~`#00D9FF`) | CTAs, highlights, active states, phase headers |
| `--accent-success` | Green tint | Correct/Enigma result indicators |
| `--accent-error` | Red tint | Wrong result / web failure indicators |

### Enigma Gray Scale
Uses CSS custom properties `--color-enigma-gray-{100..900}` for the full gray ramp. Key stops:
- `gray-200`: Muted text, borders
- `gray-400`: Secondary UI elements
- `gray-600`: Dividers, subtle borders
- `gray-800`: Very dim text, disabled states

## Typography

### Font Stacks
```css
--font-mono: "Berkeley Mono", "SF Mono", "Monaco", "Cascadia Code", monospace;
--font-sans: system-ui, -apple-system, "Segoe UI", sans-serif;
```

### Usage Rules
| Context | Font | Weight | Size Pattern |
|---------|------|--------|-------------|
| Headings (h2) | Sans-serif | 700 | 2rem–3rem |
| Section labels (NN) | Monospace | 400 | 0.75rem |
| Section tags | Monospace | 400 | 0.625rem, uppercase, letter-spacing |
| Body text | Sans-serif | 400 | 1rem–1.125rem |
| Stat numbers | Monospace | 700 | 3rem–4rem |
| Terminal output | Monospace | 400 | 0.875rem |
| Table data | Monospace | 400 | 0.8125rem |
| CTA buttons | Sans-serif | 600 | 0.875rem |

### Line Heights
- Headings: 1.1–1.2
- Body: 1.5–1.6
- Terminal/code: 1.4

## Spacing Scale (REM-based)

```
0.25rem  — tight gaps (within components)
0.5rem   — small padding (table cells, inline elements)
0.75rem  — component internal padding
1rem     — standard gap
1.5rem   — section internal spacing
2rem     — between components within a section
4rem     — between sections (vertical rhythm)
6rem     — major section breaks
```

## Layout

### Container
- Max-width: ~1200px centered
- Horizontal padding: 1.5rem (mobile) → 4rem (desktop)
- Sections are full-width backgrounds with contained content

### Grid Patterns
- **Stats grid:** CSS Grid, auto-fill with minmax(200px, 1fr)
- **Comparison tables:** Full-width tables with fixed column widths
- **Side-by-side:** 2-column grid with gap, stacks on mobile
- **Architecture stack:** Single column, stacked layers

### Breakpoints
- Mobile: < 768px (stack layouts, reduce font sizes, 15 FPS canvas)
- Desktop: >= 768px (side-by-side layouts, full font sizes, 30 FPS canvas)

## Animation Tokens

### Scroll Reveal
```css
.animate-in {
  opacity: 0;
  transform: translateY(20px);
  transition: opacity 0.6s ease, transform 0.6s ease;
}
.animate-in.is-visible {
  opacity: 1;
  transform: translateY(0);
}
```

### Type-in Effect
```css
.type-line {
  animation: type-in 0.05s ease forwards;
  animation-delay: calc(var(--line-index) * 0.03s);
}
```

### Ping (live indicator)
```css
animation: ping 2s cubic-bezier(0, 0, 0.2, 1) infinite;
/* Scale + fade out pulse */
```

### Header Transitions
```css
.site-header {
  transition: background 0.3s ease, backdrop-filter 0.3s ease;
}
```

## Component Tokens

### Buttons
```css
.cta-primary {
  background: var(--accent-teal);
  color: #000;
  padding: 0.75rem 1.5rem;
  border-radius: 4px;
  font-weight: 600;
}
.cta-secondary {
  background: transparent;
  color: var(--text-primary);
  border: 1px solid var(--text-muted);
  padding: 0.75rem 1.5rem;
  border-radius: 4px;
}
.toggle-btn {
  background: transparent;
  color: var(--text-muted);
  border: 1px solid var(--color-enigma-gray-600);
  padding: 0.5rem 1rem;
  cursor: pointer;
}
.toggle-btn.active {
  color: var(--accent-teal);
  border-color: var(--accent-teal);
}
```

### Cards / Panels
```css
.panel {
  background: var(--bg-surface);
  border: 1px solid var(--color-enigma-gray-600);
  border-radius: 8px;
  padding: 1.5rem;
}
.terminal-panel {
  background: #0a0a0a;
  border: 1px solid var(--color-enigma-gray-600);
  border-radius: 8px;
  padding: 1.5rem;
  font-family: var(--font-mono);
}
```

### Tables
```css
table {
  width: 100%;
  border-collapse: collapse;
  font-family: var(--font-mono);
  font-size: 0.8125rem;
}
th {
  text-align: left;
  padding: 0.5rem;
  border-bottom: 1px solid var(--color-enigma-gray-600);
  color: var(--text-muted);
  text-transform: uppercase;
  font-size: 0.625rem;
  letter-spacing: 0.05em;
}
td {
  padding: 0.5rem;
  border-bottom: 1px solid var(--color-enigma-gray-800);
  color: var(--text-secondary);
}
```

### Speed Badges
```css
.speed-badge {
  display: inline-block;
  background: var(--accent-teal);
  color: #000;
  padding: 0.125rem 0.5rem;
  border-radius: 2px;
  font-family: var(--font-mono);
  font-size: 0.75rem;
  font-weight: 700;
}
```
