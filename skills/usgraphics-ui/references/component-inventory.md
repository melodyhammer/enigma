# U.S. Graphics Company UI — Component Inventory

## Navigation

```html
<header class="usg-header">
  <div class="usg-doc">
    <div class="usg-header__inner">
      <a href="/" class="usg-header__logo">
        <span class="usg-header__logo-text">U.S. GRAPHICS COMPANY</span>
      </a>
      <nav class="usg-header__nav">
        <a href="#" class="usg-header__link">Office</a>
        <a href="#" class="usg-header__link">Products</a>
        <a href="#" class="usg-header__link">Catalog</a>
        <a href="#" class="usg-header__link">Extras</a>
        <a href="#" class="usg-header__link">Login</a>
      </nav>
    </div>
  </div>
  <hr class="usg-rule usg-rule--flush">
</header>
```

```css
.usg-header {
  padding: var(--usg-space-lg) 0;
  background: var(--usg-bg);
}

.usg-header__inner {
  display: flex;
  align-items: baseline;
  justify-content: space-between;
}

.usg-header__logo-text {
  font-family: var(--usg-font-condensed);
  font-size: 16px;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.04em;
  color: var(--usg-text);
  text-decoration: none;
}

.usg-header__logo { text-decoration: none; }

.usg-header__nav {
  display: flex;
  gap: var(--usg-space-xl);
}

.usg-header__link {
  font-family: var(--usg-font-condensed);
  font-size: 13px;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.04em;
  color: var(--usg-text);
  text-decoration: none;
}

.usg-header__link:hover {
  text-decoration: underline;
  color: var(--usg-text);
}

.usg-header__link--active {
  text-decoration: underline;
}
```

---

## Document Title Block

```html
<div class="usg-title-block">
  <span class="usg-catalog-no">TX-02</span>
  <h1 class="usg-display">BERKELEY MONO™</h1>
  <span class="usg-label">Typeface</span>
</div>
```

```css
.usg-title-block {
  padding: var(--usg-space-2xl) 0;
}

.usg-title-block .usg-catalog-no {
  display: block;
  margin-bottom: var(--usg-space-sm);
}

.usg-title-block .usg-display {
  margin-bottom: var(--usg-space-xs);
}
```

---

## Specimen Banner

```html
<div class="usg-specimen">
  <div class="usg-specimen__text">
    Aa Bb Cc Dd Ee Ff Gg Hh Ii Jj Kk Ll Mm
    Nn Oo Pp Qq Rr Ss Tt Uu Vv Ww Xx Yy Zz
  </div>
  <div class="usg-specimen__meta">
    <span class="usg-caption" style="color: var(--usg-text-inverse-muted);">
      Berkeley Mono™ — Regular 400
    </span>
  </div>
</div>
```

```css
.usg-specimen {
  background: var(--usg-bg-specimen);
  color: var(--usg-text-inverse);
  padding: var(--usg-space-3xl) var(--usg-space-2xl);
  font-family: var(--usg-font-mono);
  overflow: hidden;
}

.usg-specimen__text {
  font-size: clamp(2rem, 5vw, 4.5rem);
  line-height: 1.2;
  letter-spacing: -0.01em;
  word-break: break-all;
}

.usg-specimen__text--large {
  font-size: clamp(3rem, 8vw, 7rem);
  line-height: 1;
}

.usg-specimen__text--pangram {
  font-size: clamp(1.25rem, 2.5vw, 2rem);
  line-height: 1.5;
}

.usg-specimen__meta {
  margin-top: var(--usg-space-xl);
  padding-top: var(--usg-space-md);
  border-top: 1px solid var(--usg-border-dark);
}
```

---

## Specification Table

