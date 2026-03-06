---
name: dramatic-dataviz
description: >
  Build dramatic editorial data visualizations in the Enigma ridge-plot style.
  Use when the user asks to "create a data visualization", "build a ridge plot",
  "make a joy division chart", "create a stacked wave chart", "build a dramatic chart",
  "visualize time series data", "create an editorial infographic", "make a poster chart",
  "build a bank failures chart", "create a spike visualization", "add particle effects
  to a chart", "implement cross-hatching", "build a dark mode data poster", or discusses
  editorial-style data art, dramatic infographics, or poster-quality data visualization.
  Also triggers when the user references "ridge lines", "joy plot", "stacked waveform",
  "explosive data viz", "Enigma dataviz style", or "editorial data art".
version: 1.0.0
---

# Dramatic Data Visualization — Editorial Style Skill

You are building data visualizations in the Enigma editorial style — dramatic, poster-quality charts that treat data as art. These are **not** dashboard charts. They are high-impact, narrative visualizations designed for storytelling, presentations, and marketing materials.

**Reference image:** `~/Downloads/hf_20260302_130256_b1465d26-894f-45ef-8eff-f577a50f1a5b.png`
(Bank Failures & Assets, 1930s–Present Day)

Before writing any code, consult the reference files in `references/` for exact visual patterns, rendering techniques, and animation specs.

---

## Visual Language

This style has 7 defining characteristics:

### 1. Ridge Plot Foundation
The base of every visualization is a **stacked ridge plot** (also called a joy plot). Dozens of horizontal wave lines are layered vertically with slight offsets, creating a topographic/geological depth effect. The lines represent the data series — peaks and valleys correspond to data values across time.

- 40–80+ individual lines stacked with 2–4px vertical offset
- Each line follows the same data contour but with slight vertical displacement
- Lines at the bottom are calmer/flatter, lines toward the top show more variation
- Creates the illusion of a 3D terrain or sedimentary layers

### 2. Explosive Jagged Spikes
When data values are extreme (crises, anomalies), the ridge lines don't just peak — they **erupt**. Jagged, mountain-like spikes shoot upward, breaking through the orderly wave pattern. These spikes:

- Are composed of sharp, angular line segments (not smooth curves)
- Have multiple sub-peaks and jagged edges
- Extend dramatically beyond the normal chart bounds
- Use crosshatch/pattern fills inside the spike body
- Terminate in particle debris at the top

### 3. Particle Debris Explosions
The tops of extreme spikes shatter into scattered geometric fragments:

- Small triangles, rectangles, diamonds, dots, and line segments
- Scattered outward and upward from the spike peak
- Larger fragments near the spike, smaller/fainter further away
- Creates a "shattering" or "explosive" effect
- Fragments use the same white stroke on dark background

### 4. Cross-Hatching & Pattern Fills
Interior areas of spikes and elevated regions use hand-drawn-style pattern fills:

- **Diagonal cross-hatching:** Intersecting diagonal lines at ~45°
- **Single-direction hatching:** Parallel diagonal lines
- **Grid hatching:** Horizontal + vertical intersecting lines
- Pattern density varies — tighter hatching in the core, sparser at edges
- Fills are bounded by the spike's outline geometry

### 5. Dark Canvas, White Lines
Everything renders as white strokes on a near-black background:

- Background: `#1a1a1a` to `#222222` (warm dark, not pure black)
- All lines: `#ffffff` or `rgba(255, 255, 255, 0.8–1.0)`
- No color fills — only stroke weight and opacity create visual hierarchy
- Glow/bloom effects on dense line clusters create brightness variation

### 6. Monospace Annotations
Text labels are minimal, precise, and documentary-style:

- All-caps, monospace font
- Small font size relative to the visualization
- Connected to features via thin leader lines
- Positioned to not overlap the main data visualization
- Labels describe what the data means, not just axis values

