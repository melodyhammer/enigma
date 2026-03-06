---
name: enigma-landing-ui
description: >
  Build and modify front-end UI for the Enigma Entity Agent Tools landing page.
  Use when the user asks to "build the landing page", "implement the MCP landing page",
  "add a section to the landing page", "update the hero section", "style the demo terminal",
  "create a comparison table", "add the graph visualization", "implement the architecture
  diagram", "build the entity expansion demo", "implement the stats section", or discusses
  front-end work on the Enigma product marketing site. Also triggers when the user references
  mcp-landing-page, entity agent tools UI, or the Enigma marketing site design.
version: 1.0.0
---

# Enigma Entity Agent Tools — Landing Page UI Skill

You are building and maintaining the front-end for Enigma's Entity Agent Tools landing page, a high-impact marketing site that showcases Enigma's business identity resolution platform. The site is built with **Astro** and deployed on **Vercel**.

Before writing any code, read the reference files in `references/` for exact design tokens, component specs, section blueprints, and interaction patterns.

---

## Design Principles

1. **Dark-first, data-dense** — Black backgrounds, monospace type for data, high contrast teal accents. The page should feel like a technical tool, not a SaaS template.
2. **Show, don't tell** — Every section has a live demo, real data table, or interactive visualization. Avoid decorative filler.
3. **Terminal aesthetic** — Code blocks, ASCII trees, and API output are first-class UI elements, not afterthoughts.
4. **Performance-conscious** — WebGL canvas throttles to 15 FPS on mobile / 30 FPS on desktop. Respect `prefers-reduced-motion`. Lazy-load heavy sections with IntersectionObserver.
5. **Progressive disclosure** — The page is 10 numbered sections. Each builds on the previous. Scroll-triggered animations reveal content as the user progresses.

---

## Page Architecture (10 Sections)

The page is divided into 10 numbered sections (`#section-01` through `#section-10`). Each section has a consistent structure:

```
<section id="section-{NN}">
  <div class="section-label">{NN}</div>
  <div class="section-tag">{CATEGORY}</div>
  <h2>{Title}</h2>
  <p>{Description}</p>
  {Section-specific content}
</section>
```

### Section 01 — Hero
**Tag:** HERO
**Title:** "The Identity Layer AI Agents Call First"
**Subtitle:** "Training data goes stale. Businesses change. Enigma keeps up — entity resolution from authoritative, continually updated sources."

**Implementation:**
- Full-viewport WebGL glitch canvas (`#glitch-canvas`) as background
- Canvas renders procedural noise with chromatic aberration shader
- Two-pass rendering: composite pass to framebuffer → glitch pass to screen
- 4 pattern textures generated via Canvas2D (checker, grid squares, horizontal stripes, dots)
- Dual CTA buttons: "Get API Access" (mailto:info@enigma.com) and "View MCP Setup" (/mcp)
- Scroll indicator at bottom
- Canvas cleanup on `webglcontextlost`, `astro:before-swap`, `beforeunload`
- Skip first 30 frames for smooth startup
- Respect `prefers-reduced-motion` — disable canvas animation entirely

See `references/interactions.md` for full WebGL shader details.

### Section 02 — Context
**Tag:** CONTEXT
**Title:** "Two Approaches to Entity Research"

**Implementation:**
- Side-by-side comparison table with two columns: "Web Research" vs "Knowledge Graph"
- Rows compare: Response Time (30s–5min vs ~0.4s), Revenue Data (scraped vs verified), Verification (unreliable vs authoritative)
- Use `<table>` with clear column headers
- Highlight the "Knowledge Graph" column with teal accent border or background tint
- Animate in on scroll via IntersectionObserver

### Section 03 — Data Foundation
**Tag:** DATA FOUNDATION
**Title:** "The Enigma Business Graph"

**Implementation:**
- Stat counter grid displaying 5 key metrics:
  - **112M** registrations across 52 jurisdictions
  - **33M** brands indexed (including micro-merchants)
  - **27M** physical operating locations
  - **80M** persons (officers & principals)
  - **2B+** government records
