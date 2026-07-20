# Chroma — K-Means Color Lab

A polished, single-file web app that teaches **K-Means clustering** by doing
**image color quantization** — reducing any photo to *K* colors. Built as a
teaching tool for a high-school / early-college AI class.

**▶ Live app:** https://lemoon01110.github.io/chroma-kmeans-color-lab/

Everything runs **client-side in your browser**. No image is ever uploaded to a
server, and the whole thing works **offline** once the page has loaded.

---

## What it does

- **Load a photo** — drag & drop, file picker, or one of 4 built-in sample images.
- **Pick K (2–32)** with a big slider; the image re-quantizes live as you drag.
- Runs **K-Means** on the image's pixels in color space, then repaints every
  pixel with its cluster's average color.
- Shows the **original and reduced** image side by side, plus a draggable
  **before/after compare slider**.
- Displays the **palette the algorithm discovered** as swatches — each with its
  hex code (click to copy) and the % of the image it covers, sortable by
  coverage or luminance.

### Extras
- **Watch it learn** — replay the K-Means iterations with play / pause / step,
  a live iteration counter, and a "converged" indicator.
- **Exports** — reduced PNG, palette as JSON, palette as CSS variables, and a
  swatch PNG.
- **Options** — color space (RGB / LAB), initialization (random / k-means++),
  and a re-seed button so students can see results vary.
- **"How this works"** explainer with a color-cube diagram and a live 2-D
  K-Means animation.
- Light / dark mode, keyboard-operable, ARIA labels, WCAG-AA contrast.

## Performance
Large images are internally downscaled for the clustering step, and K-Means runs
in a **Web Worker** so dragging the slider never freezes the page. Slider-driven
recomputes are debounced.

## Running it
It's a single self-contained HTML file — no build step, no dependencies, no CDN.

- **Online:** open the live link above.
- **Offline:** download [`index.html`](index.html) and double-click it, or:
  ```bash
  git clone https://github.com/lemoon01110/chroma-kmeans-color-lab.git
  cd chroma-kmeans-color-lab
  # then just open index.html in any modern browser
  ```

## For students reading the source
The K-Means loop lives in the `WORKER_SOURCE` string inside `index.html` and is
commented step-by-step: **assign** each pixel to its nearest marker → **move**
each marker to the average of its pixels → **repeat** until it **converges**.
Because nobody labels the pixels, this is *unsupervised* learning: the palette is
a rule the algorithm discovered on its own.

## License
[MIT](LICENSE) — free to use, modify, and share in your classroom.