### 7. Minimal Iconography
Small line-art pictograms mark significant events on the timeline:

- Architectural/institutional icons (bank building, shield)
- Drawn with the same white-stroke-on-dark treatment
- Very small relative to the overall visualization
- Placed at their chronological position on the time axis

---

## Design Principles

1. **Data as landscape** — The chart should feel like terrain, geology, or a seismograph. Readers experience magnitude viscerally, not just numerically.
2. **Drama over precision** — Exact values are less important than conveying the *scale* of events. A spike 10× taller than the baseline tells the story.
3. **White on dark, always** — No color. The constraint of monochrome forces visual clarity through line weight, density, spacing, and pattern.
4. **Let empty space speak** — Calm periods (flat ridge lines) are as important as crises (spikes). The contrast creates narrative tension.
5. **Editorial annotation** — Labels are sparse, precise, and positioned like a newspaper infographic. They guide the eye without cluttering.

---

## Color Tokens

```css
:root {
  --dv-bg: #1a1a1a;                          /* Canvas background */
  --dv-bg-pure: #111111;                      /* Deeper black for contrast areas */
  --dv-line: #ffffff;                          /* Primary line color */
  --dv-line-dim: rgba(255, 255, 255, 0.4);    /* Faded/background lines */
  --dv-line-mid: rgba(255, 255, 255, 0.65);   /* Mid-emphasis lines */
  --dv-line-bright: rgba(255, 255, 255, 1.0); /* Peak/foreground lines */
  --dv-glow: rgba(255, 255, 255, 0.15);       /* Bloom/glow effect */
  --dv-text: #ffffff;                          /* Annotation text */
  --dv-text-dim: rgba(255, 255, 255, 0.6);    /* Secondary labels */
  --dv-axis: rgba(255, 255, 255, 0.3);        /* Axis lines and ticks */
}
```

## Typography

```css
--dv-font: "Berkeley Mono", "SF Mono", "Courier New", monospace;
```

| Element | Size | Weight | Style |
|---------|------|--------|-------|
| Chart title (if any) | 14–16px | 700 | ALL CAPS, letter-spacing 0.1em |
| Axis label | 11–12px | 400 | ALL CAPS, letter-spacing 0.06em |
| Annotation callout | 10–11px | 400 | ALL CAPS |
| Axis tick values | 9–10px | 400 | Monospace numbers |
| Fine print / source | 8px | 400 | ALL CAPS, dimmed |

---

## Rendering Approach

These visualizations are best built with **Canvas 2D** or **SVG** (for smaller datasets). D3.js for data binding, Canvas for performance with 40–80+ layered lines.

### Recommended Stack
- **D3.js** — Data loading, scales, axis generation
- **Canvas 2D** — Rendering ridge lines, hatching, particles (performance)
- **SVG overlay** — Annotations, labels, icons (crisp text rendering)

### Alternative: Pure SVG
For simpler datasets (<30 lines), pure SVG with D3 works well. Use `<path>` elements for ridge lines and `<pattern>` for cross-hatching.

---

## Implementation Guide

### Step 1: Ridge Plot Base

Generate N layered lines from the data:

```javascript
// Pseudo-code
for (let i = 0; i < NUM_LINES; i++) {
  const yOffset = i * LINE_SPACING;
  const opacity = mapRange(i, 0, NUM_LINES, 0.3, 1.0);

  ctx.beginPath();
  ctx.strokeStyle = `rgba(255, 255, 255, ${opacity})`;
  ctx.lineWidth = 0.8;

  for (let x = 0; x < dataPoints.length; x++) {
    const value = data[x] * heightScale;
    const y = baseY - value - yOffset;
    if (x === 0) ctx.moveTo(xScale(x), y);
    else ctx.lineTo(xScale(x), y);
  }
  ctx.stroke();
}
```

