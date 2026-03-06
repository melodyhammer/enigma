---
name: teenage-engineering-ui
description: >
  Build UIs in the Teenage Engineering design language — ultra-clean, industrial-Scandinavian
  product design with mathematical grid precision, thin sans-serif typography, monochrome
  palettes, and form-follows-function minimalism.
  Use when the user asks to "create a TE-style page", "build a teenage engineering layout",
  "make an industrial product page", "design a Scandinavian-minimal interface",
  "create a hardware product showcase", "build a clean grid layout",
  "make a Dieter Rams style page", "design a Braun-inspired interface",
  "create a precision-grid product page", "build a monochrome product site",
  or discusses teenage engineering aesthetics, industrial-Scandinavian design,
  Univers typography, mathematical grid systems, or hardware-product minimalism.
  Also triggers when the user references "TE style", "pocket operator aesthetic",
  "Swedish industrial design", "Univers font layout", "calculated grid system",
  "thin sans-serif product page", or "form-follows-function web design".
version: 1.0.0
---

# Teenage Engineering UI — Design System Skill

You are building UIs in the Teenage Engineering design language — a design philosophy rooted in Swedish industrial design, Dieter Rams functionalism, and mathematical precision. Every element exists because it must. Nothing is decorative. The grid is calculated to sub-pixel accuracy. Typography is thin, light, and measured. The product IS the hero — the page is merely the stage.

**Reference:** https://teenage.engineering/products/ep-133

---

## Core Philosophy

Teenage Engineering's design language is built on 6 principles:

### 1. Mathematical Grid Precision
The layout is not "responsive" in the sloppy modern sense — it is **calculated**. Every dimension derives from the viewport width through precise mathematical relationships. Column widths, gutters, margins, font sizes — all computed from a single root value. The grid is a 12-column system where every measurement is a fraction of the whole. Nothing is approximate.

### 2. Thin Is Beautiful
Typography is almost impossibly thin. The primary font (Univers) is used in its lightest weights — Light and Thin. This creates a sense of precision engineering, like the engraved markings on a machined aluminum surface. Bold text barely exists. Weight communicates hierarchy through size, not thickness.

### 3. Monochrome + Photography
The interface itself is purely monochrome: near-black text on off-white/light gray. Color only enters through product photography and the occasional status badge. The restraint makes the products pop — they're the only colorful thing on the page.

### 4. Product as Hero
Every layout decision serves the product. Images are large, clean, and precisely positioned. Text is secondary — brief, factual, and positioned to complement, never compete with, the product image. Specs are presented as clean lists. Marketing language is minimal.

### 5. Flat, Not Elevated
No shadows, no gradients, no depth effects. Everything sits on the same plane. Visual hierarchy comes from size, weight, and position — not z-axis tricks. This mirrors TE's physical products which celebrate flat panel construction.

### 6. Content Density Through Precision
Pages can be long and content-rich, but never feel cluttered because every element is precisely placed on the grid. Generous whitespace between sections, tight internal spacing within components. The rhythm is metronomic.

---

## Color Tokens

```css
:root {
  /* ========== SURFACES ========== */
  --te-bg: #F5F5F5;                     /* Primary background — warm light gray */
  --te-bg-white: #F9FAF9;              /* Slightly warmer white — product pages */
  --te-bg-pure: #FFFFFF;               /* Pure white — cards, inputs */
  --te-bg-dark: #0F0E12;               /* Near-black — inverted sections */
  --te-bg-mid: #E5E5E5;               /* Mid gray — subtle section breaks */

  /* ========== TEXT ========== */
  --te-text: #0F0E12;                   /* Primary text — warm near-black */
  --te-text-secondary: #6B6B6B;        /* Secondary/muted */
  --te-text-tertiary: #999999;         /* Captions, disabled */
  --te-text-inverse: #F5F5F5;          /* Text on dark backgrounds */
  --te-text-inverse-muted: #999999;    /* Muted text on dark */

  /* ========== BORDERS ========== */
  --te-border: #D5D5D5;               /* Default border/divider */
  --te-border-light: #E8E8E8;         /* Subtle divider */
  --te-border-dark: #333333;           /* Borders on dark surfaces */

  /* ========== STATUS ========== */
  --te-new: #0F0E12;                   /* "new" badge — same as text, understated */
  --te-sale: #CC0000;                  /* "reduced price" — the only red */
  --te-limited: #0F0E12;              /* "limited run" — same as text */

  /* ========== FUNCTIONAL ========== */
  --te-link: #0F0E12;                  /* Links — same as text */
  --te-link-hover: #6B6B6B;           /* Link hover — dims, doesn't color */
  --te-focus: #0F0E12;                /* Focus ring */
}
```

---

## Typography

