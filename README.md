# Rudransh Rajak — 3D Portfolio

A single-page, 3D portfolio built from scratch with **HTML, CSS and Three.js**. No build step, no framework — just open it and go.

![HTML](https://img.shields.io/badge/HTML5-E34F26?style=flat-square&logo=html5&logoColor=white)
![CSS](https://img.shields.io/badge/CSS3-1572B6?style=flat-square&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat-square&logo=javascript&logoColor=black)
![Three.js](https://img.shields.io/badge/Three.js-000000?style=flat-square&logo=three.js&logoColor=white)

## What's inside

- **3D hero scene** — a rotating wireframe icosahedron, glowing core, orbiting motes, twin ring systems and a 2,400-point dust field, all reacting to the mouse and page scroll.
- **Layered hero** — floating code card with pointer parallax, live stat strip and availability badge.
- **Scroll choreography** — IntersectionObserver reveals, animated skill bars, counting stats, scroll progress bar and active-section navigation.
- **3D tilt cards** — projects and cards respond to the cursor in perspective.
- **Custom cursor**, preloader, glassmorphism, gradient type and full responsive layout.
- **Working contact form** — validates, then opens a pre-filled email draft to the address in `assets/js/main.js`.

## Run it

Because the page uses ES modules for Three.js, it needs to be served over HTTP (not opened as a `file://` URL).

```bash
# Option 1 — VS Code: right click index.html → "Open with Live Server"

# Option 2 — any static server
npx serve .
# or
npx http-server -p 5173
```

Then visit `http://localhost:3000` (or whichever port your server prints).

## Files

```
index.html                  → all page content and sections
assets/
  css/style.css             → design system, layout, animations, responsive rules
  js/main.js                → preloader, cursor, nav, reveals, counters, tilt, form
  js/three-scene.js         → Three.js hero scene
  js/vendor/three.module.js → Three.js r161 (self-hosted, works offline)
  favicon.svg               → monogram favicon
```

## Customizing

**Colors / fonts** — edit the tokens at the top of `assets/css/style.css`:

```css
:root {
  --bg: #05060a;
  --cyan: #67e8f9;
  --violet: #a78bfa;
  --pink: #f0abfc;
  --grad: linear-gradient(115deg, #67e8f9, #a78bfa, #f0abfc);
  ...
}
```

**3D scene** — `assets/js/three-scene.js`:
- `shellGeo` / `core` — main object size and shape
- `COUNT` (2400) — dust particle count (lower it on low-end devices)
- `world.position.x = visW * 0.32` — how far right the object sits on desktop
- pointer/scroll response in `render()`

**Email** — change `const EMAIL = "..."` inside `assets/js/main.js` and the `mailto:` links in `index.html`.

## Deploying

Any static host works — drag the folder into [Netlify Drop](https://app.netlify.com/drop), connect a GitHub repo to Vercel, or push to GitHub Pages. No configuration or build command needed.

## Performance notes

- Three.js is vendored locally, so the scene works without a CDN.
- The render loop pauses when the hero leaves the viewport or the tab is hidden.
- Pixel ratio is capped at 2, and antialiasing is skipped on high-DPI screens.
- `prefers-reduced-motion` renders a single static frame and disables tilt/reveals.

---

Designed and built for **Rudransh Rajak** · Bhopal, India
