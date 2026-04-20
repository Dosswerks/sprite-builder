# Sprite Builder

A browser-based pixel art editor for building video game sprites with frame animation support.

---

## Features

- Custom pixel dimensions (up to 512×512)
- Multi-frame animation support (up to 64 frames)
- Zoomed pixel grid with transparency checkerboard
- Grid lines at high zoom levels
- Bresenham line interpolation for smooth painting
- Dual-sidebar layout with grouped tools
- Responsive collapse to horizontal toolbar on narrow viewports (≤600px)
- Custom logo support (setup screen and editor)

### Tools

- Pencil: Paint individual pixels
- Eraser: Remove pixels to transparent
- Eyedropper: Pick a color from the canvas
- Flood Fill: Fill contiguous areas with the selected color
- Selection: Marquee rectangle select for copy, cut, paste, move, rotate, and flip
- Full 16-million color picker

### Selection & Transform

- Marquee rectangle selection with dashed border overlay
- Copy, cut, and paste selected pixel regions (Ctrl+C/X/V)
- Floating paste overlay — drag to reposition before committing
- Rotate 90° clockwise or counter-clockwise
- Flip horizontally
- Works within the same frame or across frames
- All operations are undoable

### Frame Operations

- Three-layer frame bar: editable export name, thumbnail, source label
- Source labels track provenance: "New frame", "Copied from Frame N", or "Imported: filename.png"
- Prev/Next frame navigation buttons
- Copy and paste between frames
- Add frames on the fly
- Import any image file (auto-scaled to sprite dimensions)
- Clear or delete individual frames

### Rehearsal Stage

- Dual-canvas preview: enlarged view and true 1:1 pixel-size view side by side
- Both canvases animate in sync
- Adjustable FPS (1–60)
- Play/pause toggle

### Export

- Export each frame as a transparent PNG
- Custom filename per frame (editable in frame bar or export modal)
- Download individually or all at once (frame index order)

### Save / Load

- Save project as `.sprb` JSON file (includes all frame data, names, and source labels)
- Load `.sprb` or `.json` project files
- Backward compatible — loads older projects without source labels

## Editor Layout

```
┌──────────┬─────────────────────────────┬──────────────┐
│ LEFT     │         Frame Bar           │ RIGHT        │
│ SIDEBAR  │  [name] [name] [name] [+]   │ SIDEBAR      │
│          │  [thumb] [thumb] [thumb]     │              │
│ File     │  [src]  [src]  [src]        │ Frame Actions│
│ Drawing  ├─────────────────────────────┤ Clipboard    │
│ Tools    │                             │ Transform    │
│ Color    │       Canvas Area           │ Edit         │
│ Output   │                             │              │
│          │                             │              │
│ [logo]   │                             │              │
└──────────┴─────────────────────────────┴──────────────┘
```

## Controls

### Mouse/Touch

- Click/drag on the canvas to paint or erase
- Click a frame thumbnail to switch frames
- With Selection tool: click and drag to select, drag floating overlay to reposition
- Click outside selection or press Escape to deselect
- Press Enter to commit floating selection

### Keyboard Shortcuts

| Key | Action |
|---|---|
| P | Pencil tool |
| E | Eraser tool |
| I | Eyedropper tool |
| F | Flood fill tool |
| S | Selection tool |
| [ | Previous frame |
| ] | Next frame |
| Ctrl+Z / Cmd+Z | Undo |
| Ctrl+C / Cmd+C | Copy selection |
| Ctrl+X / Cmd+X | Cut selection |
| Ctrl+V / Cmd+V | Paste selection |
| Escape | Deselect / commit floating |
| Enter | Commit floating selection |

## Custom Logo

Place logo images in the `assets/` folder:

- `assets/logo.png` — Large logo for the setup screen (max 320×120px). Replaces the "Sprite Builder" title.
- `assets/logo-small.png` — Small logo for the editor sidebar (max 140×80px). Appears below the left sidebar menus.

If the logo files are not found, the text title is shown as fallback.

## Getting Started

1. Open `index.html` in any modern browser
2. Enter the pixel width, height, and number of frames
3. Click "Start Editing"
4. Paint pixels, import images, or both
5. Use the Selection tool to copy, move, rotate, and flip pixel regions
6. Use the Rehearsal stage to preview animations at both enlarged and actual size
7. Export frames as transparent PNGs when finished
8. Save your project as a `.sprb` file to resume later

## Technical Details

Single-file HTML5 Canvas application with no external dependencies. All rendering, input handling, and export logic contained in one `index.html`. Works on desktop and mobile browsers.

- Canvas rendering uses `willReadFrequently` optimization for pixel-level read/write operations
- Export uses `canvas.toDataURL('image/png')` for lossless transparent output
- 30-level undo stack (pixel operations only; frame add/delete are not undoable)
- Flood fill uses exact RGBA byte equality (no tolerance)
- Touch input: single-touch only, multi-touch ignored, `touch-action: none` on canvas
- Responsive: sidebars collapse to horizontal toolbar at ≤600px viewport width

## File Structure

```
sprite-builder/
  index.html          — Complete application
  README.md           — This file
  assets/
    logo.png          — Optional: setup screen logo
    logo-small.png    — Optional: editor sidebar logo
```

---

## Credits

Built with Kiro AI-assisted development

Concept and design: [Andrew Doss](https://www.andrewdoss.com/)

Copyright © 2026 Andrew Doss. All Rights Reserved.
