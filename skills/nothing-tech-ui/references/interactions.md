# Nothing Tech UI — Interactions & Animations

## Scroll Reveal

Elements fade in and slide up as they enter the viewport. This is the primary animation pattern — used on nearly every section.

```javascript
function initScrollReveal() {
  const elements = document.querySelectorAll('[data-reveal]');

  const observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        entry.target.classList.add('nt-revealed');
        observer.unobserve(entry.target);
      }
    });
  }, { threshold: 0.2 });

  elements.forEach(el => observer.observe(el));
}

document.addEventListener('DOMContentLoaded', initScrollReveal);
```

```css
[data-reveal] {
  opacity: 0;
  transform: translateY(24px);
  transition:
    opacity 600ms cubic-bezier(0.16, 1, 0.3, 1),
    transform 600ms cubic-bezier(0.16, 1, 0.3, 1);
}

[data-reveal].nt-revealed {
  opacity: 1;
  transform: translateY(0);
}

/* Stagger children */
[data-reveal-stagger] > * {
  opacity: 0;
  transform: translateY(16px);
  transition:
    opacity 500ms cubic-bezier(0.16, 1, 0.3, 1),
    transform 500ms cubic-bezier(0.16, 1, 0.3, 1);
}

[data-reveal-stagger].nt-revealed > *:nth-child(1) { transition-delay: 0ms; }
[data-reveal-stagger].nt-revealed > *:nth-child(2) { transition-delay: 100ms; }
[data-reveal-stagger].nt-revealed > *:nth-child(3) { transition-delay: 200ms; }
[data-reveal-stagger].nt-revealed > *:nth-child(4) { transition-delay: 300ms; }
[data-reveal-stagger].nt-revealed > *:nth-child(5) { transition-delay: 400ms; }
[data-reveal-stagger].nt-revealed > *:nth-child(6) { transition-delay: 500ms; }

[data-reveal-stagger].nt-revealed > * {
  opacity: 1;
  transform: translateY(0);
}
```

Usage:
```html
<h2 data-reveal>it's metal now.</h2>

<div data-reveal data-reveal-stagger>
  <div class="nt-spec-card">...</div>
  <div class="nt-spec-card">...</div>
  <div class="nt-spec-card">...</div>
</div>
```

---

## Navigation Scroll Behavior

Nav background becomes opaque and gains a shadow on scroll.

```javascript
function initNavScroll() {
  const nav = document.querySelector('.nt-nav');
  let lastScroll = 0;

  window.addEventListener('scroll', () => {
    const scrollY = window.scrollY;

    // Add solid background after scrolling past hero
    if (scrollY > 100) {
      nav.classList.add('nt-nav--scrolled');
    } else {
      nav.classList.remove('nt-nav--scrolled');
    }

    // Hide nav on scroll down, show on scroll up
    if (scrollY > lastScroll && scrollY > 300) {
      nav.classList.add('nt-nav--hidden');
    } else {
      nav.classList.remove('nt-nav--hidden');
    }

    lastScroll = scrollY;
  });
}
```

```css
.nt-nav--scrolled {
  background: rgba(255, 255, 255, 0.98);
  box-shadow: 0 1px 0 rgba(0, 0, 0, 0.05);
}

.nt-nav--hidden {
  transform: translateY(-100%);
  transition: transform 300ms cubic-bezier(0.65, 0, 0.35, 1);
}

.nt-nav {
  transition:
    transform 300ms cubic-bezier(0.65, 0, 0.35, 1),
    background 200ms ease,
    box-shadow 200ms ease;
}
```

---

## Dot-Matrix Animated Background

Canvas-based animated dot grid for hero sections or loading states.

```javascript
function initDotMatrix(canvas) {
  const ctx = canvas.getContext('2d');
  const dpr = window.devicePixelRatio || 1;
  let width, height;

  function resize() {
    width = canvas.parentElement.offsetWidth;
    height = canvas.parentElement.offsetHeight;
    canvas.width = width * dpr;
    canvas.height = height * dpr;
    canvas.style.width = width + 'px';
    canvas.style.height = height + 'px';
    ctx.scale(dpr, dpr);
  }

  const spacing = 20;
  const dotRadius = 1;

  function draw(time) {
    ctx.clearRect(0, 0, width, height);

    for (let x = spacing; x < width; x += spacing) {
      for (let y = spacing; y < height; y += spacing) {
        // Wave pattern from center
        const dx = x - width / 2;
        const dy = y - height / 2;
        const dist = Math.sqrt(dx * dx + dy * dy);
        const wave = Math.sin(dist * 0.01 - time * 0.002) * 0.5 + 0.5;

        const alpha = 0.08 + wave * 0.15;
        const radius = dotRadius + wave * 0.5;

        ctx.beginPath();
        ctx.arc(x, y, radius, 0, Math.PI * 2);
        ctx.fillStyle = `rgba(0, 0, 0, ${alpha})`;
        ctx.fill();
      }
    }

    requestAnimationFrame(draw);
  }

  resize();
  window.addEventListener('resize', resize);
  requestAnimationFrame(draw);
}
```

---

## Image Parallax

Subtle parallax on hero images — image moves slower than scroll.

```javascript
function initParallax() {
  const heroes = document.querySelectorAll('.nt-hero__media img');

  window.addEventListener('scroll', () => {
    const scrollY = window.scrollY;
    heroes.forEach(img => {
      const section = img.closest('.nt-hero');
      const rect = section.getBoundingClientRect();
      if (rect.bottom > 0 && rect.top < window.innerHeight) {
        const offset = scrollY * 0.15;
        img.style.transform = `translateY(${offset}px) scale(1.05)`;
      }
    });
  }, { passive: true });
}
```

---

## Smooth Scroll Progress Bar

