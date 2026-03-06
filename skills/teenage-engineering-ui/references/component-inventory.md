# Teenage Engineering UI — Component Inventory

## Navigation

```html
<nav class="te-nav">
  <div class="te-container">
    <div class="te-nav__inner">
      <a href="/" class="te-nav__logo">teenage engineering</a>
      <div class="te-nav__links">
        <a href="#" class="te-nav__link">products</a>
        <a href="#" class="te-nav__link">store</a>
        <a href="#" class="te-nav__link">support</a>
        <a href="#" class="te-nav__link">about</a>
        <a href="#" class="te-nav__link te-nav__cart">in cart (0)</a>
      </div>
    </div>
  </div>
</nav>
```

```css
.te-nav {
  padding: var(--te-space-md) 0;
}

.te-nav__inner {
  display: flex;
  align-items: baseline;
  justify-content: space-between;
}

.te-nav__logo {
  font-size: var(--te-text-sm);
  font-weight: var(--te-weight-light);
  text-decoration: none;
  color: var(--te-text);
  letter-spacing: 0.02em;
}

.te-nav__links {
  display: flex;
  gap: var(--te-space-lg);
}

.te-nav__link {
  font-size: var(--te-text-sm);
  font-weight: var(--te-weight-light);
  color: var(--te-text);
  text-decoration: none;
}

.te-nav__link:hover { opacity: 0.6; }

@media (max-width: 640px) {
  .te-nav__links { gap: var(--te-space-md); }
}
```

---

## Product Hero

```html
<section class="te-hero">
  <div class="te-container">
    <div class="te-hero__image">
      <img src="product.webp" alt="EP–133 K.O.II" />
    </div>
    <div class="te-hero__info">
      <h1 class="te-hero__title">EP–133 K.O.II</h1>
      <p class="te-hero__tagline">sampler. sequencer. drum machine.</p>
      <p class="te-hero__price">$329</p>
      <a href="#" class="te-hero__cta">buy now</a>
    </div>
  </div>
</section>
```

```css
.te-hero {
  padding: var(--te-space-xl) 0;
}

.te-hero__image {
  margin-bottom: var(--te-space-lg);
}

.te-hero__image img {
  width: 100%;
  height: auto;
  object-fit: contain;
}

.te-hero__title {
  font-size: var(--te-text-2xl);
  font-weight: var(--te-weight-thin);
  line-height: var(--te-leading-display);
  letter-spacing: -0.01em;
  margin-bottom: var(--te-space-xs);
}

.te-hero__tagline {
  font-size: var(--te-text-base);
  font-weight: var(--te-weight-light);
  color: var(--te-text-secondary);
  margin-bottom: var(--te-space-md);
}

.te-hero__price {
  font-size: var(--te-text-lg);
  font-weight: var(--te-weight-thin);
  margin-bottom: var(--te-space-md);
}

.te-hero__cta {
  font-size: var(--te-text-sm);
  font-weight: var(--te-weight-light);
  color: var(--te-text);
  text-decoration: underline;
}

.te-hero__cta:hover { opacity: 0.6; }
```

---

## Product Card

```html
<article class="te-product-card">
  <div class="te-product-card__image">
    <img src="product-thumb.webp" alt="EP–133" />
  </div>
  <div class="te-product-card__info">
    <span class="te-product-card__name">EP–133 K.O.II</span>
    <a href="#" class="te-product-card__action">add to cart</a>
  </div>
</article>
```

```css
.te-product-card {
  display: flex;
  flex-direction: column;
}

.te-product-card__image {
  margin-bottom: var(--te-space-sm);
}

.te-product-card__image img {
  width: 100%;
  aspect-ratio: 1 / 1;
  object-fit: contain;
}

.te-product-card__name {
  font-size: var(--te-text-sm);
  font-weight: var(--te-weight-light);
  display: block;
  margin-bottom: 2px;
}

.te-product-card__action {
  font-size: var(--te-text-xs);
  font-weight: var(--te-weight-light);
  color: var(--te-text-secondary);
  text-decoration: underline;
}

.te-product-card__action:hover { opacity: 0.6; }
```

