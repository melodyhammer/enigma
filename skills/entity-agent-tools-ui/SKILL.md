---
name: entity-agent-tools-ui
description: >
  Build and modify front-end UI for the Enigma Entity Agent Tools presentation site.
  Use when the user asks to "build the entity agent tools page", "implement the entity tools site",
  "add a section to the entity tools page", "update the hero glitch effect", "style the business cards",
  "create the comparison cards", "add the D3 entity graph", "implement the architecture stack",
  "build the phase expansion flow", "update the test results section", "implement the nav dots",
  or discusses front-end work on the Enigma entity agent tools presentation. Also triggers when
  the user references entity-agent-tools, the Enigma slide deck site, entity-agent-tools-psi,
  or the beige-themed Enigma product page.
version: 1.0.0
---

# Enigma Entity Agent Tools — Presentation Site UI Skill

You are building and maintaining the front-end for Enigma's Entity Agent Tools presentation site — a 10-section, full-viewport scrollable experience that showcases Enigma's business identity resolution platform. The site is a **single-page HTML/CSS/JS application** deployed on **Vercel**.

**Live reference:** https://entity-agent-tools-psi.vercel.app/

Before writing any code, read the reference files in `references/` for exact design tokens, component specs, section blueprints, and interaction patterns.

---

## Design Principles

1. **Light, warm, typographic** — Beige background (`#f5f3f0`), near-black text, emerald green accents. Berkeley Mono throughout. The page should feel like a polished data presentation, not a marketing site.
2. **Full-viewport sections** — Each of the 10 sections is `min-height: 100vh` with scroll-snap on desktop. Users navigate like a slide deck.
3. **Data as UI** — Business cards with real revenue data, comparison tables, stat grids, and ASCII-style terminal output are the primary visual elements. No stock photos or illustrations.
4. **Subtle interactivity** — Nav dots, keyboard navigation, card hover reveals, and a D3.js force-directed graph. Animations are functional (scroll reveals, hover states), not decorative.
5. **Monospace-first typography** — Berkeley Mono in 4 weights (400–700) is the primary font. Inter as body fallback. All-caps headings with letter-spacing.

---

## Tech Stack

- **Rendering:** Single HTML file, vanilla CSS + JS
- **Canvas:** p5.js for hero glitch effect (WebGL shaders)
- **Data Visualization:** D3.js force simulation for entity graph (Section 09)
- **Fonts:** Self-hosted Berkeley Mono (woff2), Inter fallback
- **Layout:** CSS Grid + Flexbox, scroll-snap on desktop
- **Animations:** CSS transitions + IntersectionObserver for scroll reveals
- **Deployment:** Vercel

---

## Page Architecture (10 Sections)

Each section follows this general structure:

```html
<section style="min-height: 100vh; scroll-snap-align: start;">
  <div class="section-number">{NN}</div>
  <!-- Section-specific content -->
</section>
```

Section numbers are large, semi-transparent watermarks (`clamp(48px, 15vw, 180px)`, opacity 0.06, positioned top-left).

---

### Section 01 — Hero
**Background:** `#0a0a0a` (dark, contrasting with rest of page)
**Title:** "ENTITY AGENT TOOLS"
**Subtitle:** "Authoritative business data APIs for AI agents. The foundation layer for faster, more accurate entity enrichment."

**Implementation:**
- Full-viewport dark section with p5.js glitch canvas (`#glitch-container`)
- Canvas uses two WebGL shaders: composite pass + glitch distortion pass
- Glitch renders in `#F3EEEA` color with chromatic aberration + block displacement
- Grid generation functions: `widthGrid`, `widthGridPg1`, `widthStripe`
- 64×42 block grid for glitch displacement
- Vignette overlay: `radial-gradient(ellipse at center, transparent 40%, rgba(0,0,0,0.5) 100%)`
- Text is white (`#ffffff`) with paragraph at `rgba(255,255,255,0.85)`
- Scroll bounce indicator at bottom (2s ease-in-out, translateY 0–8px)
- `pixelDensity(1)` for performance

See `references/interactions.md` for full shader code details.

### Section 02 — Context
**Title:** "Two approaches to entity research"

**Implementation:**
- Two-column comparison grid (`grid-template-columns: 1fr 1fr`)
- Left card: "Web Research" — neutral styling
- Right card: "Knowledge Graph" — highlighted with accent border + gradient background
- Metrics compared: Response time (30s–5min vs ~0.4s), data sourcing, verification
- Key differentiator callout: "Revenue data from card transactions, not web estimates. Legal entity verification against government registrations, not scraped databases."
- Stacks to 1 column on mobile