```javascript
function initScrollProgress() {
  const bar = document.querySelector('.nt-scroll-indicator__bar');
  if (!bar) return;

  window.addEventListener('scroll', () => {
    const scrollTop = window.scrollY;
    const docHeight = document.documentElement.scrollHeight - window.innerHeight;
    const progress = (scrollTop / docHeight) * 100;
    bar.style.width = progress + '%';
  }, { passive: true });
}
```

---

## Horizontal Product Scroll with Drag

```javascript
function initDragScroll(container) {
  let isDown = false;
  let startX;
  let scrollLeft;

  container.addEventListener('mousedown', (e) => {
    isDown = true;
    container.style.cursor = 'grabbing';
    startX = e.pageX - container.offsetLeft;
    scrollLeft = container.scrollLeft;
  });

  container.addEventListener('mouseleave', () => {
    isDown = false;
    container.style.cursor = 'grab';
  });

  container.addEventListener('mouseup', () => {
    isDown = false;
    container.style.cursor = 'grab';
  });

  container.addEventListener('mousemove', (e) => {
    if (!isDown) return;
    e.preventDefault();
    const x = e.pageX - container.offsetLeft;
    const walk = (x - startX) * 1.5;
    container.scrollLeft = scrollLeft - walk;
  });
}

// Usage
document.querySelectorAll('.nt-product-strip').forEach(initDragScroll);
```

---

## Number Counter Animation

For spec values that count up when scrolled into view.

```javascript
function initCounters() {
  const counters = document.querySelectorAll('[data-count]');

  const observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        const el = entry.target;
        const target = parseFloat(el.dataset.count);
        const suffix = el.dataset.countSuffix || '';
        const duration = 1200;
        const start = performance.now();

        function update(now) {
          const elapsed = now - start;
          const progress = Math.min(elapsed / duration, 1);
          // Ease out cubic
          const eased = 1 - Math.pow(1 - progress, 3);
          const current = (target * eased).toFixed(
            target % 1 !== 0 ? 1 : 0
          );
          el.textContent = current + suffix;

          if (progress < 1) requestAnimationFrame(update);
        }

        requestAnimationFrame(update);
        observer.unobserve(el);
      }
    });
  }, { threshold: 0.5 });

  counters.forEach(el => observer.observe(el));
}
```

Usage:
```html
<span class="nt-spec-card__value" data-count="50" data-count-suffix=" MP">0 MP</span>
<span class="nt-spec-card__value" data-count="5000" data-count-suffix=" mAh">0 mAh</span>
<span class="nt-spec-card__value" data-count="6.7" data-count-suffix='"'>0"</span>
```

---

## Mobile Menu Toggle

```javascript
function initMobileMenu() {
  const toggle = document.querySelector('.nt-nav__menu-toggle');
  const overlay = document.querySelector('.nt-mobile-menu');

  if (!toggle || !overlay) return;

  toggle.addEventListener('click', () => {
    const isOpen = overlay.classList.contains('nt-mobile-menu--open');

    if (isOpen) {
      overlay.classList.remove('nt-mobile-menu--open');
      document.body.style.overflow = '';
    } else {
      overlay.classList.add('nt-mobile-menu--open');
      document.body.style.overflow = 'hidden';
    }
  });
}
```

```css
.nt-mobile-menu {
  position: fixed;
  inset: 0;
  background: var(--nt-bg-primary);
  z-index: 99;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  gap: var(--nt-space-xl);
  opacity: 0;
  pointer-events: none;
  transition: opacity 300ms ease;
}

.nt-mobile-menu--open {
  opacity: 1;
  pointer-events: all;
}

.nt-mobile-menu a {
  font-size: clamp(1.5rem, 5vw, 2.5rem);
  font-weight: 500;
  letter-spacing: -0.02em;
  opacity: 0;
  transform: translateY(20px);
  transition: opacity 400ms ease, transform 400ms ease;
}

.nt-mobile-menu--open a {
  opacity: 1;
  transform: translateY(0);
}

.nt-mobile-menu--open a:nth-child(1) { transition-delay: 100ms; }
.nt-mobile-menu--open a:nth-child(2) { transition-delay: 150ms; }
.nt-mobile-menu--open a:nth-child(3) { transition-delay: 200ms; }
.nt-mobile-menu--open a:nth-child(4) { transition-delay: 250ms; }
.nt-mobile-menu--open a:nth-child(5) { transition-delay: 300ms; }
```

---

## Keyboard Accessibility

```css
/* Focus visible for keyboard navigation */
.nt-btn:focus-visible,
.nt-nav__link:focus-visible,
.nt-product-card:focus-visible {
  outline: 2px solid var(--nt-text-primary);
  outline-offset: 2px;
}

.nt-dark .nt-btn:focus-visible,
.nt-dark .nt-nav__link:focus-visible {
  outline-color: var(--nt-text-inverse);
}

/* Skip link */
.nt-skip-link {
  position: absolute;
  top: -40px;
  left: 0;
  background: var(--nt-text-primary);
  color: var(--nt-bg-primary);
  padding: 8px 16px;
  z-index: 300;
  font-size: 14px;
  transition: top 200ms ease;
}
.nt-skip-link:focus { top: 0; }
```

---

## Reduced Motion

```css
@media (prefers-reduced-motion: reduce) {
  [data-reveal] {
    opacity: 1;
    transform: none;
    transition: none;
  }

  [data-reveal-stagger] > * {
    opacity: 1;
    transform: none;
    transition: none;
  }

  .nt-hero__scroll-line { animation: none; opacity: 0.6; }
  .nt-dot-loader span { animation: none; background: var(--nt-dot-active); }

  .nt-product-card,
  .nt-product-card__image img {
    transition: none;
  }
}
```
