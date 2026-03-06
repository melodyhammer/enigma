# Component Inventory — HTML/CSS Patterns

## Base Panel

Every component group lives inside a panel container:

```html
<div class="ds-panel">
  <span class="ds-panel-label">Component Name</span>
  <span class="ds-panel-indicator">⊘</span>
  <div class="ds-panel-content">
    <!-- Component content -->
  </div>
</div>
```

```css
.ds-panel {
  background: var(--surface-primary);
  border: 1px solid var(--border-default);
  padding: 16px;
  padding-top: 32px; /* room for label */
  position: relative;
}
.ds-panel-label {
  position: absolute;
  top: 8px;
  left: 12px;
  font: 400 14px var(--font-mono);
  color: var(--text-primary);
}
.ds-panel-indicator {
  position: absolute;
  top: 8px;
  right: 12px;
  font-size: 14px;
  color: var(--text-secondary);
}
```

---

## Buttons

### Filled Button
```html
<button class="btn btn-filled">Label</button>
```
```css
.btn {
  font: 500 12px var(--font-mono);
  padding: 8px 16px;
  border: none;
  cursor: pointer;
  transition: opacity var(--transition-fast);
}
.btn-filled {
  background: var(--text-on-light);
  color: var(--text-primary);
}
.btn-filled:hover { opacity: 0.85; }
```

### Outlined Button
```html
<button class="btn btn-outlined">Label</button>
```
```css
.btn-outlined {
  background: transparent;
  color: var(--text-on-light);
  border: 1px solid var(--border-canvas);
}
```

### Icon Button
```html
<button class="btn btn-icon">
  <svg class="icon">...</svg>
</button>
```
```css
.btn-icon {
  width: 32px;
  height: 32px;
  padding: 4px;
  display: inline-flex;
  align-items: center;
  justify-content: center;
  background: var(--text-on-light);
  color: var(--text-primary);
  border: none;
}
```

### Dropdown Button
```html
<button class="btn btn-dropdown">
  <span>Select</span>
  <span class="chevron">▾</span>
</button>
```
```css
.btn-dropdown {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  background: var(--text-on-light);
  color: var(--text-primary);
  padding: 8px 12px;
  border: none;
}
```

### Full-Width Button
```css
.btn-full { width: 100%; }
```

---

## Checkboxes

```html
<label class="checkbox">
  <input type="checkbox" />
  <span class="checkbox-box"></span>
  <span class="checkbox-label">Checkbox</span>
</label>
```

```css
.checkbox { display: inline-flex; align-items: center; gap: 8px; cursor: pointer; }
.checkbox input { display: none; }
.checkbox-box {
  width: 16px;
  height: 16px;
  border: 1.5px solid var(--border-canvas);
  background: transparent;
  position: relative;
}
.checkbox input:checked + .checkbox-box {
  background: var(--text-on-light);
  border-color: var(--text-on-light);
}
.checkbox input:checked + .checkbox-box::after {
  content: '✓';
  color: var(--text-primary);
  font-size: 12px;
  position: absolute;
  inset: 0;
  display: flex;
  align-items: center;
  justify-content: center;
}
/* Variant: colored fill */
.checkbox-box--accent {
  /* Uses --color-process or --color-status for checked bg */
}
```

---

## Chips

```html
<div class="chip-group">
  <span class="chip">Chips</span>
  <span class="chip">Banner</span>
  <span class="chip">Chip</span>
  <span class="chip">Chips</span>
</div>
```

```css
.chip-group { display: flex; flex-wrap: wrap; gap: 8px; }
.chip {
  font: 500 11px var(--font-mono);
  padding: 4px 12px;
  border: 1px solid var(--border-canvas);
  background: transparent;
  color: var(--text-on-light);
  cursor: pointer;
}
.chip:hover { background: var(--text-on-light); color: var(--text-primary); }
.chip.active { background: var(--text-on-light); color: var(--text-primary); }
```

---

## Banner & Toast