- Each stat is a card with the number prominently displayed in large monospace type
- Subtitle text below each number in smaller gray text
- Consider animating numbers counting up on scroll entry
- Closing text about real-time graph traversal capabilities

### Section 04 — Live Demo
**Tag:** LIVE DEMO
**Title:** "Entity Expansion"

**Implementation:**
- Terminal-style panel showing the command: `$ enigma expand query: "Tacombi"`
- Output renders in 4 sequential phases with type-in animation (`.05s ease forwards` with line-index delay):
  - **Phase 1 — Brand Resolution** (1 record): TACOMBI, Mexican Restaurant, NAICS 722511, tacombi.com, $33.5M revenue
  - **Phase 2 — Legal Entities** (9 records): TACOMBI HOLDING NA LLC (NY 2009), 8 subsidiaries
  - **Phase 3 — Officers & Locations** (48 records): 5+ officers, 26 locations, 9 registrations
  - **Phase 4 — Government Records** (329 records): 216 NYC DOHMH inspections, 28 Chicago inspections, 15 DOB applications, 22 other
- Summary bar at bottom: 329 records, 2 API calls, <3s, 8 entities, 5+ officers, 26 locations
- Use Berkeley Mono font, dark background, teal accent for phase headers
- Dither-style progress bars between phases

See `references/section-specs.md` for exact terminal output content.

### Section 05 — Test Examples
**Tag:** TEST EXAMPLES
**Title:** "Side-by-side Results"

**Implementation:**
- Interactive comparison table with 6 real business queries
- Each row has a toggle button to flip between Enigma results and web research results
- Columns: Query, Brand, Legal Entity, Revenue, Response Time
- Speed ratio badge on each row (29×–371× faster)
- Toggle buttons use `.toggle-btn` class with active state styling
- Default view shows Enigma results; clicking toggles to web results for that row

**Data (6 rows):**
1. BUTTER CONSIGNMENT LLC → CONSIGNMENT BROOKLYN / $872,738 / 0.44s (vs 35.2s = 80×)
2. 45 MERCER RESTAURANT LLC → MERCER KITCHEN / $2.5M / 0.33s (vs 90.5s = 274×)
3. N. MARKET RESTAURANT, INC. → NORTH MARKET RESTAURANT / $1.3M / 0.59s (vs 218.8s = 371×)
4. Laki Active → LAKI ACTIVE LLC / $244,226 / 1.54s (vs 44.5s = 29×)
5. Suitsupply → SUITSUPPLY USA INC / $11.5M / 0.63s (vs 33.6s = 53×)
6. Blank Street → BLANK STREET INC / $3.0B / 0.38s (vs 36.8s = 97×)

See `references/section-specs.md` for full table data including web research results.

### Section 06 — Identity Case Study
**Tag:** IDENTITY
**Title:** "Identity is Hard"

**Implementation:**
- Deep-dive analysis panel for "Maxxon Co" search
- Three-column or stacked layout:
  - **The Problem:** Web research returned wrong entity (live competitor site)
  - **Enigma's Approach:** Graph traversal + state registration resolved correct entity
  - **Verification:** Government sources confirming correctness
- Use callout boxes or cards for each column
- Red/warning accent for the "wrong result" section, teal for the "correct" section

### Section 07 — Test Results
**Tag:** TEST RESULTS
**Title:** "80 Businesses — Speed + Quality"

**Implementation:**
- Statistical summary from 80-business benchmark
- Key metrics displayed prominently:
  - Enigma median: **0.54s** (p95: 0.82s, p99: 0.96s)
  - Web median: **43s**
  - Enigma fill rate: **81.5%** vs Web: **68.2%**
- Field-by-field accuracy table (6 fields):
  - Brand Name: 98% vs 81% (+17pp)
  - Address: 82% vs 84% (-2pp)
  - Phone: 81% vs 78% (+3pp)
  - Website: 86% vs 84% (+2pp)
  - Revenue: 66% vs 31% (+35pp)
  - Legal Entity: 76% vs 51% (+25pp)
- Response time distribution histogram:
  - <30s: 5 queries, 30-60s: 46, 60-90s: 24, >90s: 4
