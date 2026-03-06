# Component Inventory — Entity Agent Tools Site

## Global Components

### Fixed Logo
```html
<div class="logo">
  <img src="enigma-logo.svg" alt="Enigma" />
</div>
```
- Position: fixed, top-left
- Desktop: `top: 32px; left: 32px`
- Mobile: `top: 16px; left: 16px`

### Navigation Dots
```html
<nav>
  <button class="active" aria-label="Section 1"></button>
  <button aria-label="Section 2"></button>
  <!-- ... 10 total -->
</nav>
```
- Container: fixed top-center, pill shape
  - `background: rgba(245,243,240,0.85)`
  - `backdrop-filter: blur(12px)`
  - `border: 1px solid var(--border)`
  - `border-radius: 100px`
  - `padding: 6px 10px`
  - `gap: 6px`
- Each dot: `width: 6px; height: 6px; border-radius: 50%`
  - Default: `border: 1px solid var(--muted); background: transparent`
  - Hover: `border-color: var(--fg)`
  - Active: `background: var(--accent); border-color: var(--accent); transform: scale(1.3); box-shadow: 0 0 6px var(--accent)`
- Hidden below 769px

### Section Counter
```html
<div class="counter">
  <span id="current">01</span> / 10
</div>
```
- Fixed bottom-right
- Desktop: `bottom: 32px; right: 32px`
- Mobile: `bottom: 16px; right: 16px; font-size: 10px`
- Font: Berkeley Mono, 12px, weight 600, `var(--muted)`

### Section Watermark Number
```html
<div class="section-number">01</div>
```
- Absolutely positioned: `top: 40px; left: 40px`
- Font: Berkeley Mono, `clamp(48px, 15vw, 180px)`, weight 700
- Opacity: 0.06
- z-index: -1

### Grid Background
```css
body::before {
  content: '';
  position: fixed;
  inset: 0;
  background-image:
    linear-gradient(var(--fg) 1px, transparent 1px),
    linear-gradient(90deg, var(--fg) 1px, transparent 1px);
  background-size: 60px 60px;
  opacity: 0.04;
  z-index: 0;
  pointer-events: none;
}
```

---

## Section-Specific Components

### p5.js Glitch Canvas (Section 01)
```html
<div id="glitch-container">
  <!-- p5.js canvas injected here -->
</div>
```
- Full viewport, behind hero text
- WebGL shaders for composite + glitch passes
- `pixelDensity(1)` for performance
- Color output: `#F3EEEA`
- Glitch block grid: 64×42 blocks
- Offset range: 0.01–0.06

### Scroll Indicator (Section 01)
```html
<div class="scroll-indicator">
  <span>scroll</span>
  <div class="scroll-arrow">↓</div>
</div>
```
- Positioned at bottom of hero
- `animation: scroll-bounce 2s ease-in-out infinite`
- Hidden on mobile

### Comparison Card (Section 02)
```html
<div class="comparison-grid">
  <div class="comparison-card">
    <h3>Web Research</h3>
    <div class="comparison-metric">
      <span class="metric-label">Response time</span>
      <span class="metric-value">30s - 5min typical</span>
    </div>
    <!-- More metrics -->
  </div>
  <div class="comparison-card highlight">
    <h3>Knowledge Graph</h3>
    <div class="comparison-metric">
      <span class="metric-label">Response time</span>
      <span class="metric-value">~0.4s API call</span>
    </div>
    <!-- More metrics -->
  </div>
</div>
```
- `.highlight`: accent border-top or left, subtle gradient background with `--accent-dim`
- Grid: `1fr 1fr` on desktop, `1fr` on tablet/mobile

### Stat Card (Section 03)
```html
<div class="stat-grid">
  <div class="stat-card">
    <span class="stat-category">Legal Entities</span>
    <span class="stat-value">112M</span>
    <span class="stat-label">registrations across 52 jurisdictions</span>
  </div>
  <!-- 5 cards total -->
</div>
```
- Grid: `repeat(5, 1fr)` with 1px gap (creates grid-line effect)
- Stat value: large monospace bold
- Responsive: 5 cols → 2 cols → 1 col

### Phase Flow (Section 04)
```html
<div class="phase-flow">
  <div class="phase-card">
    <div class="phase-number">01</div>
    <div class="phase-title">Brand Resolution</div>
    <div class="phase-record-count">1 record</div>
    <div class="phase-data">
      <div class="data-line">Brand: TACOMBI</div>
      <div class="data-line">Type: Mexican Restaurant</div>
      <div class="data-line">Revenue: $33.5M</div>
    </div>
  </div>
  <div class="phase-arrow">→</div>
  <!-- More phases -->
</div>
<div class="phase-summary">
  <span class="summary-big">1 → 329</span>
  <span class="summary-text">One fuzzy name expands to 329 connected records</span>
  <span class="summary-meta">API calls: 2 | Total time: &lt;3s</span>
</div>
```
- Horizontal flow on desktop with arrows between phases
- Vertical stack on mobile (arrows hidden)
- Phase numbers in accent color

### Business Card (Section 05)
```html
<div class="biz-card">
  <div class="card-header" style="min-height: 80px; padding: 20px;">
    <div class="card-bg" style="background-image: url(...)"></div>
    <div class="monogram">CB</div>
    <h3 class="card-title">Consignment Brooklyn</h3>
    <p class="card-subtitle">Input: "BUTTER CONSIGNMENT LLC"</p>
  </div>
  <div class="card-content">
    <div class="data-row">
      <span class="row-label">Brand</span>
      <span class="row-enigma">CONSIGNMENT BROOKLYN</span>
      <span class="row-vs">vs</span>
      <span class="row-web">Consignment Brooklyn</span>
    </div>
    <!-- More data rows -->
    <div class="data-row speed-row">
      <span class="row-label">Speed</span>
      <span class="row-enigma">0.44s</span>
      <span class="row-vs">vs</span>
      <span class="row-web">32.1s <span class="speed-badge">73×</span></span>
    </div>
  </div>
</div>
```

