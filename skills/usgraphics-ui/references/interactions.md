# U.S. Graphics Company UI — Interactions & Page Structure

## Core Principle: Almost No Animation

This is the most important thing about USGC interactions: **there are almost none.**

The page is a document. Documents don't animate. Content loads and is immediately visible. No scroll reveals, no fade-ins, no parallax, no loading skeletons, no progress indicators beyond plain text.

---

## Allowed Interactions

### Link Hover
```css
a {
  text-decoration: underline;
  transition: color 150ms ease;
}
a:hover {
  color: var(--usg-link-hover); /* #CC3300 */
}
```

### Button Hover
```css
.usg-btn:hover {
  background: var(--usg-text);
  color: var(--usg-bg);
}
```
Transition: 150ms ease. The border-outlined button fills with black on hover, text goes cream.

### Table Row Hover
```css
.usg-spec-table tbody tr:hover {
  background: var(--usg-bg-muted); /* #EDEAE4 */
}
```
Subtle, no transition — instant background change.

### Input Focus
```css
.usg-input:focus {
  border-color: var(--usg-text); /* 1px border goes from gray to black */
}
```
Transition: 150ms ease.

### Glyph Hover (Character Grid)
```css
.usg-glyph-grid span:hover {
  background: var(--usg-bg-muted);
}
```
Instant, no transition.

---

## What NOT to Do

- No `IntersectionObserver` scroll reveals
- No `opacity: 0 → 1` animations on page load
- No `translateY` slide-up effects
- No parallax scrolling
- No loading spinners or skeleton screens
- No animated counters
- No hover transforms (scale, translateY)
- No transition on page navigation
- No animated dots, waves, particles, or decorative motion
- No CSS keyframe animations (except cursor blink if implementing a terminal)

The visual interest comes from **typography, layout, and content** — not from motion.

---

## Page Structure Template

Every page follows this document structure:

```javascript
// Page structure (conceptual)
const pageStructure = {
  header: {
    logo: "U.S. GRAPHICS COMPANY",
    nav: ["Office", "Products", "Catalog", "Extras", "Sitemap", "Login"]
  },
  rule: "1px solid black",  // after header ALWAYS

  titleBlock: {
    catalogNo: "TX-02",     // mono, tertiary color, letter-spaced
    title: "BERKELEY MONO", // condensed, display size, uppercase
    subtitle: "TYPEFACE"    // condensed, label size, secondary color
  },
  rule: "1px solid black",

  specimenBanner: {
    bg: "#111111",
    content: "Specimen text in the typeface",
    meta: "Font name — Weight info"
  },
  rule: "1px solid black",

  sections: [
    {
      heading: "DESCRIPTION",  // condensed, h2, uppercase
      body: "Monospace body text...",
      rule: "after"
    },
    {
      heading: "SPECIFICATIONS",
      content: "Specification table",
      rule: "after"
    },
    {
      heading: "AVAILABILITY",
      content: "Pricing block + CTA button",
      rule: "after"
    }
  ],

  footer: {
    copyright: "© 2026 U.S. Graphics Company",
    version: "Production v2.4.1"
  }
};
```

---

## Responsive Behavior

The page is a single-column document. Responsive behavior is minimal:

```css
/* Desktop: full width with generous margins */
@media (min-width: 1025px) {
  .usg-doc { padding: 0 80px; }
}

/* Tablet: slightly narrower margins */
@media (max-width: 1024px) {
  .usg-doc { padding: 0 48px; }
  .usg-metric-grid { grid-template-columns: repeat(2, 1fr); }
}

/* Mobile: tight margins, single column */
@media (max-width: 640px) {
  .usg-doc { padding: 0 20px; }
  .usg-header__inner { flex-direction: column; gap: 16px; }
  .usg-header__nav { flex-wrap: wrap; gap: 16px; }
  .usg-metric-grid { grid-template-columns: 1fr; }
  .usg-spec-table__label { width: auto; }
  .usg-glyph-grid { grid-template-columns: repeat(auto-fill, minmax(48px, 1fr)); }
}
```

The document never tries to be "mobile-first" in the contemporary sense — it's a document that narrows gracefully. No hamburger menus, no off-canvas panels, no bottom sheets.

---

## Print Styles

Since this IS a document, print styles are a natural fit:

```css
@media print {
  body { background: white; color: black; }
  .usg-header__nav { display: none; }
  .usg-specimen { break-inside: avoid; }
  .usg-btn { display: none; }
  a { color: black; text-decoration: underline; }
  a::after { content: " (" attr(href) ")"; font-size: 10px; }
  .usg-rule { border-top-color: #000; }
}
```

---

## Keyboard Navigation

```css
/* Focus styles — visible, squared, functional */
a:focus-visible,
.usg-btn:focus-visible,
.usg-input:focus-visible {
  outline: 2px solid var(--usg-text);
  outline-offset: 2px;
}

/* Skip link */
.usg-skip {
  position: absolute;
  top: -40px;
  left: 0;
  background: var(--usg-text);
  color: var(--usg-bg);
  padding: 8px 16px;
  font-family: var(--usg-font-condensed);
  font-size: 13px;
  font-weight: 700;
  text-transform: uppercase;
  text-decoration: none;
  z-index: 300;
}

.usg-skip:focus {
  top: 0;
}
```

---

## Dark Panel Content

When rendering content inside dark specimen panels:

```css
.usg-dark {
  background: var(--usg-bg-specimen);
  color: var(--usg-text-inverse);
  padding: var(--usg-space-2xl);
}

.usg-dark .usg-label,
.usg-dark .usg-caption {
  color: var(--usg-text-inverse-muted);
}

.usg-dark .usg-rule {
  border-top-color: var(--usg-border-dark);
}

.usg-dark .usg-btn {
  border-color: var(--usg-text-inverse);
  color: var(--usg-text-inverse);
}

.usg-dark .usg-btn:hover {
  background: var(--usg-text-inverse);
  color: var(--usg-bg-specimen);
}

.usg-dark .usg-spec-table tbody td {
  border-bottom-color: var(--usg-border-dark);
}
```