```css
:root {
  /* Font stack — Univers in its thinnest weights */
  --te-font: "Univers Next", "Univers", "Helvetica Neue Light",
             "Helvetica Neue", "Arial", -apple-system, sans-serif;
  --te-font-thin: "Univers Next W02 Thin", "Univers Thin",
                  "Helvetica Neue Thin", sans-serif;

  /* Fluid sizing — everything derives from viewport width */
  --te-client-width: 100vw;
  --te-text-xs: calc(var(--te-client-width) * 0.00918);    /* ~9px at 980 */
  --te-text-sm: calc(var(--te-client-width) * 0.01327);    /* ~13px at 980 */
  --te-text-base: calc(var(--te-client-width) * 0.01837);  /* ~18px at 980 */
  --te-text-lg: calc(var(--te-client-width) * 0.02755);    /* ~27px at 980 */
  --te-text-xl: calc(var(--te-client-width) * 0.03673);    /* ~36px at 980 */
  --te-text-2xl: calc(var(--te-client-width) * 0.05);      /* ~49px at 980 */
  --te-text-display: calc(var(--te-client-width) * 0.07);  /* ~69px at 980 */
}
```

| Element | Size Token | Weight | Style |
|---------|-----------|--------|-------|
| Display/Hero | --te-text-display | 200 (Thin) | Uppercase or sentence, tight tracking |
| Page title | --te-text-2xl | 200 | Uppercase, letter-spacing -0.01em |
| Section heading | --te-text-xl | 300 (Light) | Uppercase, letter-spacing 0em |
| Sub-heading | --te-text-lg | 300 | Sentence case |
| Body | --te-text-base | 300 | Sentence case, line-height 1.2× |
| Body small | --te-text-sm | 300 | Sentence case, line-height 1.22× |
| Caption/meta | --te-text-xs | 300 | Sentence/uppercase |
| Product name | --te-text-sm–base | 300 | Uppercase for model numbers |
| Price | --te-text-base | 300 | Standard numerals |
| Nav links | --te-text-sm | 300 | Sentence case |
| Button | --te-text-sm | 300 | Sentence case or lowercase |

**Key type rules:**
- Font weight is ALWAYS 200 (Thin) or 300 (Light) — never regular (400), never bold
- The only "bold" is using a larger size, not a heavier weight
- Line-height is extremely tight: 1.02× to 1.22× (not the 1.5–1.6 of normal web)
- Letter-spacing: neutral to slightly negative for display sizes
- Product model numbers use ALL CAPS with en-dashes: EP–133, OP–1, PO–33
- Body copy is minimal — 1-2 sentences, factual, no marketing fluff
- Fluid sizing means text scales perfectly with viewport — no breakpoint jumps

---

## Grid System

The grid is the foundation. Everything is mathematical.

```css
:root {
  --te-columns: 12;
  --te-max-width: 980px;
  --te-margin: 4.59%;          /* Side margins as % of viewport */
  --te-gutter: 1.02%;          /* Gutter between columns */
  --te-column-width: 6.63%;    /* Single column width */
  --te-baseline: 1.02%;        /* Baseline grid unit */
}
```

### Column Classes
```css
.c1  { width: calc(1 * var(--te-column-width) + 0 * var(--te-gutter)); }
.c2  { width: calc(2 * var(--te-column-width) + 1 * var(--te-gutter)); }
.c3  { width: calc(3 * var(--te-column-width) + 2 * var(--te-gutter)); }
.c4  { width: calc(4 * var(--te-column-width) + 3 * var(--te-gutter)); }
.c6  { width: calc(6 * var(--te-column-width) + 5 * var(--te-gutter)); }
.c8  { width: calc(8 * var(--te-column-width) + 7 * var(--te-gutter)); }
.c12 { width: calc(12 * var(--te-column-width) + 11 * var(--te-gutter)); }
```

### Simplified Implementation
For practical HTML/CSS, use this equivalent:
```css
.te-container {
  max-width: 980px;
  margin: 0 auto;
  padding: 0 4.5%;
}

.te-grid {
  display: grid;
  grid-template-columns: repeat(12, 1fr);
  gap: 10px;
}
```

---

## Spacing

All spacing derives from the baseline grid unit (approximately 10px at 980px viewport).

| Token | Value | Use |
|-------|-------|-----|
| --te-space-unit | 10px | Base grid unit |
| --te-space-xs | 5px | Tight gaps |
| --te-space-sm | 10px | Gutter, inline spacing |
| --te-space-md | 20px | Component padding |
| --te-space-lg | 40px | Section internal |
| --te-space-xl | 60px | Between major sections |
| --te-space-2xl | 80px | Page-level rhythm |
| --te-space-3xl | 120px | Hero spacing |

---

## Component Patterns

### Navigation
- Minimal top bar: logo left, links right
- Logo: "teenage engineering" in thin lowercase type — or abbreviated "te"
- Links: thin, lowercase, sentence case, separated by generous spacing
- Cart indicator: "in cart (2)" style counter
- "Store" link prominent
- No background color, no border — floats on the page background
- On mobile: collapses to minimal