### Section 03 — Data Foundation
**Title:** "The Data Foundation"
**Subtitle:** "Perpetually updating source of truth for US businesses. Every entity connected by relationships traversable in real-time."

**Implementation:**
- 5-column stat grid (`grid-template-columns: repeat(5, 1fr)`, gap: 1px)
- Stats:
  - **112M** Legal Entities
  - **33M** Brands
  - **27M** Locations
  - **80M** Persons
  - **2B+** Gov Records
- Each stat card has: `.stat-category` (label), `.stat-value` (large number), `.stat-label` (description)
- 1px gap creates grid-line visual effect
- Responsive: maintains 5 columns on tablet (reduced padding), 2 columns on mobile, 1 column on very small screens

### Section 04 — Entity Expansion
**Title:** "Entity Expansion"
**Subtitle:** "One API call. Four expansion phases."

**Implementation:**
- Phase flow visualization showing "Tacombi" query expanding through 4 phases
- Each phase is a card/panel with phase number, title, and data output
- Phase 1: Brand Resolution (1 record) — TACOMBI, Mexican Restaurant, $33.5M
- Phase 2: Legal Entities (9 records) — TACOMBI HOLDING NA LLC, 8 subsidiaries
- Phase 3: Relationships & Registrations (48 records) — 5 officers, 26 locations, 9 states
- Phase 4: Government Records (329 records) — 216 DOHMH, 28 Chicago, 15 DOB, 22 other
- Summary bar: "1 → 329 | One fuzzy name expands to 329 connected records"
- Footer: "API calls: 2 | Total time: <3s"
- Phase arrows connect phases horizontally on desktop, hidden on mobile (stacks vertically)

See `references/section-specs.md` for exact terminal output content.

### Section 05 — Test Examples
**Title:** "Test Examples"

**Implementation:**
- Grid of 6 business cards (`.biz-card` component)
- Each card has:
  - `.card-header` with background image reveal on hover
  - `.monogram` (48×48px, top-right, fades out on hover)
  - `.card-content` with data rows
  - `.data-row` grid: `70px 1fr 24px 1fr` (label | enigma value | vs | web value)
  - `.speed-row` at bottom showing speed comparison with ratio badge
- Card hover: image fades in, text goes white, monogram fades, card lifts 2px with shadow
- 6 examples: Consignment Brooklyn, Odd Sister, Maelove, The Garage, Laki Active, N. Market Restaurant

See `references/section-specs.md` for all 6 card data sets.

### Section 06 — The Entity Resolution Problem
**Title:** "The Entity Resolution Problem"
**Subtitle:** "Identity is hard"

**Implementation:**
- Maxxon Co deep-dive case study
- Two-column layout comparing Enigma result vs Web result:
  - **Enigma (correct):** Small wholesale distributor, City of Industry CA, $176,869 revenue, resolved in 0.71s
  - **Web (wrong):** Maxxon Corporation, national flooring manufacturer, Hamel MN, $15.4M revenue, took 30.9s
- "87× revenue difference" callout
- Why Web Fails explanation: "maxxonusa.com is down. No web footprint. Google defaults to the nationally-known Maxxon® Corporation..."
- How Enigma Resolves: "Graph traversal links 'MAXXON CO' to its CA state registration, NAICS code, and card transaction revenue"
- Verification: "Google Maps confirms warehouse at 17915 Railroad St. Google AI Overview confirms these are two separate entities."

### Section 07 — Test Results
**Title:** "Test Results · 100 Businesses"

**Implementation:**
- Key metrics displayed prominently:
  - **75×** faster avg
  - **80.2%** Enigma fill rate vs **63.5%** web
  - **35%** web errors
  - Enigma **0.66s** vs Web **49.3s**
- Latency distribution: p50 0.54s, p95 0.82s, p99 0.96s — "100% under 1 second"
- Web response distribution histogram (n=99): <30s: 7, 30–60: 47, 60–90: 22, >90s: 3
- Field-by-field fill rates table (6 fields, Enigma vs Web)
- Web error pattern categories: WRONG ENTITY, TOTAL FAILURE, INACCURATE, GAVE UP
- "35% of web queries affected"

See `references/section-specs.md` for all data tables.

### Section 08 — Architecture
**Title:** "Architecture"
**Subtitle:** "Knowledge graphs at the foundation change what's possible above."

