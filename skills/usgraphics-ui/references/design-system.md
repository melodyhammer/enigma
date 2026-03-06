# U.S. Graphics Company UI — Design System Tokens

## Full CSS Custom Properties

```css
:root {
  /* ========== SURFACES ========== */
  --usg-bg: #F5F3EF;
  --usg-bg-pure: #FFFFFF;
  --usg-bg-muted: #EDEAE4;
  --usg-bg-dark: #1A1A1A;
  --usg-bg-inverse: #000000;
  --usg-bg-specimen: #111111;

  /* ========== TEXT ========== */
  --usg-text: #1A1A1A;
  --usg-text-secondary: #666666;
  --usg-text-tertiary: #999999;
  --usg-text-inverse: #F5F3EF;
  --usg-text-inverse-muted: #AAAAAA;

  /* ========== RULES & BORDERS ========== */
  --usg-rule: #1A1A1A;
  --usg-rule-light: #CCCCCC;
  --usg-rule-hairline: #E0DDD7;
  --usg-border: #CCCCCC;
  --usg-border-dark: #333333;

  /* ========== STATUS ========== */
  --usg-new: #CC3300;
  --usg-available: #1A1A1A;
  --usg-unavailable: #999999;
  --usg-experimental: #996600;
  --usg-link-hover: #CC3300;

  /* ========== TYPOGRAPHY ========== */
  --usg-font-mono: "Berkeley Mono", "SF Mono", "Menlo", "Courier New", monospace;
  --usg-font-condensed: "Univers LT Pro Condensed", "Arial Narrow",
                         "Helvetica Neue Condensed", sans-serif;
  --usg-font-sans: "Helvetica Neue", "Arial", -apple-system, sans-serif;

  --usg-text-display: clamp(2rem, 4vw, 3rem);
  --usg-text-h1: clamp(1.5rem, 3vw, 2rem);
  --usg-text-h2: clamp(1.125rem, 2vw, 1.375rem);
  --usg-text-h3: 1rem;
  --usg-text-body: 0.875rem;
  --usg-text-small: 0.8125rem;
  --usg-text-caption: 0.75rem;
  --usg-text-micro: 0.6875rem;

  --usg-weight-regular: 400;
  --usg-weight-bold: 700;

  --usg-leading-body: 1.7;
  --usg-leading-heading: 1.2;
  --usg-leading-tight: 1.1;

  --usg-tracking-tight: -0.01em;
  --usg-tracking-normal: 0em;
  --usg-tracking-wide: 0.02em;
  --usg-tracking-wider: 0.05em;
  --usg-tracking-widest: 0.1em;

  /* ========== SPACING ========== */
  --usg-space-xs: 4px;
  --usg-space-sm: 8px;
  --usg-space-md: 16px;
  --usg-space-lg: 24px;
  --usg-space-xl: 32px;
  --usg-space-2xl: 48px;
  --usg-space-3xl: 64px;
  --usg-space-4xl: 96px;

  /* ========== LAYOUT ========== */
  --usg-max-width: 960px;
  --usg-max-width-wide: 1200px;
  --usg-reading-width: 720px;
  --usg-margin-desktop: 80px;
  --usg-margin-tablet: 48px;
  --usg-margin-mobile: 20px;

  /* ========== BREAKPOINTS ========== */
  --usg-bp-sm: 640px;
  --usg-bp-md: 768px;
  --usg-bp-lg: 1024px;

  /* ========== MOTION ========== */
  --usg-duration: 150ms;
  --usg-ease: ease;
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
  font-family: var(--usg-font-mono);
  font-weight: var(--usg-weight-regular);
  font-size: var(--usg-text-body);
  line-height: var(--usg-leading-body);
  color: var(--usg-text);
  background: var(--usg-bg);
}

img { max-width: 100%; display: block; }

a {
  color: var(--usg-text);
  text-decoration: underline;
  transition: color var(--usg-duration) var(--usg-ease);
}
a:hover { color: var(--usg-link-hover); }
```

## Document Container

```css
.usg-doc {
  max-width: var(--usg-max-width);
  margin: 0 auto;
  padding: 0 var(--usg-margin-desktop);
}

.usg-doc--wide {
  max-width: var(--usg-max-width-wide);
}

.usg-reading {
  max-width: var(--usg-reading-width);
}

@media (max-width: 1024px) {
  .usg-doc { padding: 0 var(--usg-margin-tablet); }
}

@media (max-width: 640px) {
  .usg-doc { padding: 0 var(--usg-margin-mobile); }
}
```

## Horizontal Rules

```css
.usg-rule {
  border: none;
  border-top: 1px solid var(--usg-rule);
  margin: var(--usg-space-3xl) 0;
}

.usg-rule--light {
  border-top-color: var(--usg-rule-light);
  margin: var(--usg-space-lg) 0;
}

.usg-rule--heavy {
  border-top: 2px solid var(--usg-rule);
  margin: var(--usg-space-4xl) 0;
}

.usg-rule--hairline {
  border-top-color: var(--usg-rule-hairline);
  margin: var(--usg-space-md) 0;
}

.usg-rule--flush {
  margin: 0;
}
```

