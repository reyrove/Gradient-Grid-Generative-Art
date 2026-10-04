# Gradient Grid — Generative Art

> A seed-based generative system for noisy gradient field compositions.  
> A reproducible catalogue of computational colour studies.

---

## What is this?

**Gradient Grid** is a generative design system built on a grid of seeded noise. Every cell carries a value between −450 and 450, and that value is mapped to a position along a linear gradient running between two colours drawn from a palette of sixteen. The grid itself is invisible; only the gradient remains.

Every artwork in this catalogue is defined by a single numeric seed. The same seed always produces the identical composition — making each piece **traceable, reproducible, and licensable** across textile, print, and apparel applications.

Named for the field-of-values technique at its core, **Gradient Grid** reframes noise as a textile.

---

## Live

🌐 **[View the catalogue →](https://reyrove.github.io/Gradient-Grid-Generative-Art/)**

---

## The System

The generator combines two layers:

| Layer | Description |
|-------|-------------|
| **Grid** | 10 to 159 columns, with rows derived from the column count. |
| **Gradient** | A two-colour linear gradient drawn from a 16-colour palette, sampled per cell by its noise value. |

Both layers are driven by the same seed, ensuring deterministic output.

### Parameters

- **Grid columns** — 10 to 159
- **Grid rows** — `cols − 5` to `cols + 5`
- **Cell value range** — −450 to 450
- **Palette** — 16 named colours
- **Palette pair** — 2 colours chosen per seed (start ≠ end)
- **Background** — the start colour of the gradient
- **Cell colour** — `lerp(start, end, (value + 450) / 900)`

---

## Structure

```
Gradient-Grid-Generative-Art/
├── index.html              ← Full catalogue (single-file)
├── images/
│   ├── fav.svg
│   ├── gradientgrid-tote.png
│   ├── gradientgrid-cushion.png
│   └── ...
├── Gradient-Grid.jpg       ← Apparel mockup
└── README.md
```

The entire project is contained in a single `index.html` — no build step, no framework. The only external dependency is **p5.js** (loaded from CDN), which drives the exact sketch pipeline.

---

## Features

- **Seed-based generation** — every composition is deterministic and reproducible
- **Same seed, many surfaces** — the plate, cover, framed print, and all four surface swatches render from the same seed
- **Tiled rectangular surfaces** — scarves, textiles, and wallpaper tile the square composition to fill their aspect ratio, preserving the visual identity
- **Archive of 8 seeds** — each thumbnail is a *different* composition; click one to load it into the plate, and every surface follows
- **Live animation** — the plate runs continuously; the cover and framed plate auto-stop after 2 seconds
- **PNG export** — download the current frame of the plate directly from the browser
- **Keyboard shortcuts** — `R` for new seed, `S` to save
- **Legal modal** — licensing, terms, and credits built in
- **Responsive** — works on desktop, tablet, and mobile
- **Mobile-first navbar** — horizontally scrollable with fade hint

---

## Usage

### Generate a new composition

Click **New Seed** or press `R`.

### Download the current frame

Click **Download** or press `S`.

### Load a seed from the archive

Click any plate in the **Archive** section. The plate, cover, framed print, and every surface swatch update to that seed.

---

## Color System

Every composition is drawn from a palette of sixteen named colours:

| Colour | RGB |
|--------|-----|
| **red** | 255, 0, 0 |
| **blue** | 0, 0, 255 |
| **yellow** | 255, 255, 0 |
| **green** | 0, 255, 0 |
| **black** | 0, 0, 0 |
| **cyan** | 0, 255, 255 |
| **white** | 255, 255, 255 |
| **magenta** | 255, 0, 255 |
| **orange** | 255, 165, 0 |
| **purple** | 128, 0, 128 |
| **pink** | 255, 105, 180 |
| **teal** | 0, 128, 128 |
| **navy** | 0, 0, 128 |
| **maroon** | 128, 0, 0 |
| **olive** | 128, 128, 0 |
| **beige** | 245, 245, 220 |

Each seed picks a **pair** of colours — one for the start of the gradient, one for the end. Every cell's value determines where along that gradient it sits. Because the seed picks both the palette and the grid values, no two compositions share the same rhythm of colour and structure.

---

## Surfaces — one seed, many ratios

Every surface in the catalogue is drawn from the same seed. The rectangular surfaces tile the square composition to fill their aspect ratio:

| Surface | Ratio | Tiling |
|---------|-------|--------|
| **Print** | 1 : 1 | 1 × 1 — identical to the plate |
| **Scarf** | 3 : 1 | 3 × 1 — composition repeated 3× horizontally |
| **Textile** | 4 : 3 | 2 × 2 — composition repeated 2× in both directions |
| **Wall** | 2 : 3 | 1 × 2 — composition repeated 2× vertically |

Every tile uses the same seed with a fresh RNG reset, so all tiles are visually identical. This is exactly what a repeat pattern looks like — one motif, tiled.

---

## Technical Notes

- **p5.js** drives the composition. `rect()` and `fill()` are used natively.
- **Seeded randomness** uses a Lehmer LCG. Same seed → same palette pair, same grid dimensions, same cell values, same composition.
- **Live plate** — 30fps. The plate's `draw()` runs continuously until the page is hidden.
- **Cover and framed plate** — 20fps, auto-stop after 2 seconds.
- **Frozen stills** — the four surface swatches and eight archive thumbnails run 2 frames then freeze.
- **Off-screen pause** — an `IntersectionObserver` calls `noLoop()` on live instances that scroll out of view.
- **`prefers-reduced-motion` respected.**

---

## About

**Gradient Grid** is a project by [Reyhaneh Daneshdoost](https://reyrove.github.io/) — an Iranian-born artist working at the intersection of classical textile logic and generative systems.

The work begins with a simple observation: the woven surface — repetitive, mathematically structured, infinitely variable — has always been a form of computation, long before computers.

**Gradient Grid** is an attempt to render that logic visible.

> *A grid is not a picture of order — it is a way to organise chaos.*

---

## Licensing

All compositions are seed-documented and available for licensing across textile, surface, and apparel applications.

For commercial use, custom editions, or exclusive rights:

📧 **reyhanehdaneshdoost@gmail.com**

See the **Licensing** section in the live catalogue for details.

---

## Links

- 🌐 [Website](https://reyrove.github.io/)
- 📷 [Instagram](https://www.instagram.com/rey._.rove/)
- 💼 [LinkedIn](https://www.linkedin.com/in/reyhaneh-daneshdoost-730481160/)
- 🐦 [X](https://x.com/reyrove)

---

## Credits

**Design & Generative System**  
Reyhaneh Daneshdoost

**Typefaces**  
Cormorant Garamond · DM Mono

**Edition**  
Gradient Grid — Autumn 2026

---

<p align="center">
  <em>Generative Gradient Field</em><br />
  <sub>© Reyrove Studio · All compositions reproducible by seed</sub>
</p>