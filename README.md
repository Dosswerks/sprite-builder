# Sprite Builder

A browser-based pixel art editor for building video game sprites with frame animation support.

---

## Features

- Custom pixel dimensions (up to 512×512)
- Multi-frame animation support (up to 64 frames)
- Zoomed pixel grid with transparency checkerboard
- Grid lines at high zoom levels
- Bresenham line interpolation for smooth painting

### Tools

- Pencil: Paint individual pixels
- Eraser: Remove pixels to transparent
- Eyedropper: Pick a color from the canvas
- Flood Fill: Fill contiguous areas with the selected color
- Full 16-million color picker

### Frame Operations

- Frame thumbnail bar with click-to-switch
- Copy and paste between frames
- Add frames on the fly
- Import any image file (auto-scaled to sprite dimensions)
- Clear individual frames

### Rehearsal Stage

- Plays the animation at actual pixel size
- Adjustable FPS (1–60)
- Play/pause toggle
- Scaled preview for visibility

### Export

- Export each frame as a transparent PNG
- Custom filename per frame
- Download individually or all at once

## Controls

### Mouse/Touch

- Click/drag on the canvas to paint or erase
- Click a frame thumbnail to switch frames

### Keyboard Shortcuts

| Key | Action |
|---|---|
| P | Pencil tool |
| E | Eraser tool |
| I | Eyedropper tool |
| F | Flood fill tool |
| [ | Previous frame |
| ] | Next frame |

## Getting Started

1. Open `index.html` in any modern browser
2. Enter the pixel width, height, and number of frames
3. Click "Start Editing"
4. Paint pixels, import images, or both
5. Use the Rehearsal stage to preview animations
6. Export frames as transparent PNGs when finished

## Technical Details

Single-file HTML5 Canvas application with no external dependencies. All rendering, input handling, and export logic contained in one `index.html`. Works on desktop and mobile browsers.

Canvas rendering uses `willReadFrequently` optimization for pixel-level read/write operations. Export uses `canvas.toDataURL('image/png')` for lossless transparent output.

---

## Credits

Built with Kiro AI-assisted development

Concept and design: [Andrew Doss](https://www.andrewdoss.com/)