Key parameters:
- `NUM_LINES`: 40–80 (more = denser, more dramatic)
- `LINE_SPACING`: 2–4px vertical offset per line
- `lineWidth`: 0.5–1.0px (thin, precise)
- Opacity: gradient from dim (back) to bright (front)

### Step 2: Spike Geometry

When a data value exceeds a threshold, generate jagged spike geometry:

```javascript
function generateSpike(x, baseHeight, spikeHeight) {
  const points = [];
  const numSegments = 15 + Math.random() * 10;

  for (let i = 0; i <= numSegments; i++) {
    const t = i / numSegments;
    const width = spikeHeight * 0.3 * (1 - t); // narrows toward top
    const jag = (Math.random() - 0.5) * width * 0.6; // jagged edges
    const yPos = baseHeight + spikeHeight * t;

    points.push({
      left: x - width / 2 + jag,
      right: x + width / 2 + jag,
      y: yPos
    });
  }
  return points;
}
```

### Step 3: Cross-Hatching

Fill spike interiors with pattern:

```javascript
function drawCrossHatch(ctx, polygon, spacing, angle1, angle2) {
  ctx.save();
  ctx.clip(); // clip to polygon boundary

  // First direction
  drawHatchLines(ctx, polygon.bounds, spacing, angle1);
  // Second direction (cross)
  drawHatchLines(ctx, polygon.bounds, spacing, angle2);

  ctx.restore();
}

function drawHatchLines(ctx, bounds, spacing, angle) {
  ctx.strokeStyle = 'rgba(255, 255, 255, 0.5)';
  ctx.lineWidth = 0.5;
  // Generate parallel lines at `angle` across `bounds` with `spacing`
}
```

Hatching styles:
- **Dense cross-hatch** (4–6px spacing): Core of large spikes
- **Sparse cross-hatch** (10–15px spacing): Edges and smaller peaks
- **Single-direction** (8–12px spacing): Transitional areas

### Step 4: Particle Debris

Scatter fragments from spike peaks:

```javascript
function generateDebris(peakX, peakY, count) {
  const particles = [];
  for (let i = 0; i < count; i++) {
    const angle = Math.random() * Math.PI * 1.2 - Math.PI * 0.1; // mostly upward
    const distance = 20 + Math.random() * 150;
    const size = 1 + Math.random() * 6;

    particles.push({
      x: peakX + Math.cos(angle) * distance,
      y: peakY - Math.sin(angle) * distance, // upward
      size: size,
      rotation: Math.random() * Math.PI * 2,
      type: ['triangle', 'rect', 'diamond', 'dot', 'line'][Math.floor(Math.random() * 5)],
      opacity: mapRange(distance, 20, 150, 1.0, 0.1)
    });
  }
  return particles;
}

function drawParticle(ctx, p) {
  ctx.save();
  ctx.translate(p.x, p.y);
  ctx.rotate(p.rotation);
  ctx.strokeStyle = `rgba(255, 255, 255, ${p.opacity})`;
  ctx.fillStyle = `rgba(255, 255, 255, ${p.opacity * 0.3})`;
  ctx.lineWidth = 0.8;

  switch (p.type) {
    case 'triangle':
      ctx.beginPath();
      ctx.moveTo(0, -p.size);
      ctx.lineTo(-p.size * 0.7, p.size * 0.5);
      ctx.lineTo(p.size * 0.7, p.size * 0.5);
      ctx.closePath();
      ctx.stroke();
      break;
    case 'rect':
      ctx.strokeRect(-p.size/2, -p.size/2, p.size, p.size * 0.6);
      break;
    case 'diamond':
      ctx.beginPath();
      ctx.moveTo(0, -p.size);
      ctx.lineTo(p.size * 0.6, 0);
      ctx.lineTo(0, p.size);
      ctx.lineTo(-p.size * 0.6, 0);
      ctx.closePath();
      ctx.stroke();
      break;
    case 'dot':
      ctx.beginPath();
      ctx.arc(0, 0, p.size * 0.3, 0, Math.PI * 2);
      ctx.fill();
      break;
    case 'line':
      ctx.beginPath();
      ctx.moveTo(-p.size, 0);
      ctx.lineTo(p.size, 0);
      ctx.stroke();
      break;
  }
  ctx.restore();
}
```

