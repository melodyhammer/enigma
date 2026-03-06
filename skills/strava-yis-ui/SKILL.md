---
name: strava-yis-ui
description: >
  Build UIs in the Strava Year in Sport design language —
  data-celebration aesthetic with bold stat counters, circle motifs,
  color-strip panels, scroll-driven reveals, and athletic energy.
  Use when the user asks to "create a data report page", "build an annual review UI",
  "make a year-in-review page", "design a Strava-style data page",
  "create an athletic data dashboard", "build a stats celebration page",
  "make a scroll-storytelling report", "design a community data page",
  or discusses Strava aesthetics, Year in Sport styling, data-celebration design,
  stat counter UIs, circle-motif layouts, athletic data reports,
  or scroll-driven data storytelling.
version: 1.0.0
---

# Strava Year in Sport UI — Design System Skill

You are building UIs in the Strava Year in Sport design language — a bold, data-driven celebration aesthetic that treats statistics as hero content. The design language was created by Manual Creative and Hello Monday for Strava's annual community report. It combines athletic energy with editorial precision: massive stat counters, circle motifs representing community unity, layered color-strip panels, and scroll-triggered reveals that let data unfold like a story. Dark backgrounds make numbers pop. The system is sporty, confident, and joyful.

**Reference:** https://www.strava.com/yis-community-2022

---

## Core Philosophy

The Strava Year in Sport design language is built on 6 principles:

### 1. Data as Hero
Statistics are the primary visual element — not illustrations, not photography. Numbers are rendered at massive display scale, often filling the viewport. The design grows organically from the data. Every section exists to celebrate a number.

### 2. The Circle Is Sacred
The circle represents community, unity, and the athlete's journey (loops, laps, cycles). Circles appear as: progress rings, background decorative elements, stat containers, chart shapes, and section transitions. They're the geometric DNA of the system.

### 3. Color-Strip Energy
Inspired by race bibs and athletic apparel, the palette uses bold color-strip panels — full-width sections that alternate between dark navy, Strava orange, olive green, and warm neutrals. Each section gets its own color identity. The effect is layered, energetic, kinetic.

### 4. Athletic Typography
Type is bold, confident, and scaled for impact. Display numbers use extreme weights (800-900) at massive sizes. Body text is clean and readable (Inter). The contrast between giant stat numbers and small descriptor labels creates dramatic visual hierarchy.

### 5. Scroll-Driven Narrative
Content unfolds chapter-by-chapter as you scroll. Each section reveals like turning a page. Counter animations bring stats to life. The page structure follows a story arc: opening → building → climax → resolution.

### 6. Dots, Lines, Strips
The graphic system is built from simple modular elements: dots, lines, color strips, and circles. These primitives compose into data visualizations, decorative patterns, and section dividers. The simplicity allows animation to be the star.

---

## Color Tokens

```css
:root {
  /* ========== BRAND ========== */
  --yis-orange: #FC4C02;                  /* Strava signature orange */
  --yis-orange-light: #FF6B2B;            /* Lighter orange for gradients */
  --yis-orange-dark: #E04400;             /* Deeper orange */

  /* ========== DARK PANELS ========== */
  --yis-navy: #1D1D3B;                    /* Deep navy — primary dark bg */
  --yis-navy-light: #2A2A52;              /* Lighter navy for cards */
  --yis-charcoal: #1A1A2E;               /* Near-black dark bg */
  --yis-dark: #111111;                    /* Deepest dark */

  /* ========== ATHLETIC ACCENTS ========== */
  --yis-olive: #4A6741;                   /* Olive green — nature/endurance */
  --yis-olive-light: #5C8A50;             /* Lighter olive */
  --yis-teal: #1B8A8A;                    /* Teal — water sports accent */
  --yis-coral: #FF6B6B;                   /* Warm coral — highlights */
  --yis-gold: #FFB800;                    /* Gold — achievement/celebration */

  /* ========== NEUTRALS ========== */
  --yis-white: #FFFFFF;
  --yis-off-white: #F7F7F5;              /* Warm off-white sections */
  --yis-light-gray: #EFEFEF;
  --yis-mid-gray: #B0B0B0;
  --yis-dark-gray: #666666;

  /* ========== TEXT ========== */
  --yis-text-dark: #1A1A1A;              /* Text on light backgrounds */
  --yis-text-light: #FFFFFF;             /* Text on dark backgrounds */
  --yis-text-muted: rgba(255,255,255,0.6); /* Muted text on dark */
  --yis-text-muted-dark: #888888;        /* Muted text on light */
}
```

---

## Typography

