# Strava Year in Sport UI — Interactions & Animation Specs

## Core Principle: Scroll-Driven Celebration

The page is a narrative that unfolds as you scroll. Each section reveals its data with purpose — numbers count up, bars fill, rings complete. The animation IS the content. Without motion, the page feels incomplete.

---

## Scroll Reveal System

### IntersectionObserver Setup
```javascript
const observer = new IntersectionObserver((entries) => {
  entries.forEach(entry => {
    if (entry.isIntersecting) {
      entry.target.classList.add('yis-revealed');
      observer.unobserve(entry.target);
    }
  });
}, {
  threshold: 0.2,
  rootMargin: '0px 0px -50px 0px'
});

document.querySelectorAll('.yis-reveal').forEach(el => observer.observe(el));
```

### Reveal Animation
```css
.yis-reveal {
  opacity: 0;
  transform: translateY(40px);
  transition: opacity 0.8s cubic-bezier(0.25, 0.1, 0.25, 1.0),
              transform 0.8s cubic-bezier(0.25, 0.1, 0.25, 1.0);
}

.yis-revealed {
  opacity: 1;
  transform: translateY(0);
}

/* Stagger children */
.yis-reveal-stagger > * {
  opacity: 0;
  transform: translateY(30px);
  transition: opacity 0.6s cubic-bezier(0.25, 0.1, 0.25, 1.0),
              transform 0.6s cubic-bezier(0.25, 0.1, 0.25, 1.0);
}

.yis-reveal-stagger.yis-revealed > *:nth-child(1) { transition-delay: 0ms; opacity: 1; transform: translateY(0); }
.yis-reveal-stagger.yis-revealed > *:nth-child(2) { transition-delay: 100ms; opacity: 1; transform: translateY(0); }
.yis-reveal-stagger.yis-revealed > *:nth-child(3) { transition-delay: 200ms; opacity: 1; transform: translateY(0); }
.yis-reveal-stagger.yis-revealed > *:nth-child(4) { transition-delay: 300ms; opacity: 1; transform: translateY(0); }
```

---

## Stat Counter Animation

```javascript
function animateCounter(el) {
  const target = parseInt(el.dataset.countTo);
  const suffix = el.dataset.countSuffix || '';
  const duration = 2000;
  const start = performance.now();

  function update(now) {
    const elapsed = now - start;
    const progress = Math.min(elapsed / duration, 1);
    // Ease out cubic
    const eased = 1 - Math.pow(1 - progress, 3);
    const current = Math.round(target * eased);

    if (target >= 1000000) {
      el.textContent = (current / 1000000).toFixed(1) + 'M' + suffix;
    } else if (target >= 1000) {
      el.textContent = Math.round(current / 1000) + 'K' + suffix;
    } else {
      el.textContent = current + suffix;
    }

    if (progress < 1) requestAnimationFrame(update);
  }

  requestAnimationFrame(update);
}
```

Duration: 2000ms with ease-out cubic. Numbers format with K/M suffixes.

---

## Progress Ring Animation

```javascript
function animateRing(el) {
  const fill = el.querySelector('.yis-ring__fill');
  const value = parseFloat(el.style.getPropertyValue('--ring-value')) / 100;
  const circumference = 2 * Math.PI * 44; // r=44
  fill.style.strokeDasharray = circumference;
  fill.style.strokeDashoffset = circumference * (1 - value);
}
```

Triggered on scroll entry. Duration handled by CSS transition: 1.2s.

---

## Bar Fill Animation

```css
.yis-bar__fill {
  width: 0;
  transition: width 1s cubic-bezier(0.25, 0.1, 0.25, 1.0);
}

.yis-revealed .yis-bar__fill {
  /* width set via inline style */
}
```

Bars start at 0 width and animate to their target on reveal.

---

## Color Strip Slide-In

```css
.yis-strips div {
  transform: scaleX(0);
  transform-origin: left;
  transition: transform 0.6s cubic-bezier(0.25, 0.1, 0.25, 1.0);
}

.yis-revealed .yis-strips div:nth-child(1) { transform: scaleX(1); transition-delay: 0ms; }
.yis-revealed .yis-strips div:nth-child(2) { transform: scaleX(1); transition-delay: 80ms; }
.yis-revealed .yis-strips div:nth-child(3) { transform: scaleX(1); transition-delay: 160ms; }
.yis-revealed .yis-strips div:nth-child(4) { transform: scaleX(1); transition-delay: 240ms; }
```

---

## Hover Interactions

### Buttons
```css
.yis-btn:hover {
  transform: translateY(-1px);
  box-shadow: 0 4px 16px rgba(252,76,2,0.3);
}
```

### Cards
```css
.yis-feature-card:hover {
  transform: translateY(-4px);
  box-shadow: 0 8px 32px rgba(0,0,0,0.16);
}

.yis-stat-card:hover {
  background: rgba(255,255,255,0.1);
}
```

### Links
```css
a:hover { color: var(--yis-orange-dark); }
```

---

## Responsive Behavior

### Desktop (>1024px)
- Full 4-column stat grids
- Large stat numbers (hero: 160px)
- Generous section padding (96px)
- Side padding: 48px

### Tablet (769px–1024px)
- 2-column grids
- Reduced stat sizes
- Section padding: 64px
- Side padding: 32px

### Mobile (≤768px)
- Single column
- Stat numbers scale down but stay bold
- Section padding: 48px
- Side padding: 24px
- Nav collapses to hamburger
- Stat cards stack vertically

---

## Page Narrative Structure

The Year in Sport follows a story arc:

1. **Opening** (Hero) — The big headline number. Sets the scale.
2. **Context** (Light panel) — What the data means. Brief narrative.
3. **Building** (Navy panel) — Key metrics that build the case.
4. **Highlight** (Orange panel) — The crown jewel stat. Maximum impact.
5. **Depth** (Light/Navy alternating) — Detailed sections with cards, bars, rings.
6. **Climax** (Olive/Dark panel) — The most impressive data point.
7. **Resolution** (CTA) — What to do next. Celebratory tone.
8. **Footer** (Dark gradient) — Links and legal.

---

## Reduced Motion

```css
@media (prefers-reduced-motion: reduce) {
  .yis-reveal {
    opacity: 1;
    transform: none;
    transition: none;
  }
  .yis-reveal-stagger > * {
    opacity: 1;
    transform: none;
    transition: none;
  }
  .yis-bar__fill { transition: none; }
  .yis-ring__fill { transition: none; }
  .yis-strips div { transform: scaleX(1); transition: none; }
}
```

---

## What NOT to Animate

- No parallax on text (only subtle on backgrounds if any)
- No horizontal sliding panels
- No 3D transforms or perspective
- No infinite loops or pulsing
- No cursor effects
- No page transition animations
- No typing/typewriter effects
- Keep it to: reveal, count, fill, slide-in. That's the vocabulary.