```html
<div class="usg-spec-table">
  <table>
    <thead>
      <tr>
        <th>ITEM</th>
        <th>SPECIFICATION</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td class="usg-spec-table__label">Widths</td>
        <td>5 (Ultra Condensed – Regular)</td>
      </tr>
      <tr>
        <td class="usg-spec-table__label">Weights</td>
        <td>12 (Thin 100 – Black 900)</td>
      </tr>
      <tr>
        <td class="usg-spec-table__label">Slants</td>
        <td>2 (Upright, Italic)</td>
      </tr>
      <tr>
        <td class="usg-spec-table__label">Total styles</td>
        <td>120</td>
      </tr>
      <tr>
        <td class="usg-spec-table__label">Variable axes</td>
        <td>wdth, wght, slnt</td>
      </tr>
      <tr>
        <td class="usg-spec-table__label">Formats</td>
        <td>OTF, TTF, WOFF2</td>
      </tr>
    </tbody>
  </table>
</div>
```

```css
.usg-spec-table table {
  width: 100%;
  border-collapse: collapse;
  font-family: var(--usg-font-mono);
  font-size: var(--usg-text-body);
}

.usg-spec-table thead th {
  font-family: var(--usg-font-condensed);
  font-size: var(--usg-text-caption);
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.05em;
  color: var(--usg-text-secondary);
  text-align: left;
  padding: var(--usg-space-sm) var(--usg-space-md);
  border-bottom: 2px solid var(--usg-rule);
}

.usg-spec-table tbody td {
  padding: var(--usg-space-sm) var(--usg-space-md);
  border-bottom: 1px solid var(--usg-rule-light);
  vertical-align: top;
}

.usg-spec-table__label {
  font-family: var(--usg-font-condensed);
  font-size: var(--usg-text-caption);
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.05em;
  color: var(--usg-text-secondary);
  white-space: nowrap;
  width: 180px;
}

.usg-spec-table tbody tr:hover {
  background: var(--usg-bg-muted);
}

/* Alternating rows variant */
.usg-spec-table--striped tbody tr:nth-child(even) {
  background: var(--usg-bg-muted);
}
```

---

## Buttons

```html
<button class="usg-btn">Add to Cart</button>
<button class="usg-btn usg-btn--filled">Purchase Now</button>
<a href="#" class="usg-btn usg-btn--link">Available Now →</a>
<button class="usg-btn" disabled>Sold Out</button>
```

```css
.usg-btn {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  font-family: var(--usg-font-condensed);
  font-size: 13px;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.06em;
  padding: 12px 24px;
  border: 1px solid var(--usg-text);
  background: transparent;
  color: var(--usg-text);
  cursor: pointer;
  border-radius: 0;
  text-decoration: none;
  transition: all var(--usg-duration) var(--usg-ease);
}

.usg-btn:hover {
  background: var(--usg-text);
  color: var(--usg-bg);
}

.usg-btn--filled {
  background: var(--usg-text);
  color: var(--usg-bg);
}

.usg-btn--filled:hover {
  background: #333;
}

.usg-btn--link {
  border: none;
  padding: 0;
  background: none;
  text-decoration: underline;
}

.usg-btn--link:hover {
  color: var(--usg-link-hover);
  background: none;
}

.usg-btn:disabled,
.usg-btn[disabled] {
  border-color: var(--usg-border);
  color: var(--usg-text-tertiary);
  cursor: not-allowed;
}

.usg-btn:disabled:hover {
  background: transparent;
  color: var(--usg-text-tertiary);
}
```

---

## Product Listing Block

```html
<article class="usg-product">
  <hr class="usg-rule">
  <div class="usg-product__header">
    <span class="usg-catalog-no">TX-02</span>
    <span class="usg-status usg-status--new">New!</span>
  </div>
  <h2 class="usg-h1 usg-product__name">BERKELEY MONO™ TYPEFACE</h2>

  <div class="usg-specimen">
    <div class="usg-specimen__text">
      The quick brown fox jumps over the lazy dog.
    </div>
  </div>

  <div class="usg-product__body">
    <p>A love letter to the golden era of computing.
    Berkeley Mono is fitted with care to perform as well
    as proportional typefaces whilst being 100% monospaced.</p>
  </div>

  <div class="usg-product__footer">
    <a href="#" class="usg-btn usg-btn--link">Available Now →</a>
  </div>
</article>
```

