# Nothing Tech UI — Design System Tokens

## Full CSS Custom Properties

```css
:root {
  /* ========== SURFACES ========== */
  --nt-bg-primary: #FFFFFF;
  --nt-bg-secondary: #F7F7F7;
  --nt-bg-tertiary: #F0F0F0;
  --nt-bg-inverse: #000000;
  --nt-bg-inverse-soft: #1A1A1A;

  /* ========== TEXT ========== */
  --nt-text-primary: #000000;
  --nt-text-secondary: #666666;
  --nt-text-tertiary: #999999;
  --nt-text-inverse: #FFFFFF;
  --nt-text-inverse-muted: #AAAAAA;

  /* ========== BORDERS ========== */
  --nt-border: #E5E5E5;
  --nt-border-strong: #CCCCCC;
  --nt-border-inverse: #333333;
  --nt-divider: #F0F0F0;

  /* ========== ACCENT ========== */
  --nt-accent: #D71921;
  --nt-accent-hover: #B5141A;

  /* ========== DOT MATRIX ========== */
  --nt-dot: #E0E0E0;
  --nt-dot-active: #000000;
  --nt-dot-inverse: #333333;
  --nt-dot-inverse-active: #FFFFFF;

  /* ========== FUNCTIONAL ========== */
  --nt-success: #00C853;
  --nt-error: #D71921;
  --nt-warning: #FF9100;

  /* ========== TYPOGRAPHY ========== */
  --nt-font: "Nothing Sans", "Helvetica Neue", "Arial", -apple-system, sans-serif;
  --nt-font-mono: "Nothing Mono", "SF Mono", "Courier New", monospace;

  --nt-text-hero: clamp(3rem, 5vw, 4.5rem);
  --nt-text-h1: clamp(2rem, 3.5vw, 3rem);
  --nt-text-h2: clamp(1.5rem, 2.5vw, 2rem);
  --nt-text-h3: 1.25rem;
  --nt-text-body-lg: 1.125rem;
  --nt-text-body: 1rem;
  --nt-text-body-sm: 0.875rem;
  --nt-text-caption: 0.75rem;
  --nt-text-micro: 0.625rem;

  --nt-weight-regular: 400;
  --nt-weight-medium: 500;

  --nt-leading-tight: 1.1;
  --nt-leading-snug: 1.3;
  --nt-leading-normal: 1.6;

  --nt-tracking-tight: -0.02em;
  --nt-tracking-normal: 0em;
  --nt-tracking-wide: 0.05em;
  --nt-tracking-wider: 0.08em;

  /* ========== SPACING ========== */
  --nt-space-xs: 4px;
  --nt-space-sm: 8px;
  --nt-space-md: 16px;
  --nt-space-lg: 24px;
  --nt-space-xl: 32px;
  --nt-space-2xl: 48px;
  --nt-space-3xl: 64px;
  --nt-space-4xl: 96px;
  --nt-space-5xl: 128px;

  /* ========== LAYOUT ========== */
  --nt-max-width: 1440px;
  --nt-gutter: 24px;
  --nt-margin-desktop: 80px;
  --nt-margin-tablet: 48px;
  --nt-margin-mobile: 20px;

  /* ========== BREAKPOINTS ========== */
  --nt-bp-sm: 640px;
  --nt-bp-md: 768px;
  --nt-bp-lg: 1024px;
  --nt-bp-xl: 1280px;
  --nt-bp-2xl: 1440px;

  /* ========== MOTION ========== */
  --nt-ease-out: cubic-bezier(0.16, 1, 0.3, 1);
  --nt-ease-in-out: cubic-bezier(0.65, 0, 0.35, 1);
  --nt-duration-fast: 200ms;
  --nt-duration-normal: 300ms;
  --nt-duration-slow: 600ms;

  /* ========== ELEVATION ========== */
  --nt-shadow-sm: 0 1px 2px rgba(0, 0, 0, 0.05);
  --nt-shadow-md: 0 4px 12px rgba(0, 0, 0, 0.08);
  --nt-shadow-lg: 0 8px 24px rgba(0, 0, 0, 0.12);

  /* ========== BORDER RADIUS ========== */
  --nt-radius-none: 0px;
  --nt-radius-sm: 2px;
  --nt-radius-full: 9999px;  /* Pills only — for color dots, tags */
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
  scroll-behavior: smooth;
}

body {
  font-family: var(--nt-font);
  font-weight: var(--nt-weight-regular);
  line-height: var(--nt-leading-normal);
  color: var(--nt-text-primary);
  background: var(--nt-bg-primary);
}

img {
  max-width: 100%;
  display: block;
}

a {
  color: inherit;
  text-decoration: none;
}
```