### Product Grid
```css
.te-product-grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: var(--te-gutter);
}

@media (max-width: 768px) {
  .te-product-grid { grid-template-columns: repeat(2, 1fr); }
}

@media (max-width: 480px) {
  .te-product-grid { grid-template-columns: 1fr; }
}
```

---

## Feature Section

```html
<section class="te-features">
  <div class="te-container">
    <h2 class="te-xl" style="margin-bottom: var(--te-space-lg);">features</h2>
    <div class="te-feature-list">
      <div class="te-feature">
        <span class="te-feature__text">built-in microphone for instant sampling from any source.</span>
      </div>
      <div class="te-feature">
        <span class="te-feature__text">motion effects — tilt and shake to modulate sound in real time.</span>
      </div>
      <div class="te-feature">
        <span class="te-feature__text">99 patterns with song mode for complete arrangement.</span>
      </div>
      <div class="te-feature">
        <span class="te-feature__text">built-in speaker. 3.5mm output. USB-C.</span>
      </div>
    </div>
  </div>
</section>
```

```css
.te-feature-list {
  display: flex;
  flex-direction: column;
}

.te-feature {
  padding: var(--te-space-md) 0;
  border-bottom: 1px solid var(--te-border);
}

.te-feature:first-child {
  border-top: 1px solid var(--te-border);
}

.te-feature__text {
  font-size: var(--te-text-base);
  font-weight: var(--te-weight-light);
  line-height: var(--te-leading-normal);
}
```

---

## Spec Table

```html
<div class="te-specs">
  <h2 class="te-lg" style="margin-bottom: var(--te-space-md);">specifications</h2>
  <table class="te-spec-table">
    <tbody>
      <tr>
        <td class="te-spec-table__label">speaker</td>
        <td class="te-spec-table__value">2W</td>
      </tr>
      <tr>
        <td class="te-spec-table__label">battery</td>
        <td class="te-spec-table__value">12hrs</td>
      </tr>
      <tr>
        <td class="te-spec-table__label">connectivity</td>
        <td class="te-spec-table__value">USB-C, bluetooth 5.0</td>
      </tr>
      <tr>
        <td class="te-spec-table__label">sample rate</td>
        <td class="te-spec-table__value">44.1kHz / 16-bit</td>
      </tr>
      <tr>
        <td class="te-spec-table__label">dimensions</td>
        <td class="te-spec-table__value">128 &times; 78 &times; 40mm</td>
      </tr>
      <tr>
        <td class="te-spec-table__label">weight</td>
        <td class="te-spec-table__value">340g</td>
      </tr>
    </tbody>
  </table>
</div>
```

```css
.te-spec-table {
  width: 100%;
  border-collapse: collapse;
}

.te-spec-table td {
  font-size: var(--te-text-sm);
  font-weight: var(--te-weight-light);
  padding: var(--te-space-sm) 0;
  border-bottom: 1px solid var(--te-border-light);
  vertical-align: top;
}

.te-spec-table__label {
  color: var(--te-text-secondary);
  width: 40%;
  padding-right: var(--te-space-md);
}

.te-spec-table__value {
  color: var(--te-text);
}
```

---

## Text Section (Body Content)

```html
<section class="te-text-section">
  <div class="te-container">
    <div class="te-grid">
      <div class="te-col-6">
        <p class="te-base">
          EP–133 K.O.II is the ultimate portable sampler
          and drum machine. record anything through the
          built-in microphone, chop and sequence on the fly.
        </p>
      </div>
    </div>
  </div>
</section>
```

```css
.te-text-section {
  padding: var(--te-space-xl) 0;
}

.te-text-section p {
  font-weight: var(--te-weight-light);
  line-height: var(--te-leading-normal);
  max-width: 480px;
}
```

---

## CTA Link (Not a Button)

```html
<a href="#" class="te-cta">buy now</a>
<a href="#" class="te-cta te-cta--underline">learn more</a>
```

```css
.te-cta {
  font-size: var(--te-text-sm);
  font-weight: var(--te-weight-light);
  color: var(--te-text);
  text-decoration: none;
}

.te-cta:hover { opacity: 0.6; }

.te-cta--underline {
  text-decoration: underline;
}
```