### Product Hero
- Full-width or near-full-width product photography
- Product image dominates — 60-80% of viewport
- Model number in thin uppercase: EP–133 K.O.II
- Brief tagline: one line, thin, understated
- "buy now" link — not even styled as a button, just a text link
- Price displayed matter-of-factly: "$329"

### Product Cards (Grid)
```
┌─────────────────────┐
│                     │
│    [product image]  │   128×128 or larger
│                     │
├─────────────────────┤
│ product name        │   thin, sm size
│ add to cart         │   text link, not button
└─────────────────────┘
```
- No border, no shadow, no card outline
- Image sits directly on the background
- Text below, left-aligned
- Minimal: name + action, nothing else
- Grid: typically 3-4 across on desktop

### Feature List
- Simple vertical list
- Each item: small icon (optional) + 1-2 line description
- Separated by thin hairline borders
- All text in thin weight
- Technical specs in monospace or same thin sans-serif
- No bullet points — just clean lines of text

### Spec Table
```
speaker          2W
battery          12hrs
connectivity     USB-C, bluetooth 5.0
sample rate      44.1kHz / 16-bit
dimensions       128 × 78 × 40mm
weight           340g
```
- Two columns: label (left-aligned) + value (right or left)
- Thin hairline separators between rows
- All same size, same weight — no emphasis
- Clean tabular layout, no header row styling

### Buttons / CTAs
Teenage Engineering barely uses "buttons" in the traditional sense:
```
buy now             → text link, thin, sometimes underlined
add to cart         → text link
learn more          → text link
worldwide delivery  → informational text link
```
When a button IS used:
- Minimal: thin 1px border, thin text, generous padding
- No fill color, no border-radius
- Hover: text dims or subtle underline
- The CTA is ALWAYS understated — the product sells itself

### Status Badges
```
new                 → plain text prefix, same weight as everything else
limited run         → plain text, slightly emphasized
reduced price       → text in red (--te-sale), the only color
```
Not pills, not colored backgrounds — just text labels.

### Section Dividers
- Thin 1px lines in --te-border color
- Full container width
- Used between major content sections
- Sometimes just whitespace — no line needed if spacing is sufficient

### Images
- Product photography: clean, studio-lit, high-contrast
- Always on white or light gray background
- No border-radius, no shadows, no frames
- WebP format, high resolution
- Sizes: 128px thumbnails, up to full-width heroes
- Object-fit: contain (never crop the product)

---

## Animation & Interaction

### Extremely Minimal
- **No scroll animations** — content is static
- **No parallax** — flat is flat
- **No loading animations** — page renders
- **No hover transforms** — no scale, no lift

### Allowed:
- Link hover: opacity change (1.0 → 0.6) or color shift to --te-link-hover
- Transition: `opacity 200ms ease` — that's it
- Cart counter updates
- Smooth scrolling (native)

The interaction philosophy: if you need animation to make your design work, your design doesn't work.

---

## Dark Sections

Rare, but when used (e.g., product launch announcements):
- Background: --te-bg-dark (#0F0E12)
- Text: --te-text-inverse (#F5F5F5)
- Same thin typography, same grid
- Product photography provides the only visual interest
- Borders: --te-border-dark (#333333)

---

## Content Voice

Teenage Engineering's copy is distinctive:
- **Minimal, almost terse** — "sampler. sequencer. drum machine."
- **Lowercase preference** — "buy now" not "BUY NOW" or "Buy Now"
- **Technical precision** — "44.1kHz / 16-bit" not "high-quality audio"
- **No superlatives** — never "best", "amazing", "revolutionary"
- **Model numbers are sacred** — always with en-dash: EP–133, not EP-133
- **Period-terminated lists** — features end with periods
- **No exclamation marks** — ever
- **Price is factual** — "$329" or "only $329", no "starting at" drama

---

## Anti-Patterns (Never Do These)

1. **No bold text** — weight 200-300 only, hierarchy through size
2. **No border-radius** — everything is squared
3. **No shadows** — flat, always
4. **No gradients** — flat colors only
5. **No colored backgrounds** — only grays, white, near-black
6. **No hover animations** — opacity change is the maximum
7. **No decorative elements** — no icons, patterns, or ornaments
8. **No marketing language** — factual only
9. **No card styles** — no outlined/shadowed containers
10. **No heavy fonts** — never above 300 weight
11. **No large buttons** — CTAs are text links
12. **No emoji** — ever

---

## File References

- **Color tokens, typography, spacing:** Defined above in this file
- **Component HTML/CSS patterns:** `references/component-inventory.md`
- **Design system tokens (full CSS):** `references/design-system.md`
- **Grid system & layout specs:** `references/interactions.md`
