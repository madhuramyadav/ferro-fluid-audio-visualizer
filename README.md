# Kinetic Alien — Ferrofluid Audio Visualizer

A mesmerizing 3D audio visualizer inspired by **ferrofluid** and Marvel's **Venom symbiote**. A dark, metallic blob morphs and spikes in real-time, reacting to music or your microphone.

Built with **Three.js** and the **Web Audio API** — runs entirely in the browser, no install needed.

[![Live Demo](https://img.shields.io/badge/Live%20Demo-Visit-brightgreen?style=for-the-badge)](https://ferro-fluid-audio-visualizer.vercel.app)

---

## Preview

<!-- Replace these with actual screenshots/recordings once deployed -->

| Ferrofluid (Orange) | Venom (Dark Indigo) | Mercury (White on Black) |
|:---:|:---:|:---:|
| ![Ferrofluid Theme](./assets/preview-ferrofluid.png) | ![Venom Theme](./assets/preview-venom.png) | ![Mercury Theme](./assets/preview-mercury.png) |

> **Video demo:** [Watch on YouTube](#) _(coming soon)_

---

## Features

- **Ferrofluid physics** — organic spikes and tendrils grow from a metallic blob, driven by audio frequencies
- **6 stunning themes** — Ferrofluid (orange), Venom (indigo), Mercury (white/black), Ocean (navy), Crimson (red), Ember (gold)
- **Dual audio input** — use your microphone or load any audio file
- **Real-time frequency analysis** — bass creates large pulses, mids form spiky protrusions, highs produce fine needles
- **Always alive** — subtle organic motion even without audio, like a living symbiote
- **Touch-optimized** — drag to rotate, pinch to zoom, tap to toggle controls — works great on tablets
- **Gain control** — adjust audio sensitivity to match your environment
- **Smooth theme transitions** — colors blend seamlessly when switching themes
- **Zero dependencies** — single HTML file, Three.js loaded from CDN
- **Cinematic look** — metallic shaders with Fresnel reflections, iridescence, multi-light setup, and vignette overlay

---

## Themes

| Theme | Background | Liquid | Vibe |
|-------|-----------|--------|------|
| **Ferrofluid** | Warm orange | Black metallic | Classic ferrofluid in a lab |
| **Venom** | Dark indigo | Black with blue sheen | Marvel symbiote |
| **Mercury** | Pure black | White / silver | Liquid metal T-1000 |
| **Ocean** | Deep navy | Black with cyan specular | Deep sea creature |
| **Crimson** | Dark red | Black with red highlights | Carnage vibes |
| **Ember** | Dark amber | Black with gold specular | Molten metal |

---

## Getting Started

### Run locally

No build step — just open the file:

```bash
# Clone the repo
git clone https://github.com/madhuramyadav/ferro-fluid-audio-visualizer.git
cd ferro-fluid-audio-visualizer

# Open in browser
open index.html        # macOS
start index.html       # Windows
xdg-open index.html    # Linux
```

Or use a local server (recommended for audio file loading):

```bash
npx serve .
# or
python -m http.server 8000
```

### Deploy to Vercel

1. Push this repo to GitHub
2. Import in [Vercel](https://vercel.com) — zero config needed
3. Done. It's a single HTML file.

---

## How It Works

```
Microphone / Audio File
        │
        ▼
   Web Audio API
   (AnalyserNode)
        │
        ▼
  FFT Frequency Data
  ┌─────┬──────┬──────┬───────┬──────┐
  │Bass │LowMid│ Mid  │HiMid  │ High │
  └──┬──┴──┬───┴──┬───┴──┬────┴──┬───┘
     │     │      │      │       │
     ▼     ▼      ▼      ▼       ▼
  Large  Medium  Spiky  Sharp   Fine
  pulses bumps   peaks  spikes  needles
        │
        ▼
  Vertex Shader (Simplex Noise × Audio)
        │
        ▼
  Fragment Shader (Metallic Material)
  • Fresnel reflections
  • Multi-light setup
  • Iridescence
  • Tone mapping
```

### Tech Stack

| Layer | Technology |
|-------|-----------|
| 3D Rendering | [Three.js](https://threejs.org/) (r160) |
| Audio Analysis | Web Audio API (AnalyserNode, FFT) |
| Geometry | IcosahedronGeometry (detail 6, ~40K vertices) |
| Shading | Custom GLSL vertex + fragment shaders |
| Noise | Simplex 3D noise (Ashima Arts) |
| Hosting | Vercel (static) |

---

## Controls

| Action | Desktop | Tablet / Mobile |
|--------|---------|----------------|
| Rotate view | Click + drag | Touch + drag |
| Zoom | Scroll wheel | Pinch |
| Show/hide controls | Click canvas | Tap canvas |
| Switch theme | Click swatch | Tap swatch |
| Start microphone | Click mic button | Tap mic button |
| Load audio file | Click music button | Tap music button |
| Play/Pause | Click play/pause | Tap play/pause |
| Adjust sensitivity | Drag gain slider | Drag gain slider |

---

## Browser Support

| Browser | Supported |
|---------|-----------|
| Chrome / Edge | Yes |
| Safari (macOS / iOS) | Yes |
| Firefox | Yes |
| Samsung Internet | Yes |

Requires **WebGL** and **Web Audio API** support. Works on tablets (iPad, Android) with touch controls.

---

## Project Structure

```
ferro-fluid-audio-visualizer/
├── index.html      # The entire app — HTML, CSS, shaders, and JS
├── assets/         # Screenshots & preview images
└── README.md
```

Yes, it's a single file. That's the point.

---

## Contributing

1. Fork the repo
2. Create a feature branch (`git checkout -b feature/cool-effect`)
3. Commit your changes
4. Push and open a PR

Ideas for contributions:
- New themes
- Post-processing effects (bloom, chromatic aberration)
- Audio waveform display
- Preset animations
- WebXR / VR support

---

## License

MIT License — see [LICENSE](LICENSE) for details.

---

## Acknowledgments

- [Three.js](https://threejs.org/) — 3D rendering
- [Ashima Arts](https://github.com/ashima/webgl-noise) — Simplex noise GLSL implementation
- Inspired by real ferrofluid physics and Marvel's Venom

---

<p align="center">
  <strong>Built with obsession by <a href="https://github.com/madhuramyadav">Madhuram Yadav</a></strong>
</p>