### Banner
```html
<div class="banner">
  <span class="banner-text">Banner message</span>
  <div class="banner-colors">
    <span class="color-dot" style="background: var(--color-signal)"></span>
    <span class="color-dot" style="background: var(--color-indicator)"></span>
    <span class="color-dot" style="background: var(--color-status)"></span>
    <span class="color-dot" style="background: var(--color-alert)"></span>
    <span class="color-dot" style="background: var(--color-process)"></span>
    <!-- additional dots -->
  </div>
  <button class="banner-close">×</button>
</div>
```

```css
.banner {
  display: flex;
  align-items: center;
  gap: 12px;
  background: var(--surface-primary);
  padding: 8px 12px;
  border: 1px solid var(--border-default);
}
.banner-text { font: 400 12px var(--font-mono); color: var(--text-primary); }
.banner-colors { display: flex; gap: 4px; }
.color-dot { width: 10px; height: 10px; border-radius: 1px; }
.banner-close {
  margin-left: auto;
  background: none;
  border: none;
  color: var(--text-primary);
  font-size: 16px;
  cursor: pointer;
}
```

### Toast
Same structure, smaller and positioned fixed:
```css
.toast {
  position: fixed;
  bottom: 24px;
  right: 24px;
  /* same styling as banner but more compact */
  padding: 6px 12px;
}
```

---

## Avatar

```html
<div class="avatar avatar-lg">
  <div class="avatar-icon">👤</div>
  <span class="avatar-status avatar-status--busy"></span>
</div>
```

```css
.avatar {
  position: relative;
  border-radius: var(--radius-full);
  background: var(--surface-elevated);
  border: 1px solid var(--border-default);
  display: flex;
  align-items: center;
  justify-content: center;
}
.avatar-sm { width: 32px; height: 32px; }
.avatar-md { width: 48px; height: 48px; }
.avatar-lg { width: 64px; height: 64px; }

.avatar-status {
  position: absolute;
  bottom: 2px;
  right: 2px;
  width: 12px;
  height: 12px;
  border-radius: var(--radius-full);
  border: 2px solid var(--surface-primary);
}
.avatar-status--active { background: var(--color-status); }
.avatar-status--busy { background: var(--color-alert); }
.avatar-status--offline { background: var(--text-secondary); }
```

---

## Sliders & Toggles

### Slider
```html
<div class="slider-group">
  <label class="slider-label">Slider</label>
  <input type="range" class="slider" />
  <div class="slider-markers">
    <!-- colored dots along track -->
  </div>
</div>
```

```css
.slider {
  -webkit-appearance: none;
  width: 100%;
  height: 2px;
  background: var(--border-default);
}
.slider::-webkit-slider-thumb {
  -webkit-appearance: none;
  width: 14px;
  height: 14px;
  border-radius: var(--radius-full);
  background: var(--text-on-light);
  cursor: pointer;
}
```

### Toggle
```html
<label class="toggle">
  <input type="checkbox" />
  <span class="toggle-track">
    <span class="toggle-thumb"></span>
  </span>
  <span class="toggle-label">Toggle</span>
</label>
```

```css
.toggle { display: inline-flex; align-items: center; gap: 8px; }
.toggle input { display: none; }
.toggle-track {
  width: 32px;
  height: 16px;
  background: var(--border-default);
  border-radius: var(--radius-pill);
  position: relative;
  transition: background var(--transition-fast);
}
.toggle-thumb {
  width: 12px;
  height: 12px;
  background: var(--text-primary);
  border-radius: var(--radius-full);
  position: absolute;
  top: 2px;
  left: 2px;
  transition: transform var(--transition-fast);
}
.toggle input:checked + .toggle-track {
  background: var(--color-process);
}
.toggle input:checked + .toggle-track .toggle-thumb {
  transform: translateX(16px);
}
```

---

## Accordion

```html
<div class="accordion">
  <div class="accordion-item">
    <button class="accordion-header">
      <span>Section Title</span>
      <span class="accordion-chevron">▾</span>
    </button>
    <div class="accordion-body">
      <p>Content text here...</p>
    </div>
  </div>
</div>
```

