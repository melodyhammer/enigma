---
name: usgraphics-ui
description: >
  Build UIs in the U.S. Graphics Company / Berkeley Mono design language —
  industrial-technical documentation aesthetic with monospace typography,
  catalog-number systems, datasheet layouts, and government-form precision.
  Use when the user asks to "create a technical document UI", "build a datasheet page",
  "make a catalog-style layout", "design a Berkeley Mono page",
  "create a US Graphics style site", "build an industrial-spec interface",
  "make a government-form layout", "design a technical specimen page",
  "create a procurement-catalog UI", "build a document-system interface",
  or discusses U.S. Graphics Company aesthetics, Berkeley Mono styling,
  technical-catalog design, datasheet layouts, engineering-document interfaces,
  or industrial typography. Also triggers when the user references
  "USGC style", "catalog number system", "datasheet UI", "technical specification page",
  "procurement document design", "engineering graphics", or "monospace document system".
version: 1.0.0
---

# U.S. Graphics Company UI — Design System Skill

You are building UIs in the U.S. Graphics Company design language — a radical aesthetic that treats every web page as a piece of **technical documentation**. The site looks and feels like a government procurement catalog, an engineering datasheet, or a military technical manual that happens to exist on the web. It's the opposite of "modern web design" — no hero gradients, no glossy cards, no playful illustrations. Instead: forms, specification tables, horizontal rules, catalog numbers, and monospace type presented with absolute institutional authority.

**Reference:** https://usgraphics.com/products/berkeley-mono

---

## Core Philosophy

The U.S. Graphics Company design language is built on 6 principles:

### 1. The Page Is a Document
Every page is a technical document first, a website second. The mental model is a printed datasheet, a government form, or a catalog page from a defense contractor. Content is organized with the same rigor as a MIL-SPEC publication: numbered sections, catalog codes, specification tables, and revision numbers.

### 2. Institutional Authority
The design radiates quiet, bureaucratic authority. It doesn't try to sell — it *specifies*. Products aren't "exciting" or "revolutionary" — they're assigned catalog numbers (TX-02, FX-102) and described with engineering precision. The tone is factual, measured, and slightly formal, like a clerk stamping forms.

### 3. Monospace as Primary Voice
Berkeley Mono (or a monospace fallback) is the primary typeface for body text, specifications, and data. This isn't a decorative choice — it's the foundational voice. Monospace text says: "this is precise, this is measured, this is engineered." A condensed sans-serif (Univers Condensed or similar) handles labels, headings, and navigation — the institutional counterpart.

### 4. The Horizontal Rule Is Sacred
Thin black horizontal lines are the primary structural element. They separate sections, delineate content blocks, and create visual hierarchy. These aren't decorative — they're functional dividers, like the lines on a government form. Every major content boundary gets a rule.

### 5. Restraint as Identity
The palette is almost monochrome: black text on warm off-white/cream paper. Color is used only for functional status indicators (red for "new", muted for "unavailable"). There are no gradients, no decorative backgrounds, no visual flourishes. The restraint *is* the design.

### 6. Catalog-Number Everything
Every product, document, and resource gets an alphanumeric designation: TX-02, FX-102, DX-102-11, BT-002. These codes are prominently displayed, often more visually prominent than the product name itself. The system conveys that this is an organization that catalogs and systematizes everything.

---

## Color Tokens

