# Nothing Tech UI — Component Inventory

## Navigation

```html
<nav class="nt-nav">
  <div class="nt-nav__inner nt-container">
    <a href="/" class="nt-nav__logo">
      <!-- Nothing dot logo or wordmark -->
      <svg width="80" height="20" viewBox="0 0 80 20">
        <text x="0" y="16" fill="currentColor"
              font-family="var(--nt-font)" font-weight="500"
              font-size="16" letter-spacing="-0.02em">nothing</text>
      </svg>
    </a>

    <div class="nt-nav__links">
      <a href="#" class="nt-nav__link">Phones</a>
      <a href="#" class="nt-nav__link">Audio</a>
      <a href="#" class="nt-nav__link">Accessories</a>
    </div>

    <div class="nt-nav__actions">
      <button class="nt-nav__icon" aria-label="Search">
        <svg width="20" height="20" viewBox="0 0 20 20" fill="none" stroke="currentColor" stroke-width="1.5">
          <circle cx="9" cy="9" r="6"/><path d="M13.5 13.5L18 18"/>
        </svg>
      </button>
      <button class="nt-nav__icon" aria-label="Cart">
        <svg width="20" height="20" viewBox="0 0 20 20" fill="none" stroke="currentColor" stroke-width="1.5">
          <path d="M4 4h1.5l2 10h8l2-7H6"/>
        </svg>
      </button>
    </div>
  </div>
</nav>
```

```css
.nt-nav {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 100;
  background: rgba(255, 255, 255, 0.95);
  backdrop-filter: blur(12px);
  border-bottom: 1px solid var(--nt-border);
  transition: background var(--nt-duration-normal) ease;
}

.nt-nav__inner {
  display: flex;
  align-items: center;
  justify-content: space-between;
  height: 56px;
}

.nt-nav__links {
  display: flex;
  gap: var(--nt-space-xl);
}

.nt-nav__link {
  font-size: 14px;
  font-weight: 500;
  text-transform: uppercase;
  letter-spacing: 0.05em;
  color: var(--nt-text-primary);
  position: relative;
}

.nt-nav__link::after {
  content: '';
  position: absolute;
  bottom: -2px;
  left: 0;
  width: 0;
  height: 1px;
  background: var(--nt-text-primary);
  transition: width var(--nt-duration-fast) ease;
}

.nt-nav__link:hover::after { width: 100%; }

.nt-nav__actions { display: flex; gap: var(--nt-space-md); }

.nt-nav__icon {
  background: none;
  border: none;
  cursor: pointer;
  color: var(--nt-text-primary);
  padding: var(--nt-space-xs);
}

/* Dark variant */
.nt-nav--dark {
  background: rgba(0, 0, 0, 0.9);
  border-bottom-color: var(--nt-border-inverse);
}
.nt-nav--dark .nt-nav__link,
.nt-nav--dark .nt-nav__icon { color: var(--nt-text-inverse); }
.nt-nav--dark .nt-nav__link::after { background: var(--nt-text-inverse); }
```

---

## Hero Section

```html
<section class="nt-hero">
  <div class="nt-hero__media">
    <!-- Full-bleed product image or video -->
    <img src="product-hero.jpg" alt="Product" class="nt-hero__img" />
  </div>
  <div class="nt-hero__content nt-container">
    <h1 class="nt-hero__title">it's metal now.</h1>
    <p class="nt-hero__subtitle">Phone (3a). starting at $349.</p>
    <div class="nt-hero__actions">
      <a href="#" class="nt-btn nt-btn-primary">Discover</a>
      <a href="#" class="nt-btn nt-btn-secondary">Pre-order</a>
    </div>
  </div>
  <div class="nt-hero__scroll">
    <div class="nt-hero__scroll-line"></div>
  </div>
</section>
```

```css
.nt-hero {
  position: relative;
  height: 100vh;
  min-height: 600px;
  display: flex;
  align-items: flex-end;
  overflow: hidden;
  background: var(--nt-bg-inverse);
}

.nt-hero__media {
  position: absolute;
  inset: 0;
}

.nt-hero__img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  object-position: center;
}

.nt-hero__content {
  position: relative;
  z-index: 2;
  padding-bottom: var(--nt-space-4xl);
  color: var(--nt-text-inverse);
}

.nt-hero__title {
  font-size: var(--nt-text-hero);
  font-weight: 500;
  letter-spacing: -0.02em;
  line-height: var(--nt-leading-tight);
  margin-bottom: var(--nt-space-md);
}

.nt-hero__subtitle {
  font-size: var(--nt-text-body-lg);
  color: var(--nt-text-inverse-muted);
  margin-bottom: var(--nt-space-xl);
}

.nt-hero__actions { display: flex; gap: var(--nt-space-md); }

.nt-hero__scroll {
  position: absolute;
  bottom: var(--nt-space-xl);
  left: 50%;
  transform: translateX(-50%);
}

.nt-hero__scroll-line {
  width: 1px;
  height: 40px;
  background: linear-gradient(to bottom, rgba(255,255,255,0.6), transparent);
  animation: scrollPulse 2s ease-in-out infinite;
}

@keyframes scrollPulse {
  0%, 100% { opacity: 0.4; transform: scaleY(0.6); }
  50% { opacity: 1; transform: scaleY(1); }
}
```