```css
.usg-product {
  padding: var(--usg-space-2xl) 0;
}

.usg-product__header {
  display: flex;
  align-items: center;
  gap: var(--usg-space-md);
  margin-bottom: var(--usg-space-sm);
}

.usg-product__name {
  margin-bottom: var(--usg-space-xl);
}

.usg-product .usg-specimen {
  margin-bottom: var(--usg-space-xl);
}

.usg-product__body {
  max-width: var(--usg-reading-width);
  margin-bottom: var(--usg-space-lg);
}

.usg-product__body p {
  font-family: var(--usg-font-mono);
  font-size: var(--usg-text-body);
  line-height: var(--usg-leading-body);
  color: var(--usg-text-secondary);
}
```

---

## Pricing Block

```html
<div class="usg-pricing">
  <table class="usg-pricing__table">
    <tbody>
      <tr>
        <td class="usg-pricing__label">Catalog no.</td>
        <td class="usg-pricing__value">FX-102</td>
      </tr>
      <tr>
        <td class="usg-pricing__label">Description</td>
        <td class="usg-pricing__value">Berkeley Mono™ Developer License</td>
      </tr>
      <tr>
        <td class="usg-pricing__label">Unit price</td>
        <td class="usg-pricing__value">$75.00</td>
      </tr>
      <tr>
        <td class="usg-pricing__label">Availability</td>
        <td class="usg-pricing__value">In Stock</td>
      </tr>
    </tbody>
  </table>
  <hr class="usg-rule--light" style="border:none;border-top:1px solid var(--usg-rule-light);margin:16px 0">
  <div style="text-align: right;">
    <button class="usg-btn">Add to Cart</button>
  </div>
</div>
```

```css
.usg-pricing__table {
  width: 100%;
  border-collapse: collapse;
}

.usg-pricing__table td {
  padding: 6px 0;
  vertical-align: top;
}

.usg-pricing__label {
  font-family: var(--usg-font-condensed);
  font-size: var(--usg-text-caption);
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.05em;
  color: var(--usg-text-secondary);
  width: 140px;
  padding-right: var(--usg-space-lg);
}

.usg-pricing__value {
  font-family: var(--usg-font-mono);
  font-size: var(--usg-text-body);
}
```

---

## Stat/Metric Display

```html
<div class="usg-metric">
  <span class="usg-metric__value">120</span>
  <span class="usg-metric__label">Total Font Styles</span>
</div>
```

```css
.usg-metric {
  display: flex;
  flex-direction: column;
  gap: var(--usg-space-xs);
}

.usg-metric__value {
  font-family: var(--usg-font-mono);
  font-size: clamp(2rem, 4vw, 3rem);
  font-weight: 400;
  line-height: 1;
  letter-spacing: -0.02em;
}

.usg-metric__label {
  font-family: var(--usg-font-condensed);
  font-size: var(--usg-text-caption);
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.05em;
  color: var(--usg-text-secondary);
}
```

---

## Metric Grid

```html
<div class="usg-metric-grid">
  <div class="usg-metric">
    <span class="usg-metric__value">5</span>
    <span class="usg-metric__label">Widths</span>
  </div>
  <div class="usg-metric">
    <span class="usg-metric__value">12</span>
    <span class="usg-metric__label">Weights</span>
  </div>
  <div class="usg-metric">
    <span class="usg-metric__value">2</span>
    <span class="usg-metric__label">Slants</span>
  </div>
  <div class="usg-metric">
    <span class="usg-metric__value">120</span>
    <span class="usg-metric__label">Styles</span>
  </div>
</div>
```