```css
.accordion {
  background: var(--surface-primary);
  border: 1px solid var(--border-default);
}
.accordion-header {
  width: 100%;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 12px 16px;
  background: none;
  border: none;
  border-bottom: 1px solid var(--border-default);
  color: var(--text-primary);
  font: 400 13px var(--font-mono);
  cursor: pointer;
}
.accordion-chevron {
  transition: transform var(--transition-fast);
}
.accordion-item.open .accordion-chevron {
  transform: rotate(180deg);
}
.accordion-body {
  max-height: 0;
  overflow: hidden;
  transition: max-height var(--transition-slow);
  padding: 0 16px;
}
.accordion-item.open .accordion-body {
  max-height: 500px;
  padding: 12px 16px;
}
```

---

## Cards (Color Grid)

```html
<div class="card-grid">
  <div class="ds-card">
    <div class="dot-grid">
      <span class="dot" style="background: var(--color-signal)"></span>
      <span class="dot" style="background: var(--color-status)"></span>
      <!-- ... rows of colored dots -->
    </div>
  </div>
</div>
```

```css
.ds-card {
  background: var(--surface-primary);
  border: 1px solid var(--border-default);
  padding: 16px;
}
.dot-grid {
  display: grid;
  grid-template-columns: repeat(8, 1fr);
  gap: 6px;
}
.dot {
  width: 10px;
  height: 10px;
  border-radius: 1px;
}
```

---

## Forms

```html
<div class="form-panel">
  <div class="form-group">
    <label class="form-label">Field Label</label>
    <input type="text" class="form-input" placeholder="Enter value..." />
  </div>
  <div class="form-group">
    <label class="form-label">Another Field</label>
    <input type="text" class="form-input" />
  </div>
  <button class="btn btn-filled btn-full">Submit</button>
</div>
```

```css
.form-panel {
  background: var(--surface-primary);
  border: 1px solid var(--border-default);
  padding: 16px;
  display: flex;
  flex-direction: column;
  gap: 12px;
}
.form-group { display: flex; flex-direction: column; gap: 4px; }
.form-label {
  font: 400 11px var(--font-mono);
  color: var(--text-secondary);
  text-transform: uppercase;
}
.form-input {
  background: var(--surface-input);
  border: 1px solid var(--border-default);
  padding: 8px 12px;
  font: 400 13px var(--font-mono);
  color: var(--text-primary);
}
.form-input:focus {
  outline: none;
  border-color: var(--color-process);
}
.form-input::placeholder { color: var(--text-secondary); }
```

---

## Dropdowns

```html
<div class="dropdown">
  <button class="dropdown-trigger">
    <span>Select option</span>
    <span class="dropdown-chevron">▲</span>
  </button>
  <div class="dropdown-menu">
    <div class="dropdown-item selected">
      <span class="dropdown-check">✓</span>
      <span>Option A</span>
    </div>
    <div class="dropdown-item">
      <span class="dropdown-check"></span>
      <span>Option B</span>
    </div>
    <div class="dropdown-item">
      <span class="dropdown-check"></span>
      <span>Option C</span>
    </div>
  </div>
</div>
```

```css
.dropdown { position: relative; display: inline-block; }
.dropdown-trigger {
  display: flex;
  align-items: center;
  gap: 8px;
  padding: 8px 12px;
  background: var(--surface-primary);
  border: 1px solid var(--border-default);
  color: var(--text-primary);
  font: 400 13px var(--font-mono);
  cursor: pointer;
}
.dropdown-menu {
  position: absolute;
  top: 100%;
  left: 0;
  width: 100%;
  background: var(--surface-primary);
  border: 1px solid var(--border-default);
  z-index: 10;
  display: none;
}
.dropdown.open .dropdown-menu { display: block; }
.dropdown-item {
  display: flex;
  align-items: center;
  gap: 8px;
  padding: 8px 12px;
  font: 400 13px var(--font-mono);
  color: var(--text-primary);
  cursor: pointer;
}
.dropdown-item:hover { background: var(--surface-elevated); }
.dropdown-check { width: 16px; font-size: 12px; }
.dropdown-item.selected .dropdown-check { color: var(--color-status); }
```

---

## List

