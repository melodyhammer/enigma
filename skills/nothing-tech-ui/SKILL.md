---
name: nothing-tech-ui
description: >
  Build UIs in the Nothing Tech design language — ultra-minimal, dot-matrix inspired,
  high-contrast black and white with transparent/skeletal aesthetics.
  Use when the user asks to "create a Nothing style page", "build a Nothing Tech UI",
  "make a minimalist tech landing page", "design a dot-matrix interface",
  "create a glyph-style layout", "build a transparent UI", "make a brutalist product page",
  "design a Swiss-grid tech page", "create a Nothing-inspired component",
  "build a monochrome product showcase", or discusses Nothing Tech aesthetics,
  dot-matrix patterns, glyph interfaces, skeletal/transparent design, or
  ultra-minimalist tech product pages. Also triggers when the user references
  "Nothing Phone style", "dot grid pattern", "glyph light interface",
  "stripped-back design", or "transparency-first UI".
version: 1.0.0
---

# Nothing Tech UI — Design System Skill

You are building UIs in the Nothing Tech design language — a radical approach to consumer tech aesthetics that strips design down to its structural skeleton. Inspired by transparency, dot-matrix displays, and Swiss typographic tradition, Nothing's visual identity is defined by what it *removes* rather than what it adds.

**Reference:** https://us.nothing.tech/

Before writing any code, consult the reference files in `references/` for exact visual patterns, component specs, and interaction details.

---

## Core Philosophy

Nothing's design language is built on 5 principles:

### 1. Transparency & Structure
Everything reveals its construction. Backgrounds show grids. Layouts expose their geometry. Components feel like X-rays of traditional UI — you see the bones. This mirrors Nothing's physical products where the phone's back panel is literally transparent.

### 2. Dot-Matrix Heritage
Nothing's signature visual element is the dot-matrix pattern — a grid of small circles that evokes LED displays, circuit boards, and early computing. This pattern appears as:
- Background textures (subtle dot grids)
- Loading states (dots illuminating in sequence)
- Decorative elements (dot clusters forming shapes)
- Typography accents (dot-matrix style numerals for callouts)