- Web error rate breakdown: 31% (wrong entity, total failure, inaccurate data, gave up)

### Section 08 — Architecture
**Tag:** ARCHITECTURE
**Title:** "The Stack"

**Implementation:**
- Vertical layered diagram showing 4 tiers (bottom to top):
  - **Layer 1 — Knowledge Graph:** "112M business registrations, 33M brands, 27M locations, 2B+ government records. Authoritative dataset enabling entity resolution."
  - **Layer 2 — Entity Resolution (Enigma):** "Core differentiator. Graph traversal links businesses to officers, addresses, filings, and state registrations. Entity ID becomes source of truth."
  - **Layer 3 — Orchestration + Web (Enigma MCP):** "Routes tools, crawls verified URLs, and fills gaps. Web research is targeted—no blind searching—because entities are already resolved."
  - **Layer 4 — Inference (LLM):** "Reasoning engine synthesizes entity data and research into coherent answers. Operates on verified inputs rather than raw web results."
- Callout box: **"The Inversion"** — "Most agents start with inference and hope web search fills gaps. This stack resolves entities first, then infers on verified data."
- Each layer should be a distinct card/band with increasing visual prominence toward the top
- Use subtle connecting lines or arrows between layers

### Section 09 — Complex Relationships
**Tag:** COMPLEX RELATIONSHIPS
**Title:** "Uncover Complex Relationships Instantly"

**Implementation:**
- Case study: Lincoln Avenue Capital — 118 linked entities across 47 states
- Toggle between two views:
  - **Tree View:** ASCII-style indented tree showing entity hierarchy
  - **Graph View:** Interactive SVG node-link diagram
- Key metrics sidebar: 118 entities, 5 officers, 14 fund structures, 6 state registrations, 8 properties
- SVG graph has hoverable/clickable nodes for officers, funds, properties, states
- Node types distinguished by color/shape:
  - Officers: one color
  - Funds: another color
  - Properties: another color
  - State registrations: another color
- Toggle buttons (`.toggle-btn`) switch between tree/graph with `.view-panel.active` visibility

See `references/section-specs.md` for Lincoln Avenue Capital entity details.

### Section 10 — Use Cases & CTA
**Tag:** USE CASES
**Title:** "Where It Fits"

**Implementation:**
- 7 use case bullets:
  1. Business Identity
  2. Lead Generation
  3. KYB Verification
  4. Due Diligence
  5. Fraud Detection
  6. Market Intelligence
  7. (General research)
- Documentation links:
  - "MCP Server →" → /mcp
  - "Documentation" → https://documentation.enigma.com/guides/ai-mcp
  - "Console" → https://console.enigma.com
  - "Support" → mailto:support@enigma.com
- Feature announcements: Claude Code skill (coming soon), Sample Entities CSV (coming soon)
- Final CTA: "Get API Access" (mailto:info@enigma.com)
- Footer links: API Reference (https://docs.enigma.com), GitHub (coming soon), CSV (coming soon)

---

## Global Components

### Scroll-Triggered Header
- Fixed position, initially transparent
- At 50px scroll: adds backdrop blur
- Below 50% viewport: shows full navigation with logo opacity transition
- Nav links: MCP Server, Documentation, Console, Support
- Logo toggles between dark/light variants based on scroll position
- Passive scroll listener for performance

### IntersectionObserver Animations
- All elements with `.animate-in` class get `.is-visible` added on viewport entry
- Threshold: 0.1, root margin: -50px
- CSS handles the actual transition (opacity 0→1, translateY)
- Re-initialized on `astro:page-load` for view transitions

### Dither Progress Bars
- Custom progress bar component with pixelated/dithered fill pattern
- Dual-theme variants (light and dark)
- Used between demo phases and in stat comparisons

---

## File References

- **Design tokens & colors:** `references/design-system.md`
- **Component specs & markup patterns:** `references/component-inventory.md`
- **Per-section detailed content & data:** `references/section-specs.md`
- **JavaScript interactions & WebGL details:** `references/interactions.md`
