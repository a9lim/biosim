# Cellular Metabolism

An interactive HTML5 Canvas simulation of cellular carbon metabolism and electron transport chains.

## Overview

This project visualizes the interconnected nature of 8 major biochemical systems within a photosynthetic cell. Users trace the flow of carbon, electrons, and energy (ATP/NADP(H)) by clicking on enzymatic reactions to advance the simulation step-by-step.

Rather than treating pathways as isolated diagrams, the simulator uses **shared metabolite nodes** (e.g., Fructose-6-Phosphate) in an orthogonal grid layout, demonstrating how pathways like Glycolysis, the Calvin Cycle, and the Pentose Phosphate Pathway naturally intersect.

## Key Features

- **Click-to-React** — Manually advance metabolic flux by clicking enzymatic arrows. Available reactions are highlighted based on current metabolite, ATP, and redox coenzyme levels.
- **Biochemical Accuracy** — Reversible enzymes (Aldolase, PGI, etc.) calculate substrate/product availability dynamically. Clicking in reverse consumes the product and returns the substrate.
- **Orthogonal Grid Layout** — Cytoplasmic carbon architecture (Glycolysis, Calvin, PPP, Krebs) mapped to a strict column-and-row system.
- **Unrolled Krebs Block** — The citric acid cycle integrated as a 3x3 logical circuit beneath Glycolysis.
- **Dynamic Shared Reactions** — Enzymes shared between pathways (TKT/TAL, TK/SBP) adapt colors based on which pathways are active.
- **Live Bioenergetic Tracking** — Global cellular pools of ATP/ADP and NADH/NAD+ shown as real-time percentage bars.
- **Light / Dark Themes** — Sunlight toggle shifts the canvas and UI between dark glassmorphism and light mode.

## Pathways

1. Glycolysis
2. Pentose Phosphate Pathway (PPP)
3. Calvin Cycle (Carbon Fixation)
4. Krebs Cycle (Citric Acid Cycle)
5. Linear Light-Dependent Reactions (Z-scheme)
6. Cyclic Light-Dependent Reactions (PSI cyclic flow)
7. Oxidative Phosphorylation (Respiratory ETC)
8. Fermentation (Ethanol pathway when anoxic)

## Tech Stack

- **HTML5 Canvas** — Custom 2D rendering pipeline (`renderer.js`, `enzymes.js`)
- **Vanilla JavaScript** — State tracking and bio-logic without frameworks (`sim.js`)
- **Pure CSS** — Glassmorphism UI, sidebar controls, responsive styling (`styles.css`)
- Zero external dependencies

## Running Locally

```bash
npx serve .
# or: python -m http.server 3000
```

Open `http://localhost:3000` in your browser.

## File Structure

| File | Purpose |
|------|---------|
| `index.html` | Application shell, DOM controls, dashboard UI |
| `styles.css` | Visual styling for the HTML interface |
| `colors.js` | Design tokens, color math, CSS custom property injection |
| `anim.js` | Easing functions, fade trackers, trail ring-buffers |
| `enzymes.js` | Drawing routines for membrane proteins, shared nodes, labels |
| `renderer.js` | Canvas 2D engine — layout, zoom/pan, hit detection, draw pipeline |
| `sim.js` | Simulation engine — metabolite store, reaction logic, autoplay loop |