## Grid System

```css
.nt-container {
  max-width: var(--nt-max-width);
  margin: 0 auto;
  padding: 0 var(--nt-margin-desktop);
}

@media (max-width: 1024px) {
  .nt-container { padding: 0 var(--nt-margin-tablet); }
}

@media (max-width: 640px) {
  .nt-container { padding: 0 var(--nt-margin-mobile); }
}

.nt-grid {
  display: grid;
  grid-template-columns: repeat(12, 1fr);
  gap: var(--nt-gutter);
}

.nt-col-6 { grid-column: span 6; }
.nt-col-4 { grid-column: span 4; }
.nt-col-3 { grid-column: span 3; }
.nt-col-full { grid-column: 1 / -1; }

@media (max-width: 768px) {
  .nt-col-6,
  .nt-col-4,
  .nt-col-3 { grid-column: 1 / -1; }
}
```

## Dot-Matrix Patterns

```css
/* Standard dot grid — light surface */
.nt-dots {
  background-image: radial-gradient(circle, var(--nt-dot) 1px, transparent 1px);
  background-size: 20px 20px;
}

/* Dense dot grid */
.nt-dots-dense {
  background-image: radial-gradient(circle, var(--nt-dot) 0.8px, transparent 0.8px);
  background-size: 12px 12px;
}

/* Sparse dot grid */
.nt-dots-sparse {
  background-image: radial-gradient(circle, var(--nt-dot) 1.2px, transparent 1.2px);
  background-size: 32px 32px;
}

/* Dark surface dot grids */
.nt-dots-inverse {
  background-image: radial-gradient(circle, var(--nt-dot-inverse) 1px, transparent 1px);
  background-size: 20px 20px;
}

.nt-dots-inverse-dense {
  background-image: radial-gradient(circle, var(--nt-dot-inverse) 0.8px, transparent 0.8px);
  background-size: 12px 12px;
}
```

## Dark Section Variant

```css
.nt-dark {
  background: var(--nt-bg-inverse);
  color: var(--nt-text-inverse);
}

.nt-dark .nt-text-secondary { color: var(--nt-text-inverse-muted); }
.nt-dark .nt-border { border-color: var(--nt-border-inverse); }
.nt-dark .nt-divider { border-color: var(--nt-border-inverse); }

.nt-dark .nt-btn-primary {
  background: var(--nt-text-inverse);
  color: var(--nt-bg-inverse);
}

.nt-dark .nt-btn-secondary {
  background: transparent;
  color: var(--nt-text-inverse);
  border-color: var(--nt-text-inverse);
}
```

## Utility Classes

```css
/* Text */
.nt-uppercase { text-transform: uppercase; letter-spacing: var(--nt-tracking-wider); }
.nt-sentence { text-transform: none; }
.nt-mono { font-family: var(--nt-font-mono); }
.nt-medium { font-weight: var(--nt-weight-medium); }

/* Spacing */
.nt-section { padding: var(--nt-space-5xl) 0; }
.nt-section-sm { padding: var(--nt-space-3xl) 0; }

/* Layout */
.nt-flex { display: flex; }
.nt-flex-center { display: flex; align-items: center; justify-content: center; }
.nt-flex-between { display: flex; align-items: center; justify-content: space-between; }
.nt-gap-sm { gap: var(--nt-space-sm); }
.nt-gap-md { gap: var(--nt-space-md); }
.nt-gap-lg { gap: var(--nt-space-lg); }
.nt-gap-xl { gap: var(--nt-space-xl); }

/* Text alignment */
.nt-text-center { text-align: center; }
.nt-text-left { text-align: left; }

/* Full bleed */
.nt-full-bleed {
  width: 100vw;
  margin-left: calc(-50vw + 50%);
}
```