```css
:root {
  /* ========== SURFACES ========== */
  --usg-bg: #F5F3EF;                    /* Warm cream — the "paper" */
  --usg-bg-pure: #FFFFFF;               /* Pure white — cards, inputs */
  --usg-bg-muted: #EDEAE4;             /* Slightly darker cream — alternating rows */
  --usg-bg-dark: #1A1A1A;              /* Near-black — specimen banners, dark panels */
  --usg-bg-inverse: #000000;           /* Pure black — hero banners */

  /* ========== TEXT ========== */
  --usg-text: #1A1A1A;                  /* Primary body text */
  --usg-text-secondary: #666666;        /* Muted/secondary text */
  --usg-text-tertiary: #999999;         /* Metadata, captions, disabled */
  --usg-text-inverse: #F5F3EF;          /* Text on dark surfaces */
  --usg-text-inverse-muted: #AAAAAA;    /* Muted text on dark */

  /* ========== BORDERS & RULES ========== */
  --usg-rule: #1A1A1A;                  /* Primary horizontal rules — black */
  --usg-rule-light: #CCCCCC;            /* Secondary/internal rules */
  --usg-rule-hairline: #E0DDD7;         /* Subtle dividers */
  --usg-border: #CCCCCC;               /* Form borders, table borders */
  --usg-border-dark: #333333;           /* Borders on dark surfaces */

  /* ========== STATUS & FUNCTIONAL ========== */
  --usg-new: #CC3300;                   /* "New!" badge — warm red */
  --usg-available: #1A1A1A;             /* "Available Now" — same as text */
  --usg-unavailable: #999999;           /* "Coming soon" / sold out */
  --usg-experimental: #996600;          /* "Experimental" status */
  --usg-link: #1A1A1A;                  /* Links — same as text, underlined */
  --usg-link-hover: #CC3300;            /* Link hover — the red */

  /* ========== SPECIMEN ========== */
  --usg-specimen-bg: #111111;           /* Dark specimen/banner background */
  --usg-specimen-text: #F5F3EF;         /* Specimen text — cream on dark */
}
```

---

## Typography

```css
:root {
  /* Primary: monospace for body, specs, data */
  --usg-font-mono: "Berkeley Mono", "SF Mono", "Menlo", "Courier New", monospace;

  /* Secondary: condensed sans-serif for headings, labels, navigation */
  --usg-font-condensed: "Univers LT Pro Condensed", "Arial Narrow",
                         "Helvetica Neue Condensed", sans-serif;

  /* Tertiary: standard sans-serif for occasional body use */
  --usg-font-sans: "Helvetica Neue", "Arial", -apple-system, sans-serif;
}
```

| Element | Font | Size | Weight | Style |
|---------|------|------|--------|-------|
| Page title / product name | Condensed | 32–48px | 700 | Uppercase, tracking 0.02em |
| Section heading | Condensed | 20–28px | 700 | Uppercase, tracking 0.02em |
| Sub-heading | Condensed | 16–18px | 700 | Uppercase, tracking 0.02em |
| Catalog number | Mono | 14–16px | 400 | Uppercase, tracking 0.1em |
| Body text | Mono | 14–15px | 400 | Normal case, line-height 1.7 |
| Specification value | Mono | 14px | 400 | Tabular, line-height 1.5 |
| Specification label | Condensed | 12px | 700 | Uppercase, tracking 0.05em |
| Navigation | Condensed | 13–14px | 700 | Uppercase, tracking 0.04em |
| Caption/metadata | Mono | 12px | 400 | Normal case, color: tertiary |
| Status badge | Condensed | 11px | 700 | Uppercase, tracking 0.08em |
| Footer/fine print | Mono | 11–12px | 400 | Normal case |
| Button | Condensed | 13px | 700 | Uppercase, tracking 0.06em |

**Key type rules:**
- Headings and labels use condensed sans-serif (institutional, compressed, authoritative)
- Body text and data use monospace (precision, engineering, measurement)
- This two-font pairing is the signature — condensed sans labels + mono body
- Headings are ALWAYS uppercase (this is the opposite of the Nothing style)
- Body text is sentence case, restrained, factual
- Line-height for mono body: 1.7 (generous — like a technical document for readability)

---

## Spacing System

Base unit: 8px. Spacing is generous — documents need breathing room for legibility.

| Token | Value | Use |
|-------|-------|-----|
| --usg-space-xs | 4px | Inline gaps, tight label spacing |
| --usg-space-sm | 8px | Table cell padding, icon gaps |
| --usg-space-md | 16px | Form field padding, list item gaps |
| --usg-space-lg | 24px | Card padding, paragraph spacing |
| --usg-space-xl | 32px | Between components |
| --usg-space-2xl | 48px | Section internal padding |
| --usg-space-3xl | 64px | Section breaks (with rule) |
| --usg-space-4xl | 96px | Major document sections |
| --usg-space-5xl | 128px | Page-level vertical rhythm |

---

## Layout System

