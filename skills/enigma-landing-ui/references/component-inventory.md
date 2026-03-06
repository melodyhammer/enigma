# Component Inventory — Enigma Landing Page

## Global Components

### Site Header
```html
<header class="site-header">
  <div class="header-inner">
    <a href="/" class="header-logo">
      <img class="header-logo-dark" src="/logo-dark.svg" alt="Enigma" />
      <img class="header-logo-light" src="/logo-light.svg" alt="Enigma" />
    </a>
    <nav class="header-nav">
      <a href="/mcp" class="header-nav-link">MCP Server</a>
      <a href="https://documentation.enigma.com/guides/ai-mcp" class="header-nav-link">Documentation</a>
      <a href="https://console.enigma.com" class="header-nav-link">Console</a>
      <a href="mailto:support@enigma.com" class="header-nav-link">Support</a>
    </nav>
  </div>
</header>
```

**Behavior:**
- Fixed position, z-index above all content
- Initially transparent background
- At `scrollY > 50`: adds `backdrop-filter: blur(10px)` and semi-transparent bg
- Below `innerHeight * 0.5`: shows full nav, transitions logo from light → dark
- Passive scroll event listener

### Section Container
```html
<section id="section-{NN}" class="page-section">
  <div class="section-inner">
    <div class="section-label">{NN}</div>
    <div class="section-tag">{CATEGORY}</div>
    <h2 class="section-title">{Title}</h2>
    <p class="section-description">{Description}</p>
    <!-- Section-specific content -->
  </div>
</section>
```

- Section label: 2-digit number, monospace, small, muted
- Section tag: ALL CAPS category, monospace, letter-spaced, small
- Title: Large sans-serif heading
- Description: Body text, secondary color

### Scroll Reveal Wrapper
```html
<div class="animate-in">
  <!-- Content fades in when scrolled into view -->
</div>
```

Uses IntersectionObserver with `threshold: 0.1` and `rootMargin: "-50px"`.

---

## Section-Specific Components

### WebGL Glitch Canvas (Section 01)
```html
<canvas id="glitch-canvas"></canvas>
```

- Full viewport dimensions
- Position: absolute, behind hero content
- WebGL context: `{ alpha: false, antialias: false }`
- Two-pass rendering pipeline:
  1. Composite pass: renders pattern textures + noise to framebuffer
  2. Glitch pass: applies chromatic aberration + block displacement to screen
- 4 procedural pattern textures (512×512 Canvas2D):
  - Checker pattern
  - Grid squares
  - Horizontal stripes
  - Dots/noise
- Throttled: 30 FPS desktop (`frameInterval = 1000/30`), 15 FPS mobile
- Skips first 30 frames for smooth startup
- Disabled entirely if `prefers-reduced-motion: reduce`

### Comparison Table (Section 02 / 05)
```html
<div class="comparison-table-wrapper">
  <table class="comparison-table">
    <thead>
      <tr>
        <th>Metric</th>
        <th class="col-enigma">Knowledge Graph</th>
        <th class="col-web">Web Research</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td class="metric-label">{Metric Name}</td>
        <td class="col-enigma">{Value}</td>
        <td class="col-web">{Value}</td>
      </tr>
    </tbody>
  </table>
</div>
```

### Interactive Toggle Table (Section 05)
```html
<div class="toggle-table">
  <div class="table-row" data-query="{query}">
    <div class="row-header">
      <span class="query-name">{Query}</span>
      <button class="toggle-btn" data-target="{query}">
        <span class="toggle-label-enigma">Enigma</span>
        <span class="toggle-label-web">Web</span>
      </button>
      <span class="speed-badge">{NN}×</span>
    </div>
    <div class="row-results row-enigma active">
      <!-- Enigma result columns -->
    </div>
    <div class="row-results row-web">
      <!-- Web result columns -->
    </div>
  </div>
</div>
```

Toggle logic: clicking `.toggle-btn` swaps `.active` between `.row-enigma` and `.row-web`.

### Stat Counter Card (Section 03)
```html
<div class="stat-grid">
  <div class="stat-card animate-in">
    <span class="stat-number">112M</span>
    <span class="stat-label">registrations across 52 jurisdictions</span>
  </div>
  <!-- More stat cards -->
</div>
```

- `.stat-number`: Large monospace, bold, white
- `.stat-label`: Small, secondary color, below number

