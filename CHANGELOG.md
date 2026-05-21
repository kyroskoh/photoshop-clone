# Changelog

All notable changes to ProPhoto Editor will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.5.0] - 2026-05-20

### Added
- **Per-Tool Size and Opacity Memory**
  - Each tool independently remembers its last-used Size and Opacity values.
  - Switching tools restores that tool's saved settings — no need to re-adjust sliders on every switch.
  - Default values are pre-configured per tool (e.g. Pencil=2px, Eraser=20px, Spray=20px/80%, shapes=2px).
- **Fill Tolerance Slider**
  - A Tolerance control (0–255) appears in the toolbar when the Fill tool is active.
  - Tolerance 0 matches exact pixel colors; higher values fill through anti-aliased or similar-colored regions.
  - Default tolerance is 30.
- **Canvas Starts in Fit-to-Screen Mode**
  - New documents and restored sessions automatically fit the canvas to the available workspace on load.
- **Improved Tool Panel Tooltips**
  - Tool panel button tooltips now use a `position: fixed` JavaScript-driven tooltip instead of CSS `::after`, which was clipped by the panel's `overflow-y: auto`. Tooltip text appears to the right of the panel, always fully visible.

### Fixed
- **Fill Tool**
  - Flood fill now uses a Uint8Array visited buffer instead of a string Set — significantly faster on large canvases.
  - Fill now respects the current Opacity slider (alpha-blends the fill color onto the existing pixel rather than always writing alpha 255).
  - Configurable tolerance via the new Tolerance slider (was hardcoded at 0, making it impossible to fill anti-aliased areas).
  - Added early exit when the clicked pixel already matches the fill color.

## [1.4.0] - 2026-05-20

### Added
- **Shape Tools — Line, Rectangle, Ellipse**
  - New Line tool: click and drag to draw straight lines; hold Shift to snap to 45° increments.
  - New Rectangle tool: click and drag to draw outlined rectangles; hold Shift to constrain to square.
  - New Ellipse tool: click and drag to draw outlined ellipses; hold Shift to constrain to circle.
  - Live dashed preview while dragging; shape is committed to the layer on mouse-up.
  - All shape strokes are recorded as vector objects compatible with the selection/move system.
  - Shape stroke width is controlled by the existing Size slider.

### Changed
- **Spray Tool Rewrite**
  - Spray now emits discrete particles via a continuous `setInterval` loop (one tick every 30 ms) independent of mouse movement, matching the behaviour of airbrush tools.
  - Particle positions use a Gaussian (Box-Muller) distribution centred on the cursor — denser near the centre, sparse at the edges.
  - Particle alpha falls off quadratically with distance from the cursor, giving natural density gradient.
  - Particle size varies randomly within the radius, creating organic variation.
  - Dot count per tick scales with brush size and opacity, providing effective pressure simulation.
  - Spray is no longer routed through the brush drawing path (separate `startSpray` / `doSprayTick` / `updateSpray` / `stopSpray` functions).

## [1.3.0] - 2026-05-20

### Added
- **Vector Object System for Drawn Content**
  - Brush, pencil, spray, and fill operations now record vector stroke objects alongside their pixel output.
  - Selection tools (marquee, lasso, magic wand) detect entire stroke objects within the selection — not just pixel regions — so full strokes are lifted and moved as a unit.
  - Marquee and lasso detect strokes whose points fall within the selection bounds; magic wand matches strokes by pixel proximity.
  - Fill operations record their bounding extent for detection.

### Changed
- **Selection Tools can now move content directly** — no need to switch to the Move tool.
  - Clicking within an active selection while using Marquee, Lasso, or Magic Wand lifts the selected content and starts a drag-to-move operation (mouseup commits).
  - Clicking outside an active floating selection commits it in place and allows starting a fresh selection.
  - Move tool also prefers vector extraction when selected strokes are available.
- On commit (mouseup), selected vector stroke records are retired from the layer's object list so subsequent selections use the updated pixel state.

## [1.2.2] - 2026-05-20

### Fixed
- **Selection Tool Functionality**
  - Marquee, lasso, and magic wand selections now correctly activate — drawn content (brush, pencil, spray, fill) can be selected and moved/transformed as expected.
  - Root cause: `rebuildSelectionMask()` called `hasActiveEditSelection()`, which called `rebuildSelectionMask()` again when the mask was unbuilt, causing infinite recursion and a silent stack overflow. The selection mask was never built, so `hasActiveEditSelection()` always returned `false` and all selection operations silently failed while the dashed overlay still rendered.
  - Fix: replaced the circular guard with a direct check of `selectedArea` and `selectionMode` in `rebuildSelectionMask()`.

## [1.2.1] - 2026-05-20

### Added
- **Selection Tool Finalization**
  - Double-click to apply/finalize **Marquee** selections.
  - Double-click to apply/finalize **Lasso** selections.
  - Double-click to trigger **Magic Wand** selection at cursor.