```css
.usg-metric-grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: var(--usg-space-lg);
  padding: var(--usg-space-xl) 0;
  border-top: 1px solid var(--usg-rule);
  border-bottom: 1px solid var(--usg-rule);
}

@media (max-width: 768px) {
  .usg-metric-grid { grid-template-columns: repeat(2, 1fr); }
}
```

---

## Form Field

```html
<div class="usg-field">
  <label class="usg-label" for="email">Email Address</label>
  <input type="email" id="email" class="usg-input" placeholder="name@company.com">
</div>
```

```css
.usg-field {
  margin-bottom: var(--usg-space-lg);
}

.usg-field .usg-label {
  display: block;
  margin-bottom: var(--usg-space-xs);
}

.usg-input {
  font-family: var(--usg-font-mono);
  font-size: var(--usg-text-body);
  padding: 10px 12px;
  border: 1px solid var(--usg-border);
  background: var(--usg-bg-pure);
  color: var(--usg-text);
  border-radius: 0;
  width: 100%;
  outline: none;
  transition: border-color var(--usg-duration) var(--usg-ease);
}

.usg-input:focus {
  border-color: var(--usg-text);
}

.usg-input::placeholder {
  color: var(--usg-text-tertiary);
}

.usg-select {
  appearance: none;
  font-family: var(--usg-font-mono);
  font-size: var(--usg-text-body);
  padding: 10px 32px 10px 12px;
  border: 1px solid var(--usg-border);
  background: var(--usg-bg-pure) url("data:image/svg+xml,%3Csvg width='10' height='6' viewBox='0 0 10 6' fill='none' xmlns='http://www.w3.org/2000/svg'%3E%3Cpath d='M1 1l4 4 4-4' stroke='%231A1A1A' stroke-width='1.5'/%3E%3C/svg%3E") right 12px center no-repeat;
  color: var(--usg-text);
  border-radius: 0;
  width: 100%;
  cursor: pointer;
}
```

---

## Footer

```html
<footer class="usg-footer">
  <hr class="usg-rule usg-rule--flush">
  <div class="usg-doc">
    <div class="usg-footer__inner">
      <span class="usg-caption">
        © 2026 U.S. Graphics Company. All rights reserved.
      </span>
      <span class="usg-caption">
        Production v2.4.1
      </span>
    </div>
  </div>
</footer>
```

```css
.usg-footer {
  padding: var(--usg-space-lg) 0 var(--usg-space-2xl);
}

.usg-footer__inner {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding-top: var(--usg-space-lg);
}

.usg-footer__links {
  display: flex;
  gap: var(--usg-space-xl);
}

.usg-footer__links a {
  font-family: var(--usg-font-condensed);
  font-size: var(--usg-text-caption);
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.04em;
  color: var(--usg-text-secondary);
  text-decoration: none;
}

.usg-footer__links a:hover {
  text-decoration: underline;
  color: var(--usg-text);
}
```

---

## Glyph Grid (Character Showcase)

```html
<div class="usg-glyph-grid">
  <span>A</span><span>B</span><span>C</span><span>D</span>
  <span>E</span><span>F</span><span>G</span><span>H</span>
  <span>a</span><span>b</span><span>c</span><span>d</span>
  <span>0</span><span>1</span><span>2</span><span>3</span>
  <span>@</span><span>#</span><span>&amp;</span><span>%</span>
</div>
```

```css
.usg-glyph-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(60px, 1fr));
  gap: 1px;
  background: var(--usg-rule-light);
  border: 1px solid var(--usg-rule-light);
}

.usg-glyph-grid span {
  display: flex;
  align-items: center;
  justify-content: center;
  font-family: var(--usg-font-mono);
  font-size: 28px;
  padding: var(--usg-space-lg);
  background: var(--usg-bg);
  aspect-ratio: 1;
}

.usg-glyph-grid span:hover {
  background: var(--usg-bg-muted);
}
```
