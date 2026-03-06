# Teenage Engineering UI — Interactions & Layout Specs

## Core Principle: Near-Zero Interaction

Teenage Engineering pages are essentially static documents with hyperlinks. The interaction model is web 1.0 in philosophy — content renders, you scroll, you click links. That's it.

---

## Allowed Interactions

### Link/CTA Hover
```css
a:hover { opacity: 0.6; }
```
Transition: `opacity 200ms ease`. This is the ONLY hover effect.

### Focus States
```css
a:focus-visible,
button:focus-visible,
input:focus-visible {
  outline: 1px solid var(--te-text);
  outline-offset: 2px;
}
```

### Form Input Focus
```css
input:focus {
  border-color: var(--te-text);
}
```

---

## What NOT to Do

- No scroll-triggered animations
- No parallax
- No loading spinners or skeletons
- No hover transforms (no scale, translateY, rotate)
- No animated counters
- No transition on background colors
- No keyframe animations
- No intersection observers for reveal effects
- No hamburger menu animation (just toggle visibility)
- No smooth scroll to sections (native only)
- No cursor effects
- No micro-interactions

---

## Page Layout Template

```
┌──────────────────────────────────────┐
│ logo                     nav links   │ ← thin bar, no bg, no border
│                                      │
│──────────────────────────────────────│ (whitespace, no rule)
│                                      │
│         [LARGE PRODUCT IMAGE]        │ ← 60-80% width, centered
│                                      │
│ EP–133 K.O.II                        │ ← thin, 2xl
│ sampler. sequencer. drum machine.    │ ← light, base, secondary
│ $329                                 │ ← thin, lg
│ buy now                              │ ← underline text link
│                                      │
│──────────────────────────────────────│ (1px divider)
│                                      │
│ features                             │ ← light, xl
│                                      │
│ ─ feature text one                   │ ← bordered list
│ ─ feature text two                   │
│ ─ feature text three                 │
│                                      │
│──────────────────────────────────────│
│                                      │
│         [PRODUCT IMAGE 2]            │
│                                      │
│ body text about the product.         │ ← 6-col width, light
│ short, factual, no fluff.            │
│                                      │
│──────────────────────────────────────│
│                                      │
│ specifications                       │
│ speaker          2W                  │
│ battery          12hrs               │ ← spec table
│ connectivity     USB-C, BT 5.0      │
│ sample rate      44.1kHz / 16-bit    │
│                                      │
│──────────────────────────────────────│
│ © teenage engineering 2026           │ ← xs, secondary
└──────────────────────────────────────┘
```

---

## Fluid Typography Implementation

The signature TE approach — all sizes derive from viewport width:

```javascript
// Conceptual — TE calculates client-width and applies proportional sizes
// In practice, CSS calc() with vw units achieves this:

// At 980px viewport:
// xs  = 980 * 0.00918 = 9px
// sm  = 980 * 0.01327 = 13px
// base = 980 * 0.01837 = 18px
// lg  = 980 * 0.02755 = 27px
// xl  = 980 * 0.03673 = 36px
// 2xl = 980 * 0.05    = 49px
// display = 980 * 0.07 = 69px

// On mobile (375px):
// With adt20x scaling (1.5x multiplier):
// xs  = 375 * 0.0138  = 5px → bumped to minimum
// sm  = 375 * 0.0199  = 7.5px
// base = 375 * 0.0276  = 10.3px
// lg  = 375 * 0.0413  = 15.5px
```

Practical CSS implementation:
```css
:root {
  --te-text-base: clamp(14px, 1.84vw, 18px);
  --te-text-sm: clamp(11px, 1.33vw, 13px);
  --te-text-lg: clamp(20px, 2.76vw, 27px);
  --te-text-xl: clamp(24px, 3.67vw, 36px);
  --te-text-2xl: clamp(32px, 5vw, 49px);
  --te-text-display: clamp(40px, 7vw, 69px);
}
```

---

## Responsive Behavior

### Desktop (>980px)
- Full 12-column grid, max 980px centered
- Side margins: 4.59% of viewport
- All type sizes at 1× scale

### Tablet (641px–980px)
- Grid collapses: 6-col items → 12-col
- Type sizes scale up by ~1.5× (adt15x/adt20x)
- Margins: 4.59% maintained
- Nav links may wrap or hide

### Mobile (≤640px)
- Everything single-column
- Type sizes at 1.5–2× mobile scale
- Margins: 20px fixed
- Nav: simplified, stacked
- Product grid: 1-2 columns
- Images: full-width

### Key responsive principle
TE scales text UP on smaller screens — the opposite of most sites. This ensures readability of their thin type on small displays.

---

## Image Handling

```css
/* Product images: always contained, never cropped */
.te-product-image {
  width: 100%;
  height: auto;
  object-fit: contain;
  background: transparent;
}

/* Hero images: can be wider */
.te-hero-image {
  width: 100%;
  max-height: 80vh;
  object-fit: contain;
}

/* Thumbnail: square, contained */
.te-thumb {
  width: 100%;
  aspect-ratio: 1 / 1;
  object-fit: contain;
}
```

No lazy loading effects, no blur-up, no fade-in. Images load and appear.

---

## Print Styles

```css
@media print {
  body { background: white; }
  .te-nav, .te-footer__links { display: none; }
  a { text-decoration: underline; color: black; }
  .te-hero__image img { max-height: 400px; }
}
```

---

## Keyboard Accessibility

```css
:focus-visible {
  outline: 1px solid var(--te-text);
  outline-offset: 2px;
}

.te-dark :focus-visible {
  outline-color: var(--te-text-inverse);
}

/* Skip link */
.te-skip {
  position: absolute;
  top: -40px;
  left: 0;
  font-size: var(--te-text-sm);
  font-weight: var(--te-weight-light);
  background: var(--te-text);
  color: var(--te-bg);
  padding: var(--te-space-sm) var(--te-space-md);
  text-decoration: none;
  z-index: 100;
}

.te-skip:focus { top: 0; }
```