When an actual button IS needed (e.g., form submit):
```css
.te-btn {
  font-family: var(--te-font);
  font-size: var(--te-text-sm);
  font-weight: var(--te-weight-light);
  color: var(--te-text);
  background: transparent;
  border: 1px solid var(--te-border);
  padding: var(--te-space-sm) var(--te-space-md);
  cursor: pointer;
  border-radius: 0;
  transition: opacity var(--te-duration) var(--te-ease);
}

.te-btn:hover { opacity: 0.6; }
```

---

## Store Category Sidebar

```html
<aside class="te-sidebar">
  <a href="#" class="te-sidebar__link te-sidebar__link--active">all products</a>
  <a href="#" class="te-sidebar__link">pocket operators</a>
  <a href="#" class="te-sidebar__link">field system</a>
  <a href="#" class="te-sidebar__link">EP series</a>
  <a href="#" class="te-sidebar__link">synthesizers</a>
  <a href="#" class="te-sidebar__link">audio</a>
  <a href="#" class="te-sidebar__link">accessories</a>
  <a href="#" class="te-sidebar__link">apparel</a>
</aside>
```

```css
.te-sidebar {
  display: flex;
  flex-direction: column;
  gap: var(--te-space-xs);
}

.te-sidebar__link {
  font-size: var(--te-text-sm);
  font-weight: var(--te-weight-light);
  color: var(--te-text-secondary);
  text-decoration: none;
  padding: 2px 0;
}

.te-sidebar__link:hover { color: var(--te-text); opacity: 1; }

.te-sidebar__link--active {
  color: var(--te-text);
}
```

---

## Status Badges

```html
<span class="te-badge">new</span>
<span class="te-badge te-badge--limited">limited run</span>
<span class="te-badge te-badge--sale">reduced price</span>
```

```css
.te-badge {
  font-size: var(--te-text-xs);
  font-weight: var(--te-weight-light);
  color: var(--te-text);
}

.te-badge--limited {
  color: var(--te-text);
}

.te-badge--sale {
  color: var(--te-sale);
}
```
No background, no border, no pill shape — just text.

---

## Footer

```html
<footer class="te-footer">
  <div class="te-container">
    <hr class="te-divider te-divider--flush">
    <div class="te-footer__inner">
      <span class="te-xs te-secondary">
        &copy; teenage engineering 2026. all rights reserved.
      </span>
      <div class="te-footer__links">
        <a href="#">privacy</a>
        <a href="#">terms</a>
        <a href="#">press</a>
      </div>
    </div>
  </div>
</footer>
```

```css
.te-footer {
  padding: var(--te-space-xl) 0 var(--te-space-lg);
}

.te-footer__inner {
  display: flex;
  justify-content: space-between;
  align-items: baseline;
  padding-top: var(--te-space-md);
}

.te-footer__links {
  display: flex;
  gap: var(--te-space-lg);
}

.te-footer__links a {
  font-size: var(--te-text-xs);
  font-weight: var(--te-weight-light);
  color: var(--te-text-secondary);
}

.te-footer__links a:hover { opacity: 0.6; }
```

---

## Full-Width Image Section

```html
<section class="te-image-section">
  <img src="lifestyle.webp" alt="Product in use" />
</section>
```

```css
.te-image-section {
  padding: var(--te-space-lg) 0;
}

.te-image-section img {
  width: 100%;
  height: auto;
  display: block;
}

/* Contained variant */
.te-image-section--contained {
  max-width: var(--te-max-width);
  margin: 0 auto;
  padding: var(--te-space-lg) var(--te-margin);
}
```

---

## Quote Block

```html
<blockquote class="te-quote">
  <p class="te-quote__text">
    "i hated every minute of training, but I said, don't quit.
    suffer now and live the rest of your life as a champion."
  </p>
  <cite class="te-quote__cite">— muhammad ali</cite>
</blockquote>
```

```css
.te-quote {
  padding: var(--te-space-xl) 0;
}

.te-quote__text {
  font-size: var(--te-text-lg);
  font-weight: var(--te-weight-thin);
  line-height: var(--te-leading-tight);
  max-width: 640px;
  margin-bottom: var(--te-space-md);
}

.te-quote__cite {
  font-size: var(--te-text-sm);
  font-weight: var(--te-weight-light);
  font-style: normal;
  color: var(--te-text-secondary);
}
```