```css
:root {
  /* Display/Marketing — Boathouse or bold sans fallback */
  --yis-font-display: "Boathouse", "Inter", "Helvetica Neue", Arial, sans-serif;

  /* UI/Body — Inter */
  --yis-font-body: "Inter", -apple-system, "Helvetica Neue", Arial, sans-serif;

  /* Monospace — for code/data elements */
  --yis-font-mono: "SF Mono", "Menlo", "Courier New", monospace;
}
```

| Element | Font | Size | Weight | Style |
|---------|------|------|--------|-------|
| Hero stat number | Display | 96–160px | 900 | Uppercase, tight tracking |
| Section stat number | Display | 64–96px | 800 | Tight tracking, line-height 1.0 |
| Stat label | Body | 14–16px | 600 | Uppercase, tracking 0.1em |
| Section heading | Display | 36–56px | 700 | Title case or uppercase |
| Sub-heading | Body | 20–28px | 600 | Sentence case |
| Body text | Body | 16–18px | 400 | Sentence case, line-height 1.6 |
| Caption/metadata | Body | 13–14px | 400 | Color: muted |
| Navigation | Body | 14px | 600 | Uppercase, tracking 0.04em |
| Button | Body | 14–16px | 700 | Uppercase, tracking 0.04em |
| Small data label | Body | 11–12px | 600 | Uppercase, tracking 0.08em |

**Key type rules:**
- Stat numbers are MASSIVE — the bigger the number, the bigger the type
- Display weights 700-900 for all headings and stats
- Body weight 400 for readable paragraphs
- Labels always uppercase with generous tracking
- Line-height for stat numbers: 0.9–1.0 (numbers touch)
- Line-height for body: 1.6 (generous reading)

---

## Spacing System

Base unit: 8px. Generous vertical rhythm — sections need room to breathe.

| Token | Value | Use |
|-------|-------|-----|
| --yis-space-xs | 4px | Tight inline gaps |
| --yis-space-sm | 8px | Label gaps, icon spacing |
| --yis-space-md | 16px | Card padding, list gaps |
| --yis-space-lg | 24px | Between components |
| --yis-space-xl | 32px | Section internal spacing |
| --yis-space-2xl | 48px | Between major blocks |
| --yis-space-3xl | 64px | Section padding (mobile) |
| --yis-space-4xl | 96px | Section padding (desktop) |
| --yis-space-5xl | 128px | Hero/display sections |

---

## Layout System

### Container
- Max-width: 1200px centered
- Side padding: 48px desktop → 24px mobile
- Content sections: full-width color panels, content constrained

### Page Structure
```
┌──────────────────────────────────────┐
│ ████ DARK HERO — giant stat  ████████│ ← full-width dark, massive number
│                                      │
│──────────────────────────────────────│
│                                      │
│  ○ STAT CARD GRID                   │ ← 2-4 column grid of stat circles
│  ○  ○  ○  ○                         │
│                                      │
│██████████████████████████████████████│
│██ ORANGE PANEL — key stat  ██████████│ ← full-width orange
│██████████████████████████████████████│
│                                      │
│  NARRATIVE SECTION                  │ ← light bg, body text
│  context paragraph                  │
│                                      │
│██████████████████████████████████████│
│██ NAVY PANEL — data viz    ██████████│ ← full-width navy
│██ [chart / counter / viz]  ██████████│
│██████████████████████████████████████│
│                                      │
│  GRID SECTION                       │ ← 2-3 col stat cards
│  ┌────┐ ┌────┐ ┌────┐              │
│  │ ## │ │ ## │ │ ## │              │
│  └────┘ └────┘ └────┘              │
│                                      │
│██████████████████████████████████████│
│██ OLIVE PANEL — CTA        ██████████│ ← full-width olive/dark
│██████████████████████████████████████│
│                                      │
│  FOOTER                             │
└──────────────────────────────────────┘
```

---

## Component Patterns

### Stat Counter (Hero)
The signature element. A massive number with small descriptor.
- Number: 800-900 weight, 80-160px, white on dark (or dark on light)
- Label: 600 weight, 12-14px, uppercase, tracking 0.1em, muted color
- Optional: unit suffix (M, B, %, hrs) at ~60% of number size
- Circle container optional: 2-4px border ring around stat