---

## Buttons

```html
<button class="nt-btn nt-btn-primary">Discover</button>
<button class="nt-btn nt-btn-secondary">Learn more</button>
<button class="nt-btn nt-btn-ghost">View all</button>
<button class="nt-btn nt-btn-primary" disabled>Sold out</button>
```

```css
.nt-btn {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  font-family: var(--nt-font);
  font-size: 14px;
  font-weight: 500;
  text-transform: uppercase;
  letter-spacing: 0.08em;
  padding: 14px 32px;
  border: none;
  border-radius: var(--nt-radius-none);
  cursor: pointer;
  transition: all var(--nt-duration-fast) ease;
  text-decoration: none;
}

.nt-btn-primary {
  background: var(--nt-text-primary);
  color: var(--nt-bg-primary);
}
.nt-btn-primary:hover { background: #333; }

.nt-btn-secondary {
  background: transparent;
  color: var(--nt-text-primary);
  border: 1px solid var(--nt-text-primary);
}
.nt-btn-secondary:hover { background: var(--nt-bg-secondary); }

.nt-btn-ghost {
  background: transparent;
  color: var(--nt-text-primary);
  padding: 8px 0;
  text-decoration: none;
}
.nt-btn-ghost:hover { text-decoration: underline; }

.nt-btn:disabled,
.nt-btn[disabled] {
  background: var(--nt-border-strong);
  color: var(--nt-text-tertiary);
  cursor: not-allowed;
}
```

---

## Product Card

```html
<article class="nt-product-card">
  <div class="nt-product-card__image">
    <img src="phone.jpg" alt="Phone (3a)" loading="lazy" />
  </div>
  <div class="nt-product-card__body">
    <h3 class="nt-product-card__title">Phone (3a)</h3>
    <p class="nt-product-card__subtitle">Black · 128GB</p>
    <div class="nt-product-card__variants">
      <span class="nt-color-dot" style="background:#000"></span>
      <span class="nt-color-dot" style="background:#FFF; border:1px solid #E5E5E5"></span>
      <span class="nt-color-dot" style="background:#4169E1"></span>
    </div>
    <span class="nt-product-card__price">$349</span>
  </div>
</article>
```

```css
.nt-product-card {
  display: flex;
  flex-direction: column;
  cursor: pointer;
  transition: transform var(--nt-duration-normal) var(--nt-ease-out);
}
.nt-product-card:hover { transform: translateY(-2px); }

.nt-product-card__image {
  aspect-ratio: 1 / 1;
  background: var(--nt-bg-secondary);
  overflow: hidden;
  margin-bottom: var(--nt-space-md);
}
.nt-product-card__image img {
  width: 100%;
  height: 100%;
  object-fit: contain;
  transition: transform 400ms var(--nt-ease-out);
}
.nt-product-card:hover .nt-product-card__image img {
  transform: scale(1.03);
}

.nt-product-card__title {
  font-size: 16px;
  font-weight: 500;
  margin-bottom: var(--nt-space-xs);
}

.nt-product-card__subtitle {
  font-size: 14px;
  color: var(--nt-text-secondary);
  margin-bottom: var(--nt-space-sm);
}

.nt-product-card__variants {
  display: flex;
  gap: 6px;
  margin-bottom: var(--nt-space-sm);
}

.nt-color-dot {
  width: 16px;
  height: 16px;
  border-radius: var(--nt-radius-full);
  display: inline-block;
}

.nt-product-card__price {
  font-size: 16px;
  font-weight: 500;
}
```

---

## Spec Card

```html
<div class="nt-spec-card">
  <div class="nt-spec-card__icon">
    <svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5">
      <rect x="6" y="2" width="12" height="20" rx="1"/>
      <line x1="9" y1="18" x2="15" y2="18"/>
    </svg>
  </div>
  <span class="nt-spec-card__value">6.7"</span>
  <span class="nt-spec-card__label">AMOLED display</span>
</div>
```