### Changed
- **Selection Editing Behavior**
  - Persistent dashed selection overlays are rendered after redraws.
  - Brush and fill operations now respect active selection bounds.
  - Selection state handling improved across crop cancel/apply and history restore.

## [1.2.0] - 2026-05-20

### Changed
- **Crop Tool Interaction**
  - Crop no longer auto-applies on pointer release.
  - Crop area can be moved by dragging inside an existing selection.
  - Crop can be applied with `Enter` or double-click inside the crop area.
  - `Escape` cancels the active crop area.

### Added
- Visual crop/selection interaction flow that supports draw-then-adjust before applying.

## [1.1.0] - 2025-11-10

### Added
- **Project Management System**
  - Project title bar showing current project name (default: "Untitled")
  - Unsaved changes indicator (*) in title bar
  - Save Project functionality - Save complete project state as .prophoto file
  - Load Project functionality - Restore previously saved .prophoto projects
  - Custom .prophoto file format with XOR encoding
  - Project name persistence across sessions

- **Auto-Save & Session State**
  - Automatic session state saving to localStorage
  - Debounced auto-save after 1 second of inactivity
  - Save on page unload and visibility change
  - Restore dialog on page load to resume previous work
  - Session state includes project name, layers, history, and settings

- **Enhanced User Experience**
  - Visual feedback for unsaved changes
  - Project name prompt when saving "Untitled" projects
  - Restore dialog shows last saved time, canvas size, and layer count

### Changed
- Updated File menu to include Save Project and Load Project options
- Session state now includes project name information
- Improved state management for better persistence

### Technical
- Implemented XOR encoding/decoding for .prophoto file format
- Enhanced localStorage state management with debouncing
- Added project name tracking throughout the application

## [1.0.0] - 2025-01-XX

### Added
- **Core Drawing Tools**
  - Move Tool - Pan and navigate the canvas
  - Marquee Tool - Rectangular selections
  - Lasso Tool - Freehand selection
  - Magic Wand - Select similar colored regions
  - Brush Tool - Customizable brush painting
  - Pencil Tool - Precise line drawing
  - Eraser Tool - Remove content with customizable size
  - Spray Tool - Airbrush-style painting
  - Text Tool - Add text to images
  - Fill Tool - Flood fill with color
  - Crop Tool - Crop images to desired size

- **Layer Management**
  - Multiple layers support
  - Layer visibility toggle
  - Layer opacity control
  - Duplicate layers
  - Delete layers
  - Merge layers down
  - Flatten all layers
  - Transparency with checkered pattern display
  - Background layer system (white by default)

- **Image Filters (7 Total)**
  - Brightness adjustment
  - Contrast enhancement
  - Blur effect
  - Sharpen effect
  - Grayscale conversion
  - Invert colors
  - Sepia tone

- **Advanced Features**
  - History System - Full undo/redo with clickable history panel (up to 20 steps)
  - Zoom Controls - Zoom from 10% to 500%
  - Grid Overlay - Toggle grid for precise alignment
  - Color Palette - 32 predefined colors + custom color picker
  - Export Options - Save as PNG or JPEG
  - Keyboard Shortcuts - For faster workflow
  - Responsive Design - Works on different screen sizes
  - Mobile Touch Support - Full touch support for all tools

- **UI Components**
  - Draggable tool panel (left side)
  - Color picker in right panel
  - Primary/secondary color swatches
  - Tool settings panel
  - Layer management panel
  - History panel
  - Status bar

- **Menu System**
  - File menu (New, Open Image, Save As PNG/JPEG)
  - Edit menu (Undo, Redo, Clear Canvas)
  - View menu (Grid, Zoom controls)
  - Filters menu (All 7 filters)
  - Layer menu (Layer operations)
  - Help menu (About)

- **Deployment**
  - GitHub Pages deployment workflow
  - Automatic deployment on push to main/master

### Technical
- Pure HTML5, CSS3, and Vanilla JavaScript
- No dependencies or external libraries
- HTML5 Canvas API for rendering
- LocalStorage API for state persistence
- File API for image loading
- Touch event support for mobile devices
- Responsive CSS with media queries

---

## Version History Summary

- **v1.5.0** - Per-tool size/opacity memory, fill tolerance slider, fixed flood fill (opacity + performance), canvas fit-to-screen on load, fixed panel tooltips
- **v1.4.0** - Shape tools (Line, Rectangle, Ellipse); spray tool rewrite with Gaussian particle distribution and continuous emission
- **v1.3.0** - Vector object system: selection tools detect and move drawn strokes directly; no tool switch required
- **v1.2.2** - Fix selection tool infinite recursion; marquee/lasso/magic wand now correctly select drawn content
- **v1.2.1** - Double-click finalize for selection tools and persistent selection-bound editing
- **v1.2.0** - Crop workflow, keyboard shortcut reliability, selection overlay fixes, and lasso selection-bound editing
- **v1.1.0** - Project management, auto-save, and .prophoto file format
- **v1.0.0** - Initial release with core editing features

---

For detailed information about features and usage, please refer to the [README.md](README.md) file.