### Color Panel Section
Full-width colored background panels that alternate:
- Dark navy (#1D1D3B) — primary data sections
- Strava orange (#FC4C02) — key highlight moments
- Olive green (#4A6741) — nature/endurance sections
- Off-white (#F7F7F5) — breathing room, context text
- Charcoal (#1A1A2E) — footer, dense data

### Stat Card
A single data point in a grid:
- Background: slightly lighter than parent panel (or transparent + border)
- Number: 700-800 weight, 36-56px
- Label: 600 weight, 12px, uppercase
- Optional circle/ring decorative element
- Border-radius: 16-24px (rounded, friendly)

### Progress Ring
SVG circle that fills to represent a percentage:
- Stroke-width: 4-8px
- Track: rgba(255,255,255,0.15) on dark
- Fill: --yis-orange or accent color
- Number centered inside ring
- Animate on scroll entry

### Data Bar
Horizontal or vertical bars for comparisons:
- Border-radius: 4-8px on ends (pill-shaped)
- Fill: orange gradient or accent color
- Track: rgba(255,255,255,0.1)
- Label above or below
- Animate width/height on scroll

### Dot Pattern
Decorative grid of dots as background texture:
- Dots: 4-6px circles
- Color: rgba(255,255,255,0.08) on dark
- Grid: 24-32px spacing
- Used as subtle background texture in panels

### Color Strip Divider
Thin horizontal bands of color between sections:
- 4-8px tall strips
- Alternating: orange, olive, teal, gold
- 3-5 strips stacked with 2px gaps
- Used as section transitions

### Buttons
```
Primary:    #FC4C02 bg, white text, border-radius 100px (pill)
            Hover: darken 10%
            Padding: 14px 32px

Secondary:  Transparent bg, white border (2px), white text
            Hover: white bg, dark text
            Border-radius: 100px

Ghost:      Transparent, text-underline
            Hover: opacity 0.7
```

### Quote/Testimonial
- Large quote mark decorative element (or circle)
- Quote text: 24-32px, weight 500, italic optional
- Attribution: 14px, uppercase, muted
- Background: dark panel with accent border-left or circle

---

## Animation & Interaction

### Core Animations
1. **Stat Counter** — Numbers count up from 0 on scroll entry (IntersectionObserver)
2. **Progress Ring** — SVG stroke-dashoffset animates on entry
3. **Panel Reveal** — Sections fade-up (translateY: 40px → 0, opacity: 0 → 1)
4. **Color Strip** — Strips slide in from left/right on entry
5. **Dot Pattern** — Subtle parallax movement on scroll

### Scroll-Driven Storytelling
- Sections trigger on ~20% viewport entry
- Stagger: child elements animate 100-200ms apart
- Duration: 600-900ms
- Easing: cubic-bezier(0.25, 0.1, 0.25, 1.0) — smooth decel

### Hover States
- Buttons: background darken, subtle scale(1.02)
- Cards: subtle lift (translateY: -4px), shadow increase
- Links: color shift to orange, underline

### Transitions
```css
transition: all 300ms cubic-bezier(0.25, 0.1, 0.25, 1.0);
```

### Reduced Motion
```css
@media (prefers-reduced-motion: reduce) {
  *, *::before, *::after {
    animation-duration: 0.01ms !important;
    transition-duration: 0.01ms !important;
  }
}
```

---

## Gradients

```css
/* Orange gradient — hero moments */
background: linear-gradient(135deg, #FC4C02 0%, #FF6B2B 100%);

/* Navy gradient — deep data sections */
background: linear-gradient(180deg, #1D1D3B 0%, #1A1A2E 100%);

/* Olive gradient — nature sections */
background: linear-gradient(135deg, #4A6741 0%, #5C8A50 100%);

/* Dark to darker — footer */
background: linear-gradient(180deg, #1A1A2E 0%, #111111 100%);

/* Subtle orange glow — accent */
background: radial-gradient(ellipse at center, rgba(252,76,2,0.15) 0%, transparent 70%);
```

---

## Anti-Patterns (Never Do These)

1. **No thin/light font weights for stats** — stats are BOLD (700-900)
2. **No flat gray backgrounds** — panels are rich colors: navy, orange, olive, charcoal
3. **No sharp corners on cards/buttons** — always rounded (16-24px cards, pill buttons)
4. **No static stat numbers** — numbers should count up on scroll
5. **No tiny stats** — if a number is important, make it BIG (64px minimum)
6. **No monochrome palette** — the color-strip energy requires 3+ panel colors
7. **No dense body text without breathing room** — generous spacing between everything
8. **No decorative illustrations** — data visualizations only (bars, rings, counters)
9. **No horizontal rules as primary dividers** — use color panels and strips instead
10. **No serif fonts** — clean sans-serif only, sporty and modern
11. **No muted/corporate tone in copy** — voice is energetic, celebratory, athletic
12. **No small hero sections** — hero fills viewport or nearly so

---

## File References

- **Color tokens, typography, spacing:** Defined above in this file
- **Component HTML/CSS patterns:** `references/component-inventory.md`
- **Design system tokens (full CSS):** `references/design-system.md`
- **Interaction & page-structure specs:** `references/interactions.md`