```css
.nt-spec-card {
  background: var(--nt-bg-secondary);
  padding: var(--nt-space-xl);
  display: flex;
  flex-direction: column;
  gap: var(--nt-space-sm);
}

.nt-spec-card__icon {
  color: var(--nt-text-secondary);
  margin-bottom: var(--nt-space-sm);
}

.nt-spec-card__value {
  font-size: clamp(2rem, 3vw, 2.5rem);
  font-weight: 500;
  letter-spacing: -0.02em;
  line-height: 1;
}

.nt-spec-card__label {
  font-size: 12px;
  text-transform: uppercase;
  letter-spacing: 0.05em;
  color: var(--nt-text-secondary);
}

/* Dark variant */
.nt-dark .nt-spec-card {
  background: var(--nt-bg-inverse-soft);
}
.nt-dark .nt-spec-card__label {
  color: var(--nt-text-inverse-muted);
}
```

---

## Split Section (Image + Text)

```html
<section class="nt-split">
  <div class="nt-split__media">
    <img src="feature.jpg" alt="Feature" loading="lazy" />
  </div>
  <div class="nt-split__content">
    <span class="nt-split__eyebrow">Camera</span>
    <h2 class="nt-split__title">see more, do more.</h2>
    <p class="nt-split__body">
      50 MP dual camera with advanced AI processing.
      Every shot, perfectly balanced.
    </p>
    <a href="#" class="nt-btn nt-btn-ghost">Learn more →</a>
  </div>
</section>
```

```css
.nt-split {
  display: grid;
  grid-template-columns: 1fr 1fr;
  min-height: 80vh;
}

@media (max-width: 768px) {
  .nt-split { grid-template-columns: 1fr; }
}

.nt-split__media {
  overflow: hidden;
}
.nt-split__media img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.nt-split__content {
  display: flex;
  flex-direction: column;
  justify-content: center;
  padding: var(--nt-space-4xl) var(--nt-space-3xl);
}

.nt-split__eyebrow {
  font-size: 12px;
  text-transform: uppercase;
  letter-spacing: 0.08em;
  color: var(--nt-text-tertiary);
  margin-bottom: var(--nt-space-lg);
}

.nt-split__title {
  font-size: var(--nt-text-h1);
  font-weight: 500;
  letter-spacing: -0.02em;
  line-height: var(--nt-leading-tight);
  margin-bottom: var(--nt-space-lg);
}

.nt-split__body {
  font-size: var(--nt-text-body-lg);
  color: var(--nt-text-secondary);
  line-height: var(--nt-leading-normal);
  margin-bottom: var(--nt-space-xl);
  max-width: 440px;
}

/* Reverse layout (image right) */
.nt-split--reverse .nt-split__media { order: 2; }
.nt-split--reverse .nt-split__content { order: 1; }
```

---

## Centered Section

```html
<section class="nt-centered nt-section">
  <div class="nt-container nt-text-center">
    <span class="nt-centered__eyebrow">Design</span>
    <h2 class="nt-centered__title">less is beautiful.</h2>
    <p class="nt-centered__body">
      Stripped back to what matters.
      Nothing extra, nothing missing.
    </p>
  </div>
</section>
```

```css
.nt-centered__eyebrow {
  display: block;
  font-size: 12px;
  text-transform: uppercase;
  letter-spacing: 0.08em;
  color: var(--nt-text-tertiary);
  margin-bottom: var(--nt-space-lg);
}

.nt-centered__title {
  font-size: var(--nt-text-h1);
  font-weight: 500;
  letter-spacing: -0.02em;
  line-height: var(--nt-leading-tight);
  margin-bottom: var(--nt-space-lg);
}

.nt-centered__body {
  font-size: var(--nt-text-body-lg);
  color: var(--nt-text-secondary);
  line-height: var(--nt-leading-normal);
  max-width: 560px;
  margin: 0 auto;
}
```

---

## Spec Grid

```html
<section class="nt-dark nt-section">
  <div class="nt-container">
    <h2 class="nt-centered__title" style="text-align:center; margin-bottom:48px">
      the specs.
    </h2>
    <div class="nt-spec-grid">
      <div class="nt-spec-card">
        <span class="nt-spec-card__value">50 MP</span>
        <span class="nt-spec-card__label">Dual camera</span>
      </div>
      <div class="nt-spec-card">
        <span class="nt-spec-card__value">5000 mAh</span>
        <span class="nt-spec-card__label">2-day battery</span>
      </div>
      <div class="nt-spec-card">
        <span class="nt-spec-card__value">6.7"</span>
        <span class="nt-spec-card__label">AMOLED display</span>
      </div>
      <div class="nt-spec-card">
        <span class="nt-spec-card__value">120 Hz</span>
        <span class="nt-spec-card__label">Refresh rate</span>
      </div>
    </div>
  </div>
</section>
```