### Document Grid
- Single-column primary, max-width 960px (narrow — like a document page)
- Side margins: 80px desktop → 48px tablet → 20px mobile
- For wider layouts: 12-column grid, max-width 1200px
- Content rarely goes wider than 720px for body text (reading column)

### Page Structure
Every page follows the "document" pattern:
```
┌─────────────────────────────────┐
│ HEADER (nav + logo)             │
│─────────────────────────────────│ ← thin rule
│                                 │
│ DOCUMENT TITLE                  │
│ Catalog Number: XX-000          │
│─────────────────────────────────│ ← thin rule
│                                 │
│ [SPECIMEN BANNER - dark bg]     │
│                                 │
│─────────────────────────────────│ ← thin rule
│                                 │
│ SECTION 1: DESCRIPTION          │
│ Monospace body text...          │
│                                 │
│─────────────────────────────────│ ← thin rule
│                                 │
│ SECTION 2: SPECIFICATIONS       │
│ ┌──────────┬──────────────────┐ │
│ │ Label    │ Value            │ │
│ ├──────────┼──────────────────┤ │
│ │ Label    │ Value            │ │
│ └──────────┴──────────────────┘ │
│                                 │
│─────────────────────────────────│ ← thin rule
│                                 │
│ SECTION 3: AVAILABILITY         │
│ Status + pricing + CTA          │
│                                 │
│─────────────────────────────────│ ← thin rule
│ FOOTER                          │
└─────────────────────────────────┘
```

---

## Component Patterns

### Navigation
- Top bar, cream background, separated from content by a thin black rule
- Logo (company name in condensed uppercase) left
- Links right: uppercase condensed, 13px, generous spacing
- No background color change on scroll — stays cream
- Links: black text, no underline, underline on hover
- Current page: slightly bolder or underlined
- Mobile: simple stacked list, no hamburger animation needed

### Horizontal Rules
The most important design element:
```css
.usg-rule {
  border: none;
  border-top: 1px solid var(--usg-rule);
  margin: 48px 0;
}

.usg-rule--light {
  border-top-color: var(--usg-rule-light);
  margin: 24px 0;
}

.usg-rule--heavy {
  border-top: 2px solid var(--usg-rule);
  margin: 64px 0;
}
```
Rules appear between EVERY major section. They are non-negotiable.

### Catalog Number Display
```
TX-02                    ← mono, 14px, letter-spacing 0.1em, color: tertiary
BERKELEY MONO™           ← condensed, 36px, 700, uppercase
TYPEFACE                 ← condensed, 16px, 700, uppercase, color: secondary
```