## Typography Classes

```css
/* Headings — always condensed, always uppercase */
.usg-display {
  font-family: var(--usg-font-condensed);
  font-size: var(--usg-text-display);
  font-weight: var(--usg-weight-bold);
  text-transform: uppercase;
  letter-spacing: var(--usg-tracking-wide);
  line-height: var(--usg-leading-tight);
}

.usg-h1 {
  font-family: var(--usg-font-condensed);
  font-size: var(--usg-text-h1);
  font-weight: var(--usg-weight-bold);
  text-transform: uppercase;
  letter-spacing: var(--usg-tracking-wide);
  line-height: var(--usg-leading-heading);
}

.usg-h2 {
  font-family: var(--usg-font-condensed);
  font-size: var(--usg-text-h2);
  font-weight: var(--usg-weight-bold);
  text-transform: uppercase;
  letter-spacing: var(--usg-tracking-wide);
  line-height: var(--usg-leading-heading);
}

.usg-h3 {
  font-family: var(--usg-font-condensed);
  font-size: var(--usg-text-h3);
  font-weight: var(--usg-weight-bold);
  text-transform: uppercase;
  letter-spacing: var(--usg-tracking-wider);
  line-height: var(--usg-leading-heading);
}

/* Body — always mono */
.usg-body {
  font-family: var(--usg-font-mono);
  font-size: var(--usg-text-body);
  line-height: var(--usg-leading-body);
}

.usg-body--small {
  font-size: var(--usg-text-small);
}

/* Catalog number */
.usg-catalog-no {
  font-family: var(--usg-font-mono);
  font-size: var(--usg-text-body);
  letter-spacing: var(--usg-tracking-widest);
  color: var(--usg-text-tertiary);
  text-transform: uppercase;
}

/* Label */
.usg-label {
  font-family: var(--usg-font-condensed);
  font-size: var(--usg-text-caption);
  font-weight: var(--usg-weight-bold);
  text-transform: uppercase;
  letter-spacing: var(--usg-tracking-wider);
  color: var(--usg-text-secondary);
}

/* Caption */
.usg-caption {
  font-family: var(--usg-font-mono);
  font-size: var(--usg-text-caption);
  color: var(--usg-text-tertiary);
}

/* Status */
.usg-status { font-family: var(--usg-font-condensed); font-size: var(--usg-text-micro); font-weight: var(--usg-weight-bold); text-transform: uppercase; letter-spacing: 0.08em; }
.usg-status--new { color: var(--usg-new); }
.usg-status--available { color: var(--usg-available); }
.usg-status--unavailable { color: var(--usg-unavailable); }
.usg-status--experimental { color: var(--usg-experimental); }
```

## Section Spacing

```css
.usg-section {
  padding: var(--usg-space-3xl) 0;
}

.usg-section--lg {
  padding: var(--usg-space-4xl) 0;
}

.usg-section + .usg-section {
  border-top: 1px solid var(--usg-rule);
}
```

## Dark Panel

```css
.usg-dark {
  background: var(--usg-bg-dark);
  color: var(--usg-text-inverse);
}

.usg-dark .usg-label { color: var(--usg-text-inverse-muted); }
.usg-dark .usg-caption { color: var(--usg-text-inverse-muted); }
.usg-dark .usg-catalog-no { color: var(--usg-text-inverse-muted); }
.usg-dark .usg-rule { border-top-color: var(--usg-border-dark); }
.usg-dark a { color: var(--usg-text-inverse); }
.usg-dark a:hover { color: var(--usg-new); }
```

## Utility Classes

```css
.usg-uppercase { text-transform: uppercase; }
.usg-mono { font-family: var(--usg-font-mono); }
.usg-condensed { font-family: var(--usg-font-condensed); }
.usg-text-center { text-align: center; }
.usg-text-right { text-align: right; }
.usg-text-secondary { color: var(--usg-text-secondary); }
.usg-text-tertiary { color: var(--usg-text-tertiary); }
.usg-mt-sm { margin-top: var(--usg-space-sm); }
.usg-mt-md { margin-top: var(--usg-space-md); }
.usg-mt-lg { margin-top: var(--usg-space-lg); }
.usg-mt-xl { margin-top: var(--usg-space-xl); }
.usg-mt-2xl { margin-top: var(--usg-space-2xl); }
.usg-mb-sm { margin-bottom: var(--usg-space-sm); }
.usg-mb-md { margin-bottom: var(--usg-space-md); }
.usg-mb-lg { margin-bottom: var(--usg-space-lg); }
.usg-mb-xl { margin-bottom: var(--usg-space-xl); }
```
