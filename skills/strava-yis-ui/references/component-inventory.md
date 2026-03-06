# Strava Year in Sport UI — Component Inventory

## Navigation

```html
<nav class="yis-nav">
  <div class="yis-container">
    <div class="yis-nav__inner">
      <a href="/" class="yis-nav__logo">enigma</a>
      <div class="yis-nav__links">
        <a href="#" class="yis-nav__link">Solutions</a>
        <a href="#" class="yis-nav__link">Products</a>
        <a href="#" class="yis-nav__link">Resources</a>
        <a href="#" class="yis-nav__link">Pricing</a>
      </div>
      <a href="#" class="yis-btn yis-btn--sm">Get Started</a>
    </div>
  </div>
</nav>
```

```css
.yis-nav {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 100;
  padding: 16px 0;
  background: rgba(29,29,59,0.95);
  backdrop-filter: blur(12px);
}

.yis-nav__inner {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.yis-nav__logo {
  font-size: 20px;
  font-weight: 800;
  color: var(--yis-white);
  text-decoration: none;
  letter-spacing: -0.01em;
}

.yis-nav__links {
  display: flex;
  gap: 32px;
}

.yis-nav__link {
  font-size: 14px;
  font-weight: 600;
  color: rgba(255,255,255,0.8);
  text-decoration: none;
  text-transform: uppercase;
  letter-spacing: 0.04em;
}

.yis-nav__link:hover { color: var(--yis-white); }

@media (max-width: 768px) {
  .yis-nav__links { display: none; }
}
```

---

## Hero Stat Section

```html
<section class="yis-panel yis-panel--navy yis-hero">
  <div class="yis-container" style="text-align:center">
    <p class="yis-label">TRUSTED BY LEADING ENTERPRISES</p>
    <div class="yis-stat-hero" data-count-to="24000000">24M+</div>
    <p class="yis-h2" style="margin-top:16px">U.S. businesses resolved</p>
    <p class="yis-body-lg" style="margin-top:24px;max-width:560px;margin-left:auto;margin-right:auto;color:var(--yis-text-muted)">
      Enigma provides foundational data on businesses, built on unparalleled entity resolution.
    </p>
  </div>
</section>
```

```css
.yis-hero {
  padding: 160px 0 128px;
  position: relative;
  overflow: hidden;
}

/* Optional decorative glow */
.yis-hero::after {
  content: '';
  position: absolute;
  top: 50%;
  left: 50%;
  width: 600px;
  height: 600px;
  transform: translate(-50%, -50%);
  background: radial-gradient(ellipse, rgba(252,76,2,0.1) 0%, transparent 70%);
  pointer-events: none;
}
```

---

## Stat Card

```html
<div class="yis-stat-card">
  <span class="yis-stat-card__number">97%</span>
  <span class="yis-stat-card__label">MERCHANT MATCH RATE</span>
</div>
```

```css
.yis-stat-card {
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
  padding: 32px 24px;
  border-radius: 24px;
  background: rgba(255,255,255,0.06);
}

.yis-stat-card__number {
  font-family: var(--yis-font-display);
  font-size: clamp(36px, 5vw, 64px);
  font-weight: 800;
  line-height: 1;
  letter-spacing: -0.02em;
}

.yis-stat-card__label {
  font-size: 12px;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.08em;
  margin-top: 12px;
  color: rgba(255,255,255,0.6);
}

/* On light backgrounds */
.yis-panel--light .yis-stat-card {
  background: var(--yis-white);
  box-shadow: var(--yis-shadow-sm);
}

.yis-panel--light .yis-stat-card__label {
  color: var(--yis-text-muted-dark);
}
```

### Stat Card Grid
```css
.yis-stat-grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 24px;
}

@media (max-width: 768px) {
  .yis-stat-grid { grid-template-columns: repeat(2, 1fr); }
}

@media (max-width: 480px) {
  .yis-stat-grid { grid-template-columns: 1fr; }
}
```

---

## Progress Ring