### Terminal Demo Panel (Section 04)
```html
<div class="terminal-panel">
  <div class="terminal-header">
    <span class="terminal-dot red"></span>
    <span class="terminal-dot yellow"></span>
    <span class="terminal-dot green"></span>
  </div>
  <div class="terminal-body">
    <div class="terminal-command">
      <span class="prompt">$</span> enigma expand query: "Tacombi"
    </div>
    <div class="terminal-phase" data-phase="1">
      <div class="phase-header">Phase 1 — Brand Resolution</div>
      <div class="phase-lines">
        <div class="type-line" style="--line-index: 0">Brand: TACOMBI</div>
        <div class="type-line" style="--line-index: 1">Type: Mexican Restaurant</div>
        <!-- More lines -->
      </div>
    </div>
    <!-- More phases -->
    <div class="terminal-summary">
      <span class="summary-item">329 records</span>
      <span class="summary-item">2 API calls</span>
      <span class="summary-item">&lt;3s</span>
    </div>
  </div>
</div>
```

- Type-in animation via `--line-index` CSS variable
- Phase headers in teal accent
- Dither progress bars between phases

### Dither Progress Bar
```html
<div class="dither-bar">
  <div class="dither-fill" style="width: {percent}%"></div>
</div>
```

- Pixelated/dithered fill texture via repeating background pattern
- Two theme variants: light fill on dark bg, dark fill on light bg

### Architecture Stack (Section 08)
```html
<div class="arch-stack">
  <div class="arch-layer" data-layer="4">
    <div class="layer-number">4</div>
    <div class="layer-name">Inference</div>
    <div class="layer-component">LLM</div>
    <div class="layer-description">{Description text}</div>
  </div>
  <!-- Layers 3, 2, 1 -->
</div>
<div class="arch-callout">
  <h3>The Inversion</h3>
  <p>Most agents start with inference and hope web search fills gaps. This stack resolves entities first, then infers on verified data.</p>
</div>
```

- Stacked vertically, layer 1 at bottom, layer 4 at top
- Each layer is a horizontal band
- Connecting lines or arrows between layers
- "The Inversion" callout is a highlighted box below/beside the stack

### Entity Graph Visualization (Section 09)
```html
<div class="entity-graph-dual">
  <div class="graph-controls">
    <button class="toggle-btn active" data-view="tree">Tree</button>
    <button class="toggle-btn" data-view="graph">Graph</button>
  </div>
  <div class="view-panel tree-view active">
    <pre class="ascii-tree">{ASCII tree content}</pre>
  </div>
  <div class="view-panel graph-view">
    <svg class="entity-graph" viewBox="...">
      <!-- Nodes and edges -->
      <circle class="node node-officer" cx="..." cy="..." r="..." />
      <circle class="node node-fund" cx="..." cy="..." r="..." />
      <line class="edge" x1="..." y1="..." x2="..." y2="..." />
      <!-- Labels -->
    </svg>
  </div>
  <div class="graph-sidebar">
    <div class="sidebar-stat">118 entities</div>
    <div class="sidebar-stat">5 officers</div>
    <div class="sidebar-stat">14 fund structures</div>
    <div class="sidebar-stat">47 states</div>
  </div>
</div>
```

**Node types in SVG:**
| Type | Visual | Color suggestion |
|------|--------|-----------------|
| Officer | Circle | Blue/purple |
| Fund | Square/rounded rect | Teal |
| Property | Diamond/house icon | Orange |
| State Registration | Small circle | Gray |
| Root entity | Larger circle | White/bright |

**Interactions:**
- Hover: tooltip with entity name + type
- Click: could highlight connected edges
- Toggle: switches `.active` between tree-view and graph-view panels

### Use Case List (Section 10)
```html
<div class="use-case-list">
  <div class="use-case-item">
    <h3>Business Identity</h3>
    <p>{Description}</p>
  </div>
  <!-- More items -->
</div>
```

### CTA Footer
```html
<footer class="page-footer">
  <div class="footer-cta">
    <h2>Get Started</h2>
    <a href="mailto:info@enigma.com" class="cta-primary">Get API Access</a>
  </div>
  <div class="footer-links">
    <a href="https://docs.enigma.com">API Reference</a>
    <a href="/mcp">MCP Server</a>
    <a href="https://documentation.enigma.com/guides/ai-mcp">Documentation</a>
    <a href="https://console.enigma.com">Console</a>
    <a href="mailto:support@enigma.com">Support</a>
  </div>
  <div class="footer-brand">
    <span>© Enigma Technologies</span>
    <a href="https://www.enigma.com">enigma.com</a>
  </div>
</footer>
```