```html
<div class="list-panel">
  <div class="list-item">
    <span class="list-check">✓</span>
    <span class="list-text">List item content</span>
    <div class="list-indicators">
      <span class="color-dot" style="background: var(--color-signal)"></span>
      <span class="color-dot" style="background: var(--color-status)"></span>
      <span class="color-dot" style="background: var(--color-process)"></span>
    </div>
  </div>
  <!-- more items -->
</div>
```

```css
.list-panel {
  background: var(--surface-primary);
  border: 1px solid var(--border-default);
}
.list-item {
  display: flex;
  align-items: center;
  gap: 12px;
  padding: 8px 12px;
  border-bottom: 1px solid var(--border-default);
  font: 400 13px var(--font-mono);
  color: var(--text-primary);
}
.list-check { width: 16px; color: var(--text-secondary); }
.list-text { flex: 1; }
.list-indicators { display: flex; gap: 4px; }
```

---

## Line Graph / Charts

```html
<div class="chart-panel">
  <div class="chart-area">
    <svg class="chart-svg" viewBox="0 0 600 200">
      <!-- Dashed grid lines -->
      <line class="grid-line" x1="0" y1="50" x2="600" y2="50" />
      <line class="grid-line" x1="0" y1="100" x2="600" y2="100" />
      <line class="grid-line" x1="0" y1="150" x2="600" y2="150" />
      <!-- Data line -->
      <polyline class="data-line" points="0,120 100,80 200,140 300,40 400,90 500,60 600,100" />
    </svg>
  </div>
</div>
```

```css
.chart-panel {
  background: var(--surface-primary);
  border: 1px solid var(--border-default);
  padding: 16px;
}
.grid-line {
  stroke: var(--border-light);
  stroke-width: 1;
  stroke-dasharray: 4 4;
}
.data-line {
  fill: none;
  stroke: var(--text-primary);
  stroke-width: 1.5;
}
/* Bar chart bars */
.chart-bar {
  fill: var(--text-primary);
}
/* Pie chart */
.chart-arc {
  fill: none;
  stroke: var(--text-primary);
  stroke-width: 1.5;
  stroke-dasharray: 8 4;
}
```

---

## Loaders

### Grid Loader
```html
<div class="loader-grid">
  <span class="loader-dot"></span>
  <span class="loader-dot active"></span>
  <span class="loader-dot"></span>
  <span class="loader-dot active"></span>
  <!-- 3x3 or 4x4 grid -->
</div>
```

```css
.loader-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 4px;
}
.loader-dot {
  width: 6px;
  height: 6px;
  border-radius: var(--radius-full);
  background: var(--text-primary);
  opacity: 0.2;
}
.loader-dot.active { opacity: 1; }
/* Animate by cycling which dots are active */
```

### Spinner Loader
```html
<div class="loader-spinner">
  <!-- 8-12 dots in a circle -->
  <span class="spinner-dot" style="--i: 0"></span>
  <span class="spinner-dot" style="--i: 1"></span>
  <!-- ... -->
</div>
```

```css
.loader-spinner {
  width: 32px;
  height: 32px;
  position: relative;
  animation: spin 1s steps(8) infinite;
}
.spinner-dot {
  position: absolute;
  width: 4px;
  height: 4px;
  border-radius: var(--radius-full);
  background: var(--text-primary);
  opacity: calc(0.1 + var(--i) * 0.1125);
  transform: rotate(calc(var(--i) * 45deg)) translateY(-12px);
  transform-origin: center center;
}
@keyframes spin {
  to { transform: rotate(360deg); }
}
```

### Arc Loader
```html
<div class="loader-arc">
  <svg viewBox="0 0 32 32">
    <circle class="arc-track" cx="16" cy="16" r="12" />
    <circle class="arc-fill" cx="16" cy="16" r="12" />
  </svg>
</div>
```

```css
.arc-track {
  fill: none;
  stroke: var(--border-default);
  stroke-width: 2;
}
.arc-fill {
  fill: none;
  stroke: var(--text-primary);
  stroke-width: 2;
  stroke-dasharray: 25 75;
  stroke-linecap: round;
  animation: arc-spin 1s linear infinite;
}
@keyframes arc-spin {
  to { transform: rotate(360deg); transform-origin: center; }
}
```