```html
<div class="yis-ring" style="--ring-size:160px;--ring-value:97">
  <svg viewBox="0 0 100 100">
    <circle class="yis-ring__track" cx="50" cy="50" r="44" />
    <circle class="yis-ring__fill" cx="50" cy="50" r="44"
            style="stroke-dasharray:276.46;stroke-dashoffset:calc(276.46 * (1 - 0.97))" />
  </svg>
  <div class="yis-ring__label">
    <span class="yis-ring__number">97%</span>
    <span class="yis-ring__text">Match Rate</span>
  </div>
</div>
```

```css
.yis-ring {
  position: relative;
  width: var(--ring-size, 160px);
  height: var(--ring-size, 160px);
}

.yis-ring svg {
  width: 100%;
  height: 100%;
  transform: rotate(-90deg);
}

.yis-ring__track {
  fill: none;
  stroke: rgba(255,255,255,0.1);
  stroke-width: 6;
}

.yis-ring__fill {
  fill: none;
  stroke: var(--yis-orange);
  stroke-width: 6;
  stroke-linecap: round;
  transition: stroke-dashoffset 1.2s var(--yis-ease);
}

.yis-ring__label {
  position: absolute;
  inset: 0;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.yis-ring__number {
  font-size: 32px;
  font-weight: 800;
  line-height: 1;
}

.yis-ring__text {
  font-size: 11px;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.06em;
  margin-top: 4px;
  opacity: 0.6;
}
```

---

## Color Strip Divider

```html
<div class="yis-strips">
  <div style="background:var(--yis-orange)"></div>
  <div style="background:var(--yis-olive)"></div>
  <div style="background:var(--yis-teal)"></div>
  <div style="background:var(--yis-gold)"></div>
</div>
```

```css
.yis-strips {
  display: flex;
  flex-direction: column;
  gap: 3px;
}

.yis-strips div {
  height: 6px;
  width: 100%;
}
```

---

## Data Bar (Horizontal)

```html
<div class="yis-bar">
  <div class="yis-bar__header">
    <span class="yis-bar__label">With Enigma</span>
    <span class="yis-bar__value">4.2%</span>
  </div>
  <div class="yis-bar__track">
    <div class="yis-bar__fill" style="width:84%"></div>
  </div>
</div>
```

```css
.yis-bar {
  margin-bottom: 24px;
}

.yis-bar__header {
  display: flex;
  justify-content: space-between;
  align-items: baseline;
  margin-bottom: 8px;
}

.yis-bar__label {
  font-size: 14px;
  font-weight: 600;
}

.yis-bar__value {
  font-size: 20px;
  font-weight: 800;
}

.yis-bar__track {
  height: 12px;
  border-radius: 6px;
  background: rgba(255,255,255,0.1);
  overflow: hidden;
}

.yis-bar__fill {
  height: 100%;
  border-radius: 6px;
  background: linear-gradient(90deg, var(--yis-orange), var(--yis-orange-light));
  transition: width 1s var(--yis-ease);
}

/* On light backgrounds */
.yis-panel--light .yis-bar__track {
  background: var(--yis-light-gray);
}
```

---

## Buttons

```html
<a href="#" class="yis-btn">Get Started</a>
<a href="#" class="yis-btn yis-btn--outline">Learn More</a>
<a href="#" class="yis-btn yis-btn--ghost">View Report →</a>
```

```css
.yis-btn {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  font-family: var(--yis-font-body);
  font-size: 14px;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.04em;
  padding: 14px 32px;
  border-radius: 100px;
  border: none;
  background: var(--yis-orange);
  color: var(--yis-white);
  text-decoration: none;
  cursor: pointer;
  transition: all 300ms var(--yis-ease);
}

.yis-btn:hover {
  background: var(--yis-orange-dark);
  color: var(--yis-white);
  transform: translateY(-1px);
  box-shadow: 0 4px 16px rgba(252,76,2,0.3);
}

.yis-btn--outline {
  background: transparent;
  border: 2px solid var(--yis-white);
  color: var(--yis-white);
}

.yis-btn--outline:hover {
  background: var(--yis-white);
  color: var(--yis-navy);
  transform: translateY(-1px);
  box-shadow: none;
}

.yis-btn--ghost {
  background: transparent;
  color: var(--yis-orange);
  padding: 8px 0;
  border-radius: 0;
  font-weight: 600;
}

.yis-btn--ghost:hover {
  color: var(--yis-orange-dark);
  transform: none;
  box-shadow: none;
}

.yis-btn--sm {
  padding: 10px 20px;
  font-size: 13px;
}
```