### Specimen Banners
Dark panels showing the typeface in action:
- Background: #111111 or #000000
- Text: cream/off-white (#F5F3EF)
- Large specimen text: 48–120px monospace
- Fills full container width
- No border-radius
- Often includes a glyph showcase or pangram

### Specification Tables
The core data component:
```
┌──────────────────┬──────────────────────────────────┐
│ ITEM             │ VALUE                            │
├──────────────────┼──────────────────────────────────┤
│ Widths           │ 5                                │
│ Weights          │ 12                               │
│ Slants           │ 2                                │
│ Total Styles     │ 120                              │
│ Variable Axes    │ wdth, wght, slnt                 │
│ Format           │ OTF, TTF, WOFF2                  │
└──────────────────┴──────────────────────────────────┘
```
- Labels: condensed sans, 12px, uppercase, bold
- Values: monospace, 14px, regular
- Borders: 1px solid #CCCCCC
- Cell padding: 12px 16px
- Alternating row bg: optional (cream / white)
- No border-radius

### Status Badges
```
[NEW!]           → red text (#CC3300), condensed, 11px, uppercase, bold
[AVAILABLE NOW →] → black text, condensed, 13px, uppercase, bold, with arrow
[COMING SOON]    → gray text (#999), condensed, 11px, uppercase
[EXPERIMENTAL]   → amber text (#996600), condensed, 11px, uppercase
```
No background fill — just colored text. Clean and document-like.

### Buttons
```
Primary:    1px solid black border, black text, transparent bg
            Hover: black bg, cream text
            Padding: 12px 24px

Action:     Black bg, cream text
            Hover: #333 bg
            Padding: 12px 24px

Link-style: Underlined text, no border, no padding
            Hover: red (#CC3300)
```
- All buttons: condensed sans, 13px, 700, uppercase, letter-spacing 0.06em
- ZERO border-radius — perfectly squared
- Transitions: 150ms ease

### Cards (Product Listings)
No visual "card" — just content blocks separated by horizontal rules:
```
────────────────────────────────────
TX-02
BERKELEY MONO™ TYPEFACE

[Dark specimen banner image]

A love letter to the golden era of computing.
Berkeley Mono is fitted with care to perform
as well as proportional typefaces whilst being
100% monospaced.

Available Now →
────────────────────────────────────
```
No shadows, no borders around the card, no background color. Just rules above and below.

### Forms & Inputs
```css
.usg-input {
  font-family: var(--usg-font-mono);
  font-size: 14px;
  padding: 10px 12px;
  border: 1px solid var(--usg-border);
  background: var(--usg-bg-pure);
  color: var(--usg-text);
  border-radius: 0;
  outline: none;
  transition: border-color 150ms ease;
}

.usg-input:focus {
  border-color: var(--usg-text);
}

.usg-label {
  font-family: var(--usg-font-condensed);
  font-size: 12px;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.05em;
  margin-bottom: 6px;
  display: block;
}
```

### Pricing Display
```
CATALOG NO.    FX-102
DESCRIPTION    Berkeley Mono™ Developer License
UNIT PRICE     $75.00
AVAILABILITY   In Stock
─────────────────────────────────
                    [ADD TO CART]
```
Prices displayed in monospace, right-aligned where appropriate. No "sale" styling — institutional, fixed pricing.

---

## Animation & Interaction

### Almost None
This is a key part of the aesthetic — things don't animate. Pages load and content is there. No scroll reveals, no fade-ins, no parallax. The document is the document.

Allowed interactions:
- Link underline on hover (instant or 150ms)
- Button background fill on hover (150ms ease)
- Focus outlines on form fields
- Subtle table row highlight on hover (background shift to cream)

That's it. No scroll-triggered anything. No transforms. No opacity animations. The page is static like a printed document.

### Page Load
Content renders immediately. No loading animations, no skeleton screens. If there's a loading state, it's a simple monospace text: "Loading..." — nothing more.

---

## Dark Panels (Specimen Sections)

When content needs a dark background (specimen showcases, hero banners):
- Background: #111111 or #000000
- Text: #F5F3EF (cream) — NOT pure white
- Muted text: #AAAAAA
- Rules: #333333
- Full-width within the document column
- Used sparingly — the page is primarily cream/light

---

## Content Voice

U.S. Graphics Company copy has a distinctive tone:
- **Institutional and formal** — "Available for immediate deployment" not "Get it now!"
- **Engineering precision** — specifications, not marketing claims
- **Understated** — "fitted with care to perform" not "the best font ever"
- **Catalog language** — "Catalog No.", "Unit Price", "Item Description"
- **Metaphorical depth** — products described with literary/poetic precision within the formal structure
- **No exclamation marks in body copy** — (except "New!" badge)
- **ALL CAPS for headings** — always, without exception
- **Product descriptions** read like technical abstracts, not sales copy

---

## Anti-Patterns (Never Do These)

1. **No border-radius** — everything is squared off, period
2. **No gradients** — flat colors only
3. **No card shadows** — content blocks are separated by rules, not elevation
4. **No colored backgrounds for sections** — only cream, white, and black
5. **No scroll animations** — the document is static
6. **No decorative illustrations** — only type specimens and functional diagrams
7. **No rounded buttons** — squared, bordered, institutional
8. **No playful typography** — condensed sans for labels, mono for body, always
9. **No hero sections with overlaid text on images** — specimen banners are separate from text
10. **No emoji** — ever
11. **No sentence-case headings** — ALWAYS UPPERCASE for headings and labels
12. **No multiple accent colors** — black, cream, and one red. That's the palette

---

## File References

- **Color tokens, typography, spacing:** Defined above in this file
- **Component HTML/CSS patterns:** `references/component-inventory.md`
- **Design system tokens (full CSS):** `references/design-system.md`
- **Interaction & page-structure specs:** `references/interactions.md`
