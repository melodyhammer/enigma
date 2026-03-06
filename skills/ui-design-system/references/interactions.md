# Interaction Patterns & Animation Specs

## General Transition Tokens

```css
--transition-fast: 0.15s ease;    /* hover states, toggles */
--transition-default: 0.2s ease;  /* card lifts, color changes */
--transition-slow: 0.3s ease;     /* accordion expand, dropdown open */
```

---

## Hover States

### Cards
```css
.ds-card:hover {
  transform: translateY(-2px);
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.2);
  transition: transform var(--transition-default), box-shadow var(--transition-default);
}
```

### Buttons
```css
.btn:hover { opacity: 0.85; }
.btn:active { opacity: 0.7; transform: scale(0.98); }
.btn-outlined:hover {
  background: var(--text-on-light);
  color: var(--text-primary);
}
```

### Chips
```css
.chip:hover {
  background: var(--text-on-light);
  color: var(--text-primary);
  transition: all var(--transition-fast);
}
```

### List Items
```css
.list-item:hover {
  background: var(--surface-elevated);
}
```

---

## Toggle Animation

```css
.toggle-thumb {
  transition: transform var(--transition-fast);
}
.toggle input:checked + .toggle-track .toggle-thumb {
  transform: translateX(16px);
}
.toggle-track {
  transition: background var(--transition-fast);
}
```

---

## Accordion Expand/Collapse

```css
.accordion-body {
  max-height: 0;
  overflow: hidden;
  transition: max-height var(--transition-slow), padding var(--transition-slow);
}
.accordion-item.open .accordion-body {
  max-height: 500px; /* generous max */
}
.accordion-chevron {
  transition: transform var(--transition-fast);
}
.accordion-item.open .accordion-chevron {
  transform: rotate(180deg);
}
```

**JavaScript:**
```javascript
document.querySelectorAll('.accordion-header').forEach(header => {
  header.addEventListener('click', () => {
    header.closest('.accordion-item').classList.toggle('open');
  });
});
```

---

## Dropdown Open/Close

```javascript
document.querySelectorAll('.dropdown-trigger').forEach(trigger => {
  trigger.addEventListener('click', (e) => {
    e.stopPropagation();
    trigger.closest('.dropdown').classList.toggle('open');
  });
});

// Close on outside click
document.addEventListener('click', () => {
  document.querySelectorAll('.dropdown.open').forEach(d => d.classList.remove('open'));
});

// Select item
document.querySelectorAll('.dropdown-item').forEach(item => {
  item.addEventListener('click', () => {
    const dropdown = item.closest('.dropdown');
    dropdown.querySelectorAll('.dropdown-item').forEach(i => i.classList.remove('selected'));
    item.classList.add('selected');
    dropdown.querySelector('.dropdown-trigger span').textContent = item.textContent.trim();
    dropdown.classList.remove('open');
  });
});
```

---

## Slider Interaction

```javascript
const slider = document.querySelector('.slider');
slider.addEventListener('input', (e) => {
  const value = e.target.value;
  // Update associated value display or markers
});
```

---

## Loader Animations

### Grid Loader (cycling pattern)
```javascript
function animateGridLoader(container, interval = 200) {
  const dots = container.querySelectorAll('.loader-dot');
  let current = 0;
  setInterval(() => {
    dots.forEach(d => d.classList.remove('active'));
    dots[current % dots.length].classList.add('active');
    current++;
  }, interval);
}
```

### Spinner (pure CSS)
```css
@keyframes spin {
  to { transform: rotate(360deg); }
}
.loader-spinner {
  animation: spin 1s steps(8) infinite;
}
```

### Arc Loader (pure CSS)
```css
@keyframes arc-spin {
  to { transform: rotate(360deg); }
}
.arc-fill {
  animation: arc-spin 1s linear infinite;
  transform-origin: center;
}
```

---

## Banner/Toast Dismiss

```javascript
document.querySelectorAll('.banner-close').forEach(btn => {
  btn.addEventListener('click', () => {
    const banner = btn.closest('.banner, .toast');
    banner.style.opacity = '0';
    banner.style.transform = 'translateY(-10px)';
    setTimeout(() => banner.remove(), 200);
  });
});
```

---

## Chart Interactions

Charts in this design system are intentionally minimal — no tooltips or hover states by default. If interactivity is needed:

```javascript
// Optional: highlight data point on hover
document.querySelectorAll('.chart-bar').forEach(bar => {
  bar.addEventListener('mouseenter', () => {
    bar.style.opacity = '0.7';
  });
  bar.addEventListener('mouseleave', () => {
    bar.style.opacity = '1';
  });
});
```

---

## Scroll Reveal (if used in page context)

```javascript
const observer = new IntersectionObserver((entries) => {
  entries.forEach(entry => {
    if (entry.isIntersecting) {
      entry.target.classList.add('visible');
    }
  });
}, { threshold: 0.1 });

document.querySelectorAll('.animate-in').forEach(el => observer.observe(el));
```

```css
.animate-in {
  opacity: 0;
  transform: translateY(20px);
  transition: opacity 0.5s ease, transform 0.5s ease;
}
.animate-in.visible {
  opacity: 1;
  transform: translateY(0);
}
```

---

## Keyboard Accessibility

All interactive components should support keyboard navigation:

```css
/* Focus visible ring */
:focus-visible {
  outline: 2px solid var(--color-process);
  outline-offset: 2px;
}
```

- **Buttons:** Enter/Space to activate
- **Toggles:** Space to toggle
- **Accordion:** Enter/Space to expand/collapse
- **Dropdown:** Enter to open, Arrow keys to navigate, Enter to select, Escape to close
- **Slider:** Arrow keys to adjust value
- **Chips:** Enter/Space to select/deselect
