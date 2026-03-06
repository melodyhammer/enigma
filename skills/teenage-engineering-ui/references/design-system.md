# Teenage Engineering UI — Design System Tokens

## Full CSS Custom Properties

```css
:root {
  /* ========== SURFACES ========== */
  --te-bg: #F5F5F5;
  --te-bg-white: #F9FAF9;
  --te-bg-pure: #FFFFFF;
  --te-bg-dark: #0F0E12;
  --te-bg-mid: #E5E5E5;

  /* ========== TEXT ========== */
  --te-text: #0F0E12;
  --te-text-secondary: #6B6B6B;
  --te-text-tertiary: #999999;
  --te-text-inverse: #F5F5F5;
  --te-text-inverse-muted: #999999;

  /* ========== BORDERS ========== */
  --te-border: #D5D5D5;
  --te-border-light: #E8E8E8;
  --te-border-dark: #333333;

  /* ========== STATUS ========== */
  --te-sale: #CC0000;

  /* ========== TYPOGRAPHY ========== */
  --te-font: "Univers Next", "Univers", "Helvetica Neue",
             "Arial", -apple-system, sans-serif;
  --te-font-thin: "Univers Next W02 Thin", "Helvetica Neue Thin",
                  "Arial", sans-serif;

  /* Fluid type scale */
  --te-client: 100vw;
  --te-text-xs: calc(var(--te-client) * 0.00918);
  --te-text-sm: calc(var(--te-client) * 0.01327);
  --te-text-base: calc(var(--te-client) * 0.01837);
  --te-text-lg: calc(var(--te-client) * 0.02755);
  --te-text-xl: calc(var(--te-client) * 0.03673);
  --te-text-2xl: calc(var(--te-client) * 0.05);
  --te-text-display: calc(var(--te-client) * 0.07);

  /* Line heights — extremely tight */
  --te-leading-display: 1.02;
  --te-leading-tight: 1.1;
  --te-leading-normal: 1.2;
  --te-leading-relaxed: 1.35;

  /* Font weights — ONLY thin and light */
  --te-weight-thin: 200;
  --te-weight-light: 300;

  /* ========== GRID ========== */
  --te-columns: 12;
  --te-max-width: 980px;
  --te-margin: 4.59%;
  --te-gutter: 10px;
  --te-col-width: 65px;
  --te-baseline: 10px;

  /* ========== SPACING ========== */
  --te-space-xs: 5px;
  --te-space-sm: 10px;
  --te-space-md: 20px;
  --te-space-lg: 40px;
  --te-space-xl: 60px;
  --te-space-2xl: 80px;
  --te-space-3xl: 120px;

  /* ========== MOTION ========== */
  --te-duration: 200ms;
  --te-ease: ease;
}
```

## Base Reset & Globals

```css
*, *::before, *::after {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

html {
  font-size: 16px;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

body {
  font-family: var(--te-font);
  font-weight: var(--te-weight-light);
  font-size: var(--te-text-base);
  line-height: var(--te-leading-normal);
  color: var(--te-text);
  background: var(--te-bg);
}

img {
  max-width: 100%;
  display: block;
}

a {
  color: var(--te-text);
  text-decoration: none;
  transition: opacity var(--te-duration) var(--te-ease);
}

a:hover {
  opacity: 0.6;
}
```

## Container & Grid

```css
.te-container {
  max-width: var(--te-max-width);
  margin: 0 auto;
  padding: 0 var(--te-margin);
}

.te-grid {
  display: grid;
  grid-template-columns: repeat(12, 1fr);
  gap: var(--te-gutter);
}

/* Column spans */
.te-col-1 { grid-column: span 1; }
.te-col-2 { grid-column: span 2; }
.te-col-3 { grid-column: span 3; }
.te-col-4 { grid-column: span 4; }
.te-col-5 { grid-column: span 5; }
.te-col-6 { grid-column: span 6; }
.te-col-8 { grid-column: span 8; }
.te-col-10 { grid-column: span 10; }
.te-col-12 { grid-column: span 12; }
.te-col-full { grid-column: 1 / -1; }

/* Column offsets */
.te-start-2 { grid-column-start: 2; }
.te-start-3 { grid-column-start: 3; }
.te-start-4 { grid-column-start: 4; }
.te-start-5 { grid-column-start: 5; }

@media (max-width: 980px) {
  .te-col-3,
  .te-col-4,
  .te-col-6 { grid-column: span 12; }
}

@media (max-width: 640px) {
  .te-container { padding: 0 20px; }
}
```

## Typography Classes

```css
/* Display — thinnest, largest */
.te-display {
  font-weight: var(--te-weight-thin);
  font-size: var(--te-text-display);
  line-height: var(--te-leading-display);
  letter-spacing: -0.01em;
}

.te-2xl {
  font-weight: var(--te-weight-thin);
  font-size: var(--te-text-2xl);
  line-height: var(--te-leading-display);
}

.te-xl {
  font-weight: var(--te-weight-light);
  font-size: var(--te-text-xl);
  line-height: var(--te-leading-tight);
}

.te-lg {
  font-weight: var(--te-weight-light);
  font-size: var(--te-text-lg);
  line-height: var(--te-leading-tight);
}

.te-base {
  font-weight: var(--te-weight-light);
  font-size: var(--te-text-base);
  line-height: var(--te-leading-normal);
}

.te-sm {
  font-weight: var(--te-weight-light);
  font-size: var(--te-text-sm);
  line-height: var(--te-leading-normal);
}

.te-xs {
  font-weight: var(--te-weight-light);
  font-size: var(--te-text-xs);
  line-height: var(--te-leading-relaxed);
}

/* Utility */
.te-thin { font-weight: var(--te-weight-thin); }
.te-light { font-weight: var(--te-weight-light); }
.te-uppercase { text-transform: uppercase; }
.te-secondary { color: var(--te-text-secondary); }
.te-tertiary { color: var(--te-text-tertiary); }
```

## Dividers

```css
.te-divider {
  border: none;
  border-top: 1px solid var(--te-border);
  margin: var(--te-space-lg) 0;
}

.te-divider--light {
  border-top-color: var(--te-border-light);
}

.te-divider--flush {
  margin: 0;
}

.te-divider--section {
  margin: var(--te-space-xl) 0;
}
```

## Dark Section

```css
.te-dark {
  background: var(--te-bg-dark);
  color: var(--te-text-inverse);
}

.te-dark a { color: var(--te-text-inverse); }
.te-dark a:hover { opacity: 0.6; }
.te-dark .te-secondary { color: var(--te-text-inverse-muted); }
.te-dark .te-divider { border-top-color: var(--te-border-dark); }
```

## Responsive Scaling

```css
/* TE's signature: larger text on smaller screens for readability */
@media (max-width: 980px) {
  :root {
    --te-text-xs: calc(var(--te-client) * 0.0138);
    --te-text-sm: calc(var(--te-client) * 0.0199);
    --te-text-base: calc(var(--te-client) * 0.0276);
    --te-text-lg: calc(var(--te-client) * 0.0413);
    --te-text-xl: calc(var(--te-client) * 0.0551);
  }
}
```