**Hover behavior:**
1. `.card-bg` fades in (`opacity: 0 → 1`, 0.3s)
2. Text over image goes white
3. `.monogram` fades out (`opacity: 1 → 0`, 0.3s)
4. Gradient overlay: `linear-gradient(to top, rgba(0,0,0,0.7), rgba(0,0,0,0.3))`
5. Card lifts: `translateY(-2px)`, shadow appears

**Data row grid:** `grid-template-columns: 70px 1fr 24px 1fr`
- `.row-label`: muted, small
- `.row-enigma`: primary weight
- `.row-vs`: muted, centered
- `.row-web`: muted/secondary

**Speed row:** darker background `rgba(0,0,0,0.02)`, no bottom border

### Maxxon Case Study (Section 06)
```html
<div class="maxxon-comparison">
  <div class="result-card result-correct">
    <div class="result-badge">✓ ENIGMA FOUND</div>
    <h3>Small wholesale distributor</h3>
    <p>City of Industry, CA</p>
    <div class="result-data">
      <div>17915 RAILROAD ST, ROWLAND HEIGHTS, CA 91748</div>
      <div>(626) 964-1887</div>
      <div>Revenue: $176,869</div>
      <div>NAICS: 424 — Wholesale Trade</div>
    </div>
    <div class="result-meta">Resolved in 0.71s via knowledge graph</div>
  </div>
  <div class="result-card result-wrong">
    <div class="result-badge">✗ WEB RESEARCH FOUND</div>
    <h3>National flooring manufacturer</h3>
    <p>Hamel, MN</p>
    <div class="result-data">
      <div>920 HAMEL RD, HAMEL, MN 55340</div>
      <div>Revenue: $15.4 million</div>
    </div>
    <div class="result-meta">Wrong entity — 87× revenue difference · took 30.9s</div>
  </div>
</div>
```
- `.result-correct`: accent/green left border
- `.result-wrong`: red/warning left border
- 2 columns on desktop, 1 column on mobile

### Architecture Stack (Section 08)
```html
<div class="stack-visual">
  <div class="stack-layer layer-inference">
    <span class="layer-label">Inference</span>
    <span class="layer-detail">Reasoning · Synthesis · Answer generation</span>
    <span class="layer-component">LLM</span>
  </div>
  <div class="stack-layer layer-orchestration">
    <span class="layer-label">Orchestration + Web</span>
    <span class="layer-detail">Tool routing · Search · Crawl · Gap-filling</span>
    <span class="layer-component">AGENT</span>
  </div>
  <div class="stack-layer layer-entity">
    <span class="layer-label">Entity Resolution</span>
    <span class="layer-detail">Graph traversal · Linking · Verification</span>
    <span class="layer-component">ENIGMA</span>
  </div>
  <div class="stack-layer layer-foundation">
    <span class="layer-label">Foundational Data</span>
    <span class="layer-detail">KNOWLEDGE GRAPH</span>
    <span class="layer-stats">112M Registrations | 33M Brands | 27M Locations | 2B+ Gov Records</span>
  </div>
</div>
```
- Flex column, gap 2px
- Each layer: horizontal band with gradient background
- Layer gradients defined in design-system.md

### D3 Entity Graph (Section 09)
```html
<svg id="entity-graph" width="100%" height="500">
  <!-- D3.js renders nodes + edges here -->
</svg>
```
- Force simulation: `d3.forceSimulation(nodes)`
  - `.force("link", d3.forceLink(links).distance(100-140))`
  - `.force("charge", d3.forceManyBody().strength(-250 to -1200))`
  - `.force("collision", d3.forceCollide().radius(r + 25))`
  - `.force("center", d3.forceCenter(w/2, h/2))`
- Node rendering: circles with radius based on type
- Edge rendering: lines between linked nodes
- Center node: larger radius + SVG glow filter
- Drag behavior: `d3.drag()` with start/drag/end handlers
- Lazy initialized when section enters viewport

### CTA Cards (Section 10)
```html
<div class="cta-grid">
  <div class="cta-card">
    <span class="cta-tag">Documentation</span>
    <h3>API Reference</h3>
    <p>Full API docs, authentication, rate limits, response schemas.</p>
    <a href="https://docs.enigma.com" class="cta-link">→ docs.enigma.com</a>
  </div>
  <div class="cta-card">
    <span class="cta-tag">Claude Code Skill</span>
    <h3>enigma-api</h3>
    <p>Claude Code plugin with 4 skills: Screen, GraphQL, KYB, and Gov Archive APIs.</p>
    <a href="enigma-api-plugin.zip" class="cta-link">↓ Download Plugin</a>
  </div>
  <div class="cta-card">
    <span class="cta-tag">Test Data</span>
    <h3>Sample Entities</h3>
    <p>100 test entities...</p>
    <a href="sample-entities.csv" class="cta-link">↓ Download CSV</a>
  </div>
</div>
```

### Final CTA
```html
<div class="final-cta">
  <p>Ready for API access?</p>
  <a href="mailto:contact@enigma.com" class="cta-button">contact@enigma.com</a>
</div>
```
