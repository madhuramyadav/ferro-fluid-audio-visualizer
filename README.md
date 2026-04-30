# Kinetic Alien — Audio Visualizer

A mesmerizing 3D audio visualizer with **12 visualization modes**, **6 color themes**, and **3 view styles**. Inspired by ferrofluid, Marvel's Venom, and sci-fi organisms.

Built with **Three.js** and the **Web Audio API** — runs entirely in the browser as a single HTML file. No install, no build step.

[![Live Demo](https://img.shields.io/badge/Live%20Demo-Visit-brightgreen?style=for-the-badge)](https://ferro-fluid-audio-visualizer.vercel.app)

---

## Preview

<!-- Replace with actual screenshots/recordings once deployed -->

| Spikes | Blob | Helix |
|:---:|:---:|:---:|
| ![Spikes](./assets/preview-spikes.png) | ![Blob](./assets/preview-blob.png) | ![Helix](./assets/preview-helix.png) |

| Jellyfish | Fireworks | Galaxy |
|:---:|:---:|:---:|
| ![Jellyfish](./assets/preview-jellyfish.png) | ![Fireworks](./assets/preview-fireworks.png) | ![Galaxy](./assets/preview-galaxy.png) |

> **Video demo:** [Watch on YouTube](#) _(coming soon)_

---

## 12 Visualization Modes

| Mode | Description |
|------|-------------|
| **Spikes** | Tiny core sphere + 120 thin cone needles that grow with audio |
| **Blob** | Connected liquid sphere with vertex displacement — organic ferrofluid |
| **Bars** | 64 radial equalizer bars arranged in a circle |
| **Wave** | Circular ribbon ring that undulates with frequency data |
| **Helix** | Double DNA spiral of 120 pulsing spheres |
| **Particles** | 500 dots that explode outward on beats and drift back |
| **Rings** | 5 stacked torus rings, each reacting to a different frequency band |
| **Tendrils** | 8 organic tentacles that wave and extend — Venom/alien feel |
| **Galaxy** | 3-arm spiral of stars rotating and pulsing with audio |
| **Jellyfish** | Translucent dome + 10 trailing tentacles, sways and pulses |
| **Heartbeat** | 3D heart shape with ECG waveform ring — pulses with bass |
| **Fireworks** | Particle bursts that shoot outward on every beat with gravity |

Switch modes instantly via the **Style** dropdown in the controls bar.

---

## 6 Color Themes

| Theme | Background | Liquid | Vibe |
|-------|-----------|--------|------|
| **Ferrofluid** | Warm orange | Black metallic | Classic ferrofluid in a lab |
| **Venom** | Dark indigo | Black with blue sheen | Marvel symbiote |
| **Mercury** | Pure black | White / silver | Liquid metal T-1000 |
| **Ocean** | Deep navy | Black with cyan specular | Deep sea creature |
| **Crimson** | Dark red | Black with red highlights | Carnage vibes |
| **Ember** | Dark amber | Black with gold specular | Molten metal |

Themes transition smoothly with color blending.

---

## 3 View Modes

| View | Effect |
|------|--------|
| **Free** | Full screen, no frame |
| **Display** | Circular viewport with glow backlight — like a physical ferrofluid display |
| **Spotlight** | Glow backlight, no frame |

Display mode scales the visualization to 50% to fit inside the circular viewport.

---

## Audio Input

### Microphone
Click the mic button to see a source selector:
- **Tab / System Audio** (desktop Chrome/Edge only) — captures audio directly from a browser tab (e.g. YouTube). No extra software needed.
- **Microphone devices** — pick any connected mic to capture ambient audio.

### Audio File
Click the music button to load any audio file from your device. Works on all platforms including tablets.

### Gain Control
Adjust the sensitivity slider to match your audio source. Visualization is capped to prevent overflow regardless of gain level.

---

## Features

- **12 visualization modes** — from ferrofluid spikes to DNA helixes to fireworks
- **6 color themes** — with smooth transitions
- **3 view modes** — Free, Display (circular frame), Spotlight
- **Multiple audio sources** — mic, audio file, tab audio capture
- **Audio source selector** — pick from available input devices
- **Touch-optimized** — drag to rotate, pinch to zoom, tap to toggle controls
- **Tablet-friendly** — Wake Lock API keeps screen on during visualization
- **Gain control** — adjust sensitivity with capped output
- **Fast-attack / slow-release** — spikes snap up on beats, slowly retract
- **Zero dependencies** — single HTML file, Three.js loaded from CDN
- **Responsive** — works on desktop, tablet, and mobile

---

## Getting Started

### Run locally

No build step — just serve it:

```bash
# Clone the repo
git clone https://github.com/madhuramyadav/ferro-fluid-audio-visualizer.git
cd ferro-fluid-audio-visualizer

# Serve locally (required for mic access)
npx serve .
# or
python -m http.server 8000
```

Then open `http://localhost:3000` (or `:8000`).

> **Note:** Microphone access requires HTTPS or localhost. Opening `index.html` directly via `file://` won't allow mic input, but audio file loading still works.

### Deploy to Vercel

1. Push this repo to GitHub
2. Import in [Vercel](https://vercel.com) — zero config needed
3. Done. It's a single HTML file.

---

## How It Works

```
Audio Source (Mic / File / Tab Audio)
        │
        ▼
   Web Audio API (AnalyserNode)
        │
        ▼
   FFT → 256 Frequency Bins
        │
   ┌────┴────────────────────────┐
   │  5 Frequency Bands          │
   │  Bass │ LowMid │ Mid │ ... │
   └────┬────────────────────────┘
        │
        ▼
   Active Visualization Mode
   (Spikes / Blob / Bars / ...)
        │
        ▼
   Three.js Render → Canvas
```

### Tech Stack

| Layer | Technology |
|-------|-----------|
| 3D Rendering | [Three.js](https://threejs.org/) r160 |
| Audio Analysis | Web Audio API (AnalyserNode, FFT) |
| Visualizations | InstancedMesh, BufferGeometry, vertex displacement |
| Screen Wake | Wake Lock API |
| Tab Audio | getDisplayMedia API |
| Hosting | Vercel (static) |

---

## Controls

| Action | Desktop | Tablet |
|--------|---------|--------|
| Rotate view | Click + drag | Touch + drag |
| Zoom | Scroll wheel | Pinch |
| Show/hide controls | Click canvas | Tap canvas |
| Switch theme | Click color swatch | Tap swatch |
| Switch viz mode | Style dropdown | Style dropdown |
| Switch view | Free / Display / Spotlight buttons | Same |
| Audio source | Click mic → select source | Tap mic → select |
| Load audio file | Click music button | Tap music button |
| Play/Pause | Click play/pause | Tap play/pause |
| Adjust sensitivity | Drag gain slider | Drag gain slider |

---

## Browser Support

| Browser | Mic | Tab Audio | Audio File |
|---------|-----|-----------|------------|
| Chrome / Edge (desktop) | Yes | Yes | Yes |
| Chrome (Android) | Yes | Partial | Yes |
| Safari (iOS 16.4+) | Yes | No | Yes |
| Firefox | Yes | No | Yes |
| Samsung Internet | Yes | No | Yes |

Requires **WebGL** and **Web Audio API**. Wake Lock keeps tablet screens on during playback.

---

## Project Structure

```
ferro-fluid-audio-visualizer/
├── index.html      # The entire app (HTML + CSS + JS)
├── assets/         # Screenshots & preview images
└── README.md
```

Single file. Zero build. That's the point.

---

## Contributing

1. Fork the repo
2. Create a feature branch (`git checkout -b feature/cool-effect`)
3. Commit your changes
4. Push and open a PR

Ideas for contributions:
- New visualization modes
- New color themes
- Post-processing effects (bloom, chromatic aberration)
- WebXR / VR support
- Spotify / streaming integration
- Keyboard shortcuts for mode switching

---

## License

MIT License — see [LICENSE](LICENSE) for details.

---

## Acknowledgments

- [Three.js](https://threejs.org/) — 3D rendering engine
- Inspired by real ferrofluid physics, Marvel's Venom, and bioluminescent sea creatures

---

<p align="center">
  <strong>Built by <a href="https://github.com/madhuramyadav">Madhuram Yadav</a></strong>
</p>