---

## Feature Card

```html
<div class="yis-feature-card">
  <div class="yis-feature-card__icon">📊</div>
  <h3 class="yis-h3" style="margin-bottom:8px">Lead Generation</h3>
  <p>Build prospect databases based on real revenues, growth signals, and more.</p>
</div>
```

```css
.yis-feature-card {
  padding: 32px;
  border-radius: 24px;
  background: rgba(255,255,255,0.06);
  transition: all 300ms var(--yis-ease);
}

.yis-feature-card:hover {
  background: rgba(255,255,255,0.1);
  transform: translateY(-4px);
}

.yis-feature-card__icon {
  font-size: 32px;
  margin-bottom: 16px;
}

/* On light backgrounds */
.yis-panel--light .yis-feature-card {
  background: var(--yis-white);
  box-shadow: var(--yis-shadow-sm);
}

.yis-panel--light .yis-feature-card:hover {
  box-shadow: var(--yis-shadow-md);
}
```

---

## Dot Pattern Background

```css
.yis-dots {
  position: relative;
}

.yis-dots::before {
  content: '';
  position: absolute;
  inset: 0;
  background-image: radial-gradient(circle, rgba(255,255,255,0.06) 1px, transparent 1px);
  background-size: 28px 28px;
  pointer-events: none;
}
```

---

## Quote Block

```html
<blockquote class="yis-quote">
  <div class="yis-quote__mark">"</div>
  <p class="yis-quote__text">
    Enigma's data helps our team identify the top prospects that match our ideal customer profile.
  </p>
  <cite class="yis-quote__cite">ROB HEWITT — COMMERCIAL DIRECTOR, PHOREST</cite>
</blockquote>
```

```css
.yis-quote {
  position: relative;
  padding: 48px;
  border-radius: 24px;
  background: rgba(255,255,255,0.06);
}

.yis-quote__mark {
  font-size: 72px;
  font-weight: 900;
  line-height: 1;
  color: var(--yis-orange);
  margin-bottom: 16px;
}

.yis-quote__text {
  font-size: clamp(20px, 2.5vw, 28px);
  font-weight: 500;
  line-height: 1.4;
  margin-bottom: 24px;
}

.yis-quote__cite {
  font-size: 12px;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.06em;
  font-style: normal;
  opacity: 0.6;
}
```

---

## Footer

```html
<footer class="yis-footer">
  <div class="yis-container">
    <div class="yis-footer__grid">
      <div>
        <p class="yis-footer__brand">enigma</p>
        <p class="yis-footer__tagline">The trusted source for business data.</p>
      </div>
      <div>
        <h4 class="yis-footer__heading">Products</h4>
        <a href="#" class="yis-footer__link">Data Solutions</a>
        <a href="#" class="yis-footer__link">API Platform</a>
      </div>
    </div>
  </div>
</footer>
```

```css
.yis-footer {
  background: linear-gradient(180deg, var(--yis-charcoal), var(--yis-dark));
  color: var(--yis-text-light);
  padding: 80px 0 48px;
}

.yis-footer__grid {
  display: grid;
  grid-template-columns: 2.5fr 1fr 1fr 1fr;
  gap: 32px;
}

.yis-footer__brand {
  font-size: 20px;
  font-weight: 800;
  margin-bottom: 8px;
}

.yis-footer__tagline {
  font-size: 14px;
  color: rgba(255,255,255,0.5);
}

.yis-footer__heading {
  font-size: 11px;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.08em;
  color: rgba(255,255,255,0.4);
  margin-bottom: 16px;
}

.yis-footer__link {
  display: block;
  font-size: 14px;
  color: rgba(255,255,255,0.7);
  text-decoration: none;
  padding: 4px 0;
}

.yis-footer__link:hover { color: var(--yis-white); }

@media (max-width: 768px) {
  .yis-footer__grid { grid-template-columns: 1fr 1fr; }
}
```