```css
.nt-spec-grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 1px;
  background: var(--nt-border-inverse);
}

.nt-spec-grid .nt-spec-card {
  text-align: center;
  align-items: center;
}

@media (max-width: 768px) {
  .nt-spec-grid { grid-template-columns: repeat(2, 1fr); }
}
```

---

## Product Strip (Horizontal Scroll)

```html
<section class="nt-section">
  <div class="nt-container">
    <div class="nt-flex-between" style="margin-bottom: 32px">
      <h2 style="font-size: var(--nt-text-h2); font-weight: 500">explore.</h2>
      <a href="#" class="nt-btn nt-btn-ghost">View all →</a>
    </div>
  </div>
  <div class="nt-product-strip">
    <article class="nt-product-card"><!-- ... --></article>
    <article class="nt-product-card"><!-- ... --></article>
    <article class="nt-product-card"><!-- ... --></article>
    <article class="nt-product-card"><!-- ... --></article>
  </div>
</section>
```

```css
.nt-product-strip {
  display: flex;
  gap: var(--nt-gutter);
  overflow-x: auto;
  scroll-snap-type: x mandatory;
  padding: 0 var(--nt-margin-desktop);
  -ms-overflow-style: none;
  scrollbar-width: none;
}
.nt-product-strip::-webkit-scrollbar { display: none; }

.nt-product-strip .nt-product-card {
  flex: 0 0 280px;
  scroll-snap-align: start;
}

@media (max-width: 640px) {
  .nt-product-strip { padding: 0 var(--nt-margin-mobile); }
  .nt-product-strip .nt-product-card { flex: 0 0 240px; }
}
```

---

## Comparison Table

```html
<div class="nt-compare">
  <table class="nt-compare__table">
    <thead>
      <tr>
        <th></th>
        <th>Phone (3a)</th>
        <th>Phone (3a) Pro</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td class="nt-compare__label">Display</td>
        <td>6.7" AMOLED</td>
        <td>6.7" LTPO AMOLED</td>
      </tr>
      <tr>
        <td class="nt-compare__label">Camera</td>
        <td>50 MP Dual</td>
        <td>50 MP Triple</td>
      </tr>
      <tr>
        <td class="nt-compare__label">Battery</td>
        <td>5000 mAh</td>
        <td>5100 mAh</td>
      </tr>
      <tr>
        <td class="nt-compare__label">Price</td>
        <td>$349</td>
        <td>$449</td>
      </tr>
    </tbody>
  </table>
</div>
```

```css
.nt-compare__table {
  width: 100%;
  border-collapse: collapse;
  font-size: 14px;
}

.nt-compare__table th {
  font-weight: 500;
  text-transform: uppercase;
  letter-spacing: 0.05em;
  font-size: 12px;
  padding: var(--nt-space-md) var(--nt-space-lg);
  text-align: left;
  border-bottom: 1px solid var(--nt-border);
}

.nt-compare__table td {
  padding: var(--nt-space-md) var(--nt-space-lg);
  border-bottom: 1px solid var(--nt-divider);
}

.nt-compare__label {
  font-weight: 500;
  color: var(--nt-text-secondary);
  text-transform: uppercase;
  letter-spacing: 0.05em;
  font-size: 12px;
}
```

---

## Newsletter Section

```html
<section class="nt-dark nt-section-sm">
  <div class="nt-container nt-text-center">
    <h3 style="font-size: var(--nt-text-h3); font-weight:500; margin-bottom:16px">
      stay in the loop.
    </h3>
    <p style="font-size:14px; color:var(--nt-text-inverse-muted); margin-bottom:24px">
      Be the first to know about new products and updates.
    </p>
    <form class="nt-newsletter">
      <input type="email" placeholder="Email address" class="nt-newsletter__input" />
      <button type="submit" class="nt-btn nt-btn-primary" style="background:#FFF; color:#000">
        Subscribe
      </button>
    </form>
  </div>
</section>
```

```css
.nt-newsletter {
  display: flex;
  max-width: 420px;
  margin: 0 auto;
  gap: 0;
}

.nt-newsletter__input {
  flex: 1;
  font-family: var(--nt-font);
  font-size: 14px;
  padding: 14px 16px;
  border: 1px solid var(--nt-border-inverse);
  border-right: none;
  background: transparent;
  color: var(--nt-text-inverse);
  outline: none;
  border-radius: 0;
}

.nt-newsletter__input::placeholder {
  color: var(--nt-text-inverse-muted);
}

.nt-newsletter__input:focus {
  border-color: var(--nt-text-inverse);
}
```

---

## Footer

```html
<footer class="nt-footer">
  <div class="nt-container">
    <div class="nt-footer__grid">
      <div class="nt-footer__col">
        <h4 class="nt-footer__heading">Products</h4>
        <a href="#" class="nt-footer__link">Phones</a>
        <a href="#" class="nt-footer__link">Audio</a>
        <a href="#" class="nt-footer__link">Accessories</a>
      </div>
      <div class="nt-footer__col">
        <h4 class="nt-footer__heading">Company</h4>
        <a href="#" class="nt-footer__link">About</a>
        <a href="#" class="nt-footer__link">Community</a>
        <a href="#" class="nt-footer__link">Careers</a>
      </div>
      <div class="nt-footer__col">
        <h4 class="nt-footer__heading">Support</h4>
        <a href="#" class="nt-footer__link">Contact</a>
        <a href="#" class="nt-footer__link">FAQ</a>
        <a href="#" class="nt-footer__link">Repairs</a>
      </div>
    </div>
    <div class="nt-footer__bottom">
      <span class="nt-footer__copy">&copy; 2026 Nothing Technology Limited</span>
    </div>
  </div>
</footer>
```

```css
.nt-footer {
  background: var(--nt-bg-inverse);
  color: var(--nt-text-inverse);
  padding: var(--nt-space-3xl) 0 var(--nt-space-xl);
}

.nt-footer__grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: var(--nt-space-xl);
  margin-bottom: var(--nt-space-3xl);
}

@media (max-width: 640px) {
  .nt-footer__grid { grid-template-columns: 1fr; gap: var(--nt-space-xl); }
}

.nt-footer__heading {
  font-size: 12px;
  text-transform: uppercase;
  letter-spacing: 0.08em;
  color: var(--nt-text-inverse-muted);
  margin-bottom: var(--nt-space-md);
  font-weight: 500;
}

.nt-footer__link {
  display: block;
  font-size: 14px;
  color: var(--nt-text-inverse);
  padding: 6px 0;
  transition: opacity var(--nt-duration-fast) ease;
}
.nt-footer__link:hover { opacity: 0.7; }

.nt-footer__bottom {
  border-top: 1px solid var(--nt-border-inverse);
  padding-top: var(--nt-space-lg);
}

.nt-footer__copy {
  font-size: 12px;
  color: var(--nt-text-inverse-muted);
}
```

---

## Dot-Matrix Loader

```html
<div class="nt-dot-loader">
  <span></span><span></span><span></span>
  <span></span><span></span><span></span>
  <span></span><span></span><span></span>
</div>
```

```css
.nt-dot-loader {
  display: grid;
  grid-template-columns: repeat(3, 8px);
  gap: 6px;
}

.nt-dot-loader span {
  width: 8px;
  height: 8px;
  border-radius: 50%;
  background: var(--nt-dot);
  animation: dotPulse 1.4s ease-in-out infinite;
}

.nt-dot-loader span:nth-child(1) { animation-delay: 0s; }
.nt-dot-loader span:nth-child(2) { animation-delay: 0.1s; }
.nt-dot-loader span:nth-child(3) { animation-delay: 0.2s; }
.nt-dot-loader span:nth-child(4) { animation-delay: 0.3s; }
.nt-dot-loader span:nth-child(5) { animation-delay: 0.4s; }
.nt-dot-loader span:nth-child(6) { animation-delay: 0.5s; }
.nt-dot-loader span:nth-child(7) { animation-delay: 0.6s; }
.nt-dot-loader span:nth-child(8) { animation-delay: 0.7s; }
.nt-dot-loader span:nth-child(9) { animation-delay: 0.8s; }

@keyframes dotPulse {
  0%, 60%, 100% { background: var(--nt-dot); }
  30% { background: var(--nt-dot-active); }
}
```

---

## Scroll Indicator

```html
<div class="nt-scroll-indicator">
  <div class="nt-scroll-indicator__bar"></div>
</div>
```

```css
.nt-scroll-indicator {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  height: 2px;
  z-index: 200;
  background: transparent;
}

.nt-scroll-indicator__bar {
  height: 100%;
  background: var(--nt-text-primary);
  width: 0%;
  transition: width 100ms linear;
}
```