**Implementation:**
- Vertical stack diagram (`.stack-visual`, flex column, gap 2px)
- 4 layers, each a colored band with gradient:
  - **Inference** (top): `linear-gradient(135deg, #E8704A, #a855f7)` — "Reasoning · Synthesis · Answer generation | LLM"
  - **Orchestration + Web:** `linear-gradient(135deg, #6366f1, #3b82f6)` — "Tool routing · Search · Crawl · Gap-filling | AGENT"
  - **Entity Resolution:** `linear-gradient(135deg, var(--accent), #059669)` — "Graph traversal · Linking · Verification | ENIGMA"
  - **Foundational Data** (bottom): `var(--fg)` (black) — "KNOWLEDGE GRAPH | 112M Registrations | 33M Brands | 27M Locations | 2B+ Gov Records"
- "The Inversion" callout: "Most agents start with inference and hope web search fills gaps. This stack resolves entities first, then infers on verified data."

### Section 09 — The Complete Picture
**Title:** "The Complete Picture"
**Case study:** Lincoln Avenue Capital — 118 linked entities across 47 states

**Implementation:**
- Workflow steps: INPUT → ENIGMA API (0.4s) → Data Retrieved → Verified Crawl Targets → Agent Web Research → OUTPUT
- Output summary: 118 entities, 5 officers, 14 fund structures, 47 state registrations
- **D3.js force-directed graph** (`#entity-graph`):
  - Force simulation with collision detection
  - Node types with distinct colors:
    - Center (LAC): `#2D8A6E`
    - Officers: `#D4A853`
    - Funds: `#C9735B`
    - Properties: `#6B9DBF`
    - GP/LP: `#5BA690`
    - States: `#4A6FA5`
  - Forces: link distance 100–140px, charge -250 to -1200, collision radius+25px
  - Draggable nodes with drag handlers
  - Glow filter on center node
  - Lazy-initialized via IntersectionObserver

See `references/interactions.md` for D3 graph configuration and `references/section-specs.md` for entity data.

### Section 10 — Use Cases & Next Steps
**Title:** "Use Cases" + "Next Steps"

**Implementation:**
- 6 use case cards (3-column grid on desktop, 1 column mobile):
  1. Business Identity Enrichment
  2. Lead Generation
  3. KYB Verification
  4. Due Diligence
  5. Fraud Detection
  6. Market Intelligence
- 3 CTA cards:
  - **Documentation:** "API Reference — Full API docs, authentication, rate limits, response schemas." → docs.enigma.com
  - **Claude Code Skill:** "enigma-api — Claude Code plugin with 4 skills: Screen, GraphQL, KYB, and Gov Archive APIs." → Download Plugin (enigma-api-plugin.zip)
  - **Test Data:** "Sample Entities — 100 test entities..." → Download CSV (sample-entities.csv)
- Final CTA: "Ready for API access?" → contact@enigma.com

---

## Global Components

### Fixed Navigation Dots
- 10 dots (one per section), fixed top-center
- Container: pill shape (`border-radius: 100px`), blurred background (`backdrop-filter: blur(12px)`)
- Each dot: 6×6px circle, `border-radius: 50%`
- Active state: `background: var(--accent)`, `transform: scale(1.3)`, glow shadow
- Click: `scrollIntoView({ behavior: 'smooth' })`
- Updated via IntersectionObserver (threshold 0.1)
- Hidden on mobile (<769px)

### Section Counter
- Fixed bottom-right, format "01 / 10"
- Berkeley Mono, 12px, weight 600, color `var(--muted)`
- Updates with active section

### Fixed Logo
- Top-left corner, `enigma-logo.svg`
- Desktop: 32px from edges; Mobile: 16px from edges

### Scroll Reveal
- All sections start: `opacity: 0; transform: translateY(30px)`
- `.visible` class: `opacity: 1; transform: translateY(0)`
- Transition: `0.6s cubic-bezier(0.4, 0, 0.2, 1)`
- Triggered by IntersectionObserver (threshold 0.1)

### Grid Background
- Fixed 60×60px grid pattern across entire page
- Opacity 0.04, z-index 0
- Provides subtle texture

---

## File References

- **Design tokens & colors:** `references/design-system.md`
- **Component specs & markup patterns:** `references/component-inventory.md`
- **Per-section detailed content & data:** `references/section-specs.md`
- **JavaScript interactions, shaders & D3 config:** `references/interactions.md`