### 3. Maximum Contrast, Minimum Color
The palette is almost entirely black and white. When color appears, it's either:
- Product photography (the only "color" allowed)
- A single red accent (#D71921) used extremely sparingly for CTAs or alerts
- Functional UI states (success green, error red)

### 4. Typographic Precision
Text is the primary design element. Large, clean, tightly tracked sans-serif type does the heavy lifting. Headlines are often conversational and lowercase — "it's metal now." not "IT'S METAL NOW". Body copy is sparse and factual.

### 5. Negative Space as Feature
White space isn't empty — it's structural. Generous margins, breathing room between sections, and restrained content density create a sense of calm authority. Every pixel of space is intentional.

---

## Color Tokens

```css
:root {
  /* Surfaces */
  --nt-bg-primary: #FFFFFF;              /* Main background — pure white */
  --nt-bg-secondary: #F7F7F7;           /* Subtle card/section background */
  --nt-bg-tertiary: #F0F0F0;            /* Hover states, input backgrounds */
  --nt-bg-inverse: #000000;             /* Dark sections — pure black */
  --nt-bg-inverse-soft: #1A1A1A;        /* Slightly lifted dark surface */

  /* Text */
  --nt-text-primary: #000000;           /* Primary text on light */
  --nt-text-secondary: #666666;         /* Secondary/muted text */
  --nt-text-tertiary: #999999;          /* Captions, labels, metadata */
  --nt-text-inverse: #FFFFFF;           /* Text on dark backgrounds */
  --nt-text-inverse-muted: #AAAAAA;     /* Muted text on dark */

  /* Borders & Lines */
  --nt-border: #E5E5E5;                 /* Default border — barely there */
  --nt-border-strong: #CCCCCC;          /* Emphasized borders */
  --nt-border-inverse: #333333;         /* Borders on dark surfaces */
  --nt-divider: #F0F0F0;               /* Section dividers */

  /* Accent — used VERY sparingly */
  --nt-accent: #D71921;                 /* Nothing red — CTAs, alerts only */
  --nt-accent-hover: #B5141A;           /* Red hover state */

  /* Dot Matrix */
  --nt-dot: #E0E0E0;                    /* Dot grid on light backgrounds */
  --nt-dot-active: #000000;             /* Active/highlighted dots */
  --nt-dot-inverse: #333333;            /* Dot grid on dark backgrounds */
  --nt-dot-inverse-active: #FFFFFF;     /* Active dots on dark */

  /* Functional */
  --nt-success: #00C853;
  --nt-error: #D71921;
  --nt-warning: #FF9100;
}
```

---

## Typography

```css
:root {
  --nt-font: "Nothing Sans", "Helvetica Neue", "Arial", -apple-system, sans-serif;
  --nt-font-mono: "Nothing Mono", "SF Mono", "Courier New", monospace;
}
```

Nothing uses a proprietary sans-serif font. When unavailable, fall back to Helvetica Neue / system sans-serif. The type is always clean, geometric, and tightly controlled.

| Element | Size | Weight | Style |
|---------|------|--------|-------|
| Hero headline | 48–72px (clamp 3–4.5rem) | 500 | Sentence case, tight tracking (-0.02em) |
| Section headline | 32–48px (clamp 2–3rem) | 500 | Sentence case, -0.02em |
| Sub-headline | 20–24px | 400 | Sentence case, 0em |
| Body large | 18px | 400 | Normal case, line-height 1.6 |
| Body | 16px | 400 | Normal case, line-height 1.6 |
| Body small | 14px | 400 | Normal case, line-height 1.5 |
| Caption | 12px | 400 | Uppercase, letter-spacing 0.08em |
| Spec label | 12px | 500 | Uppercase, letter-spacing 0.05em |
| Spec value | 32–40px | 500 | Tabular numerals |
| Nav link | 14px | 500 | Uppercase, letter-spacing 0.05em |
| Button | 14px | 500 | Uppercase, letter-spacing 0.08em |

**Key type rules:**
- Headlines are conversational — lowercase sentence case, not ALL CAPS
- Periods at the end of headlines are a signature move: "it's metal now."
- Body copy is minimal — 1-2 sentences max per block
- Numbers in specs are oversized relative to their labels

---

## Spacing System

Base unit: 8px

| Token | Value | Use |
|-------|-------|-----|
| --nt-space-xs | 4px | Tight internal padding |
| --nt-space-sm | 8px | Icon gaps, tight spacing |
| --nt-space-md | 16px | Component internal padding |
| --nt-space-lg | 24px | Card padding, section gaps |
| --nt-space-xl | 32px | Between components |
| --nt-space-2xl | 48px | Section padding |
| --nt-space-3xl | 64px | Major section breaks |
| --nt-space-4xl | 96px | Hero spacing |
| --nt-space-5xl | 128px | Page-level vertical rhythm |

---

## Layout System

### Grid
- 12-column grid, max-width 1440px, centered
- Gutters: 24px (desktop), 16px (mobile)
- Side margins: 80px (desktop) → 48px (tablet) → 20px (mobile)
- Full-bleed sections break out of the grid for hero imagery

### Section Pattern
Every section follows one of these layouts:
1. **Full-bleed hero** — Edge-to-edge image/video with centered text overlay
2. **Split** — 50/50 image + text, alternating sides
3. **Centered stack** — Centered headline, centered content block
4. **Spec grid** — 2–4 column grid of specification cards
5. **Product strip** — Horizontal scroll of product cards

### Breakpoints
```css
--nt-bp-sm: 640px;
--nt-bp-md: 768px;
--nt-bp-lg: 1024px;
--nt-bp-xl: 1280px;
--nt-bp-2xl: 1440px;
```

---

## Component Patterns

### Navigation
- Fixed top bar, white background, thin bottom border
- Logo left (Nothing wordmark or dot logo), links center, icons right (search, cart, account)
- Links: uppercase, 14px, 500 weight, generous horizontal spacing
- On scroll: subtle backdrop-blur, slight shadow
- Mobile: hamburger → full-screen overlay with large stacked links
- On dark sections: inverts to white text on transparent/dark bg

### Hero Sections
- Full-viewport height (100vh or 90vh)
- Product image dominates — typically 60-80% of the frame
- Text overlay: conversational headline + one-line description + CTA button
- Text positioned bottom-left or center, never competing with product
- Subtle scroll indicator (thin line or dot) at bottom center
- Optional: background video with poster fallback

### Buttons
```
Primary:   Black bg, white text, no border-radius (0px or 2px max)
           Hover: #333 bg
           Padding: 14px 32px

Secondary: White bg, black text, 1px black border
           Hover: #F7F7F7 bg
           Padding: 14px 32px

Ghost:     Transparent bg, black text, no border
           Hover: underline
           Padding: 8px 0

Inverse:   White bg on dark sections, black text
           Hover: #E5E5E5 bg
           Padding: 14px 32px

Disabled:  #CCCCCC bg, #999 text
```
- All buttons: uppercase, 14px, 500 weight, letter-spacing 0.08em
- Minimal or ZERO border-radius — squared-off is the signature
- Transitions: background-color 200ms ease

### Product Cards
```
Container:  White bg, no border, no shadow, no border-radius
            Hover: subtle lift (translateY(-2px)) + light shadow
Image:      Aspect ratio 1:1, object-fit contain, #F7F7F7 bg
Title:      16px, 500 weight, one line, truncate
Subtitle:   14px, 400 weight, #666 color
Price:      16px, 500 weight, black
Sale price: Red accent + line-through on original
Variants:   Small color circles (16px) below title
```

### Spec Cards
```
Container:  #F7F7F7 bg (or #1A1A1A for dark variant)
            Padding: 32px
            No border-radius
Value:      36–48px, 500 weight, black (or white on dark)
Label:      12px, uppercase, #666 (or #AAA on dark)
            Letter-spacing 0.05em
Icon:       24px line icon above value (optional)
```

### Dot-Matrix Pattern
The signature decorative element:
```css
.dot-grid {
  background-image: radial-gradient(circle, var(--nt-dot) 1px, transparent 1px);
  background-size: 20px 20px;
}

.dot-grid-dense {
  background-size: 12px 12px;
}

.dot-grid-inverse {
  background-image: radial-gradient(circle, var(--nt-dot-inverse) 1px, transparent 1px);
}
```
Use sparingly — as section backgrounds, card accents, or loading placeholders.

### Image Treatment
- Product photography: clean, high-contrast, studio-lit on white or black
- Hero images: atmospheric, dramatic lighting, often showing product transparency
- All images: no border-radius, no filters, no overlays (let the photo speak)
- Lazy loading with LQIP (low quality image placeholder) blur-up

### Dividers
- Hairline: 1px solid #E5E5E5 (or #333 on dark)
- Full-width, edge-to-edge within their container
- Used between sections, not between individual items

---

## Animation & Interaction

### Scroll Reveals
- Elements fade in + slide up on scroll into view
- `opacity: 0 → 1`, `translateY(24px) → 0`
- Duration: 600ms, easing: cubic-bezier(0.16, 1, 0.3, 1)
- Stagger: 100ms between sibling elements
- Trigger: when element is 20% in viewport

### Hover States
- Buttons: background color shift, 200ms ease
- Cards: translateY(-2px) + box-shadow fade-in, 300ms ease
- Links: underline slide-in from left, 200ms ease
- Images: subtle scale(1.02), 400ms ease

### Page Transitions
- Fade between sections, 300ms
- No flashy transitions — everything is controlled and deliberate

### Loading
- Dot-matrix animation: dots illuminate in wave pattern
- Skeleton screens use dot-grid pattern as placeholder
- No spinners — Nothing's loading states are geometric

---

## Dark Section Rules

Pages frequently alternate white and black sections. On dark sections:
- Background: #000000 (pure black, not dark gray)
- Text: #FFFFFF
- Muted text: #AAAAAA
- Borders: #333333
- Dot grid: #333 dots, #FFF active
- Buttons invert (white primary on black bg)
- Same spacing, same typography weights — only colors flip

---

## Content Voice

Nothing's copy style is distinctive:
- **Conversational, lowercase headlines** — "it's metal now." not "IT'S METAL NOW"
- **Periods on headlines** — adds finality and confidence
- **Short, factual body copy** — specs speak for themselves
- **No exclamation marks** — ever
- **Technical precision** — "50 MP dual camera" not "amazing camera"
- **Understated confidence** — let the product do the talking

---

## Anti-Patterns (Never Do These)

1. **No gradients** — flat colors only (exception: product photography)
2. **No rounded corners** — 0px or 2px max border-radius
3. **No drop shadows on cards** — except subtle hover state
4. **No decorative icons** — only functional or spec icons
5. **No color backgrounds** — only black, white, and grays
6. **No busy patterns** — only the dot-matrix grid, used sparingly
7. **No emoji** — ever
8. **No multiple font weights in one line** — keep it clean
9. **No borders on images** — product photos float freely
10. **No uppercase headlines** — sentence case with period is the signature

---

## File References

- **Color tokens, typography, spacing:** Defined above in this file
- **Component HTML/CSS patterns:** `references/component-inventory.md`
- **Design system tokens (full CSS):** `references/design-system.md`
- **Interaction & animation specs:** `references/interactions.md`
