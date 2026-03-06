# Strava Year in Sport UI — Design System Tokens

## Full CSS Custom Properties

```css
:root {
  /* ========== BRAND ========== */
  --yis-orange: #FC4C02;
  --yis-orange-light: #FF6B2B;
  --yis-orange-dark: #E04400;

  /* ========== DARK PANELS ========== */
  --yis-navy: #1D1D3B;
  --yis-navy-light: #2A2A52;
  --yis-charcoal: #1A1A2E;
  --yis-dark: #111111;

  /* ========== ATHLETIC ACCENTS ========== */
  --yis-olive: #4A6741;
  --yis-olive-light: #5C8A50;
  --yis-teal: #1B8A8A;
  --yis-coral: #FF6B6B;
  --yis-gold: #FFB800;

  /* ========== NEUTRALS ========== */
  --yis-white: #FFFFFF;
  --yis-off-white: #F7F7F5;
  --yis-light-gray: #EFEFEF;
  --yis-mid-gray: #B0B0B0;
  --yis-dark-gray: #666666;

  /* ========== TEXT ========== */
  --yis-text-dark: #1A1A1A;
  --yis-text-light: #FFFFFF;
  --yis-text-muted: rgba(255,255,255,0.6);
  --yis-text-muted-dark: #888888;

  /* ========== TYPOGRAPHY ========== */
  --yis-font-display: "Inter", "Helvetica Neue", Arial, sans-serif;
  --yis-font-body: "Inter", -apple-system, "Helvetica Neue", Arial, sans-serif;
  --yis-font-mono: "SF Mono", "Menlo", "Courier New", monospace;

  --yis-text-hero: clamp(72px, 12vw, 160px);
  --yis-text-stat: clamp(48px, 8vw, 96px);
  --yis-text-stat-sm: clamp(36px, 5vw, 64px);
  --yis-text-display: clamp(32px, 4.5vw, 56px);
  --yis-text-h1: clamp(28px, 3.5vw, 44px);
  --yis-text-h2: clamp(22px, 2.5vw, 32px);
  --yis-text-h3: clamp(18px, 2vw, 24px);
  --yis-text-body: 16px;
  --yis-text-body-lg: 18px;
  --yis-text-small: 14px;
  --yis-text-caption: 13px;
  --yis-text-micro: 11px;
  --yis-text-label: 12px;

  --yis-weight-regular: 400;
  --yis-weight-medium: 500;
  --yis-weight-semibold: 600;
  --yis-weight-bold: 700;
  --yis-weight-extrabold: 800;
  --yis-weight-black: 900;

  --yis-leading-stat: 0.9;
  --yis-leading-tight: 1.1;
  --yis-leading-heading: 1.2;
  --yis-leading-body: 1.6;
  --yis-leading-relaxed: 1.8;

  --yis-tracking-tight: -0.02em;
  --yis-tracking-normal: 0em;
  --yis-tracking-wide: 0.04em;
  --yis-tracking-wider: 0.08em;
  --yis-tracking-widest: 0.12em;

  /* ========== SPACING ========== */
  --yis-space-xs: 4px;
  --yis-space-sm: 8px;
  --yis-space-md: 16px;
  --yis-space-lg: 24px;
  --yis-space-xl: 32px;
  --yis-space-2xl: 48px;
  --yis-space-3xl: 64px;
  --yis-space-4xl: 96px;
  --yis-space-5xl: 128px;

  /* ========== LAYOUT ========== */
  --yis-max-width: 1200px;
  --yis-content-width: 960px;
  --yis-reading-width: 640px;
  --yis-padding-desktop: 48px;
  --yis-padding-mobile: 24px;

  /* ========== RADIUS ========== */
  --yis-radius-sm: 8px;
  --yis-radius-md: 16px;
  --yis-radius-lg: 24px;
  --yis-radius-xl: 32px;
  --yis-radius-pill: 100px;
  --yis-radius-circle: 50%;

  /* ========== MOTION ========== */
  --yis-duration-fast: 200ms;
  --yis-duration: 300ms;
  --yis-duration-slow: 600ms;
  --yis-duration-reveal: 800ms;
  --yis-ease: cubic-bezier(0.25, 0.1, 0.25, 1.0);
  --yis-ease-bounce: cubic-bezier(0.34, 1.56, 0.64, 1);

  /* ========== SHADOWS ========== */
  --yis-shadow-sm: 0 2px 8px rgba(0,0,0,0.08);
  --yis-shadow-md: 0 4px 16px rgba(0,0,0,0.12);
  --yis-shadow-lg: 0 8px 32px rgba(0,0,0,0.16);
  --yis-shadow-glow: 0 0 40px rgba(252,76,2,0.3);
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
  font-family: var(--yis-font-body);
  font-weight: var(--yis-weight-regular);
  font-size: var(--yis-text-body);
  line-height: var(--yis-leading-body);
  color: var(--yis-text-dark);
  background: var(--yis-white);
  overflow-x: hidden;
}

img { max-width: 100%; display: block; }

a {
  color: var(--yis-orange);
  text-decoration: none;
  transition: color var(--yis-duration-fast) var(--yis-ease);
}
a:hover { color: var(--yis-orange-dark); }
```