Particle counts:
- Large spike (crisis-level): 80–150 particles
- Medium spike: 30–60 particles
- Small spike: 10–20 particles

### Step 5: Annotations

```javascript
function drawAnnotation(ctx, x, y, label, leaderEndX, leaderEndY) {
  // Leader line
  ctx.strokeStyle = 'rgba(255, 255, 255, 0.5)';
  ctx.lineWidth = 0.5;
  ctx.setLineDash([2, 3]);
  ctx.beginPath();
  ctx.moveTo(x, y);
  ctx.lineTo(leaderEndX, leaderEndY);
  ctx.stroke();
  ctx.setLineDash([]);

  // Label
  ctx.font = '10px "Berkeley Mono", monospace';
  ctx.fillStyle = 'rgba(255, 255, 255, 0.85)';
  ctx.textAlign = 'left';
  ctx.fillText(label.toUpperCase(), leaderEndX + 6, leaderEndY + 3);
}
```

### Step 6: Axes

Axes are minimal — just a baseline and tick marks:

```javascript
// X-axis (time)
ctx.strokeStyle = 'rgba(255, 255, 255, 0.3)';
ctx.lineWidth = 0.5;
ctx.beginPath();
ctx.moveTo(marginLeft, height - marginBottom);
ctx.lineTo(width - marginRight, height - marginBottom);
ctx.stroke();

// Tick marks + labels
timeLabels.forEach(({ x, label }) => {
  ctx.beginPath();
  ctx.moveTo(x, height - marginBottom);
  ctx.lineTo(x, height - marginBottom + 6);
  ctx.stroke();

  ctx.font = '9px "Berkeley Mono", monospace';
  ctx.fillStyle = 'rgba(255, 255, 255, 0.6)';
  ctx.textAlign = 'center';
  ctx.fillText(label, x, height - marginBottom + 18);
});

// Y-axis label (rotated)
ctx.save();
ctx.translate(20, height / 2);
ctx.rotate(-Math.PI / 2);
ctx.font = '10px "Berkeley Mono", monospace';
ctx.fillStyle = 'rgba(255, 255, 255, 0.6)';
ctx.textAlign = 'center';
ctx.fillText('MAGNITUDE: BANK FAILURES & ASSETS', 0, 0);
ctx.restore();
```

---

## Composition Guidelines

### Layout
- Full-bleed dark background
- Chart area: ~80% of canvas width, centered
- Generous margins for axis labels and annotations
- Y-axis label runs vertically along left edge
- X-axis runs along bottom with sparse tick marks
- Annotations positioned in negative space (calm areas)

### Visual Hierarchy (brightest → dimmest)
1. Spike peaks and debris particles (full white, 1.0 opacity)
2. Front ridge lines (0.8–1.0 opacity)
3. Cross-hatching fills (0.4–0.6 opacity)
4. Annotation text (0.85 opacity)
5. Back ridge lines (0.3–0.5 opacity)
6. Axis lines and ticks (0.3 opacity)
7. Leader lines (0.5 opacity, dashed)

### Scale & Proportion
- The tallest spike should be 60–80% of total canvas height
- Baseline ridge lines occupy the bottom 20–30%
- Debris field extends 10–15% above the spike peak
- Annotations sit in the middle ground between baseline and spike peaks

---

## File References

- **Color tokens & typography:** Defined above in this file
- **Rendering techniques (canvas patterns, hatching, particles):** `references/rendering.md`
- **Data mapping & scale strategies:** `references/data-mapping.md`
- **Example compositions & layout grids:** `references/compositions.md`
