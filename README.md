# HyperCube 4D — Interactive Tesseract Visualization

**Live demo:** https://majhrs16-official.github.io/Hypercube/

Single-file, zero-dependency (except Three.js) interactive 4D hypercube (tesseract) visualization built with geometric algebra (Clifford algebra) rotors.

## Features

- **Real 4D geometry**: 8 cubic cells × 8 vertices = 64 vertices in 4D, projected to 3D frustums via perspective projection
- **Clifford algebra rotors**: 7-component rotors (1 scalar + 6 bivectors: XY, XZ, XW, YZ, YW, ZW) — double cover of SO(4)
- **Perspective projection 4D→3D**: `scale = projDist / (projDist - w)` — no stereoscopy, pure math
- **Interactive controls**:
  - Drag / 1-finger: orbit 3D camera
  - Shift+Drag / 2-finger drag: rotate hypercube in 4D (XW/YW planes)
  - Scroll / Pinch: zoom projection distance
  - Auto-rotation across 4 planes simultaneously
- **Touch support**: Full mobile/touchscreen interaction
- **Camera position display**: Real-time X, Y, Z, Radius readout
- **Single HTML file**: `index.html` + local `three.min.js` — works offline, on GitHub Pages, anywhere

## Controls

| Input | Action |
|-------|--------|
| Drag / 1-finger | Rotate 3D view (orbit camera) |
| Shift+Drag / 2-finger drag | Rotate 4D (XW/YW planes) |
| Scroll / Pinch | Zoom projection distance |
| Auto Rotate button | Toggle 4-plane continuous rotation |
| Reset View | Return to default orientation |
| Wireframe / Cells | Toggle render mode |
| Sliders | Fine control of each 4D rotation plane |

## Math

The tesseract's 8 cells are defined by fixing one coordinate (X, Y, Z, or W) to ±1. Each cell has 8 vertices forming a 3D cube in 4D space.

Rotations use **geometric algebra rotors** in 4D:
```
R = s + xy·e₁₂ + xz·e₁₃ + xw·e₁₄ + yz·e₂₃ + yw·e₂₄ + zw·e₃₄
v' = R v R̃  (sandwich product)
```

Perspective projection from 4D camera at `(0,0,0,projDist)`:
```
(x, y, z, w) → (x, y, z) * projDist / (projDist - w)
```

## Files

- `index.html` — Complete application (HTML + CSS + JS)
- `three.min.js` — Three.js r155 (UMD build, exposes global `THREE`)

## Run locally

```bash
# Option 1: Python
python3 -m http.server 8080

# Option 2: Node
npx serve .

# Option 3: Open directly in browser (file:// works since no ES modules)
xdg-open index.html
```

## License

MIT — do whatever you want with it.