## Container

```css
.yis-container {
  max-width: var(--yis-max-width);
  margin: 0 auto;
  padding: 0 var(--yis-padding-desktop);
}

.yis-container--narrow {
  max-width: var(--yis-content-width);
}

@media (max-width: 768px) {
  .yis-container { padding: 0 var(--yis-padding-mobile); }
}
```

## Color Panel Sections

```css
.yis-panel {
  width: 100%;
  padding: var(--yis-space-4xl) 0;
}

.yis-panel--navy {
  background: linear-gradient(180deg, var(--yis-navy) 0%, var(--yis-charcoal) 100%);
  color: var(--yis-text-light);
}

.yis-panel--orange {
  background: linear-gradient(135deg, var(--yis-orange) 0%, var(--yis-orange-light) 100%);
  color: var(--yis-text-light);
}

.yis-panel--olive {
  background: linear-gradient(135deg, var(--yis-olive) 0%, var(--yis-olive-light) 100%);
  color: var(--yis-text-light);
}

.yis-panel--dark {
  background: var(--yis-dark);
  color: var(--yis-text-light);
}

.yis-panel--light {
  background: var(--yis-off-white);
  color: var(--yis-text-dark);
}
```

## Typography Classes

```css
.yis-stat-hero {
  font-family: var(--yis-font-display);
  font-size: var(--yis-text-hero);
  font-weight: var(--yis-weight-black);
  line-height: var(--yis-leading-stat);
  letter-spacing: var(--yis-tracking-tight);
}

.yis-stat {
  font-family: var(--yis-font-display);
  font-size: var(--yis-text-stat);
  font-weight: var(--yis-weight-extrabold);
  line-height: var(--yis-leading-stat);
  letter-spacing: var(--yis-tracking-tight);
}

.yis-stat-sm {
  font-family: var(--yis-font-display);
  font-size: var(--yis-text-stat-sm);
  font-weight: var(--yis-weight-bold);
  line-height: 1.0;
  letter-spacing: var(--yis-tracking-tight);
}

.yis-display {
  font-family: var(--yis-font-display);
  font-size: var(--yis-text-display);
  font-weight: var(--yis-weight-bold);
  line-height: var(--yis-leading-tight);
}

.yis-h1 {
  font-family: var(--yis-font-display);
  font-size: var(--yis-text-h1);
  font-weight: var(--yis-weight-bold);
  line-height: var(--yis-leading-heading);
}

.yis-h2 {
  font-family: var(--yis-font-display);
  font-size: var(--yis-text-h2);
  font-weight: var(--yis-weight-semibold);
  line-height: var(--yis-leading-heading);
}

.yis-h3 {
  font-family: var(--yis-font-display);
  font-size: var(--yis-text-h3);
  font-weight: var(--yis-weight-semibold);
  line-height: var(--yis-leading-heading);
}

.yis-label {
  font-family: var(--yis-font-body);
  font-size: var(--yis-text-label);
  font-weight: var(--yis-weight-semibold);
  text-transform: uppercase;
  letter-spacing: var(--yis-tracking-wider);
  color: var(--yis-text-muted);
}

.yis-label--dark {
  color: var(--yis-text-muted-dark);
}

.yis-body-lg {
  font-size: var(--yis-text-body-lg);
  line-height: var(--yis-leading-body);
}

.yis-caption {
  font-size: var(--yis-text-caption);
  color: var(--yis-text-muted-dark);
}
```

## Gradients

```css
.yis-gradient-orange {
  background: linear-gradient(135deg, var(--yis-orange) 0%, var(--yis-orange-light) 100%);
}

.yis-gradient-navy {
  background: linear-gradient(180deg, var(--yis-navy) 0%, var(--yis-charcoal) 100%);
}

.yis-gradient-olive {
  background: linear-gradient(135deg, var(--yis-olive) 0%, var(--yis-olive-light) 100%);
}

.yis-glow-orange {
  background: radial-gradient(ellipse at center, rgba(252,76,2,0.15) 0%, transparent 70%);
}
```

## Utility Classes

```css
.yis-text-center { text-align: center; }
.yis-text-muted { color: var(--yis-text-muted); }
.yis-uppercase { text-transform: uppercase; }
.yis-tracking-wide { letter-spacing: var(--yis-tracking-wide); }
.yis-mt-sm { margin-top: var(--yis-space-sm); }
.yis-mt-md { margin-top: var(--yis-space-md); }
.yis-mt-lg { margin-top: var(--yis-space-lg); }
.yis-mt-xl { margin-top: var(--yis-space-xl); }
.yis-mt-2xl { margin-top: var(--yis-space-2xl); }
.yis-mb-sm { margin-bottom: var(--yis-space-sm); }
.yis-mb-md { margin-bottom: var(--yis-space-md); }
.yis-mb-lg { margin-bottom: var(--yis-space-lg); }
.yis-mb-xl { margin-bottom: var(--yis-space-xl); }
```
