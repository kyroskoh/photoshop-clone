# Changelog

All notable changes to ProPhoto Editor will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.10.2] - 2026-05-21

### Added
- **Retouch tool category** — introduced a new toolbox category dedicated to advanced paint/retouch workflows.
- **New tools** — Gradient (linear/radial), Pattern (preset/custom), Clone Stamp (Alt-click source with aligned mode), Blur, Sharpen, and Burn tools.
- **Contextual tool options** — added top-toolbar option groups for gradient type, pattern source selection/loading, and clone aligned toggle.

### Changed
- **Layer replay coverage** — extended stroke replay rendering for gradient and pattern layer elements so these new element types remain visible in layer/object redraw flows.

## [1.10.1] - 2026-05-21

### Changed
- **Selected-element move interaction smoothing** — moving a selected layer element now starts on the first drag after selection, removing the previous two-click behavior.
- **Auto Move-tool selection for element moves** — selecting a layer element now automatically switches to Move tool for immediate transform/move workflows.
- **Top toolbar transform quick actions** — rotate/flip icon buttons were added to the horizontal toolbar for one-click rotate 90° CW/CCW and flip horizontal/vertical operations.

## [1.10.0] - 2026-05-21

### Added
- **Photoshop-style Free Transform workflow** — `Ctrl+T` now starts Free Transform; `Enter` commits and `Esc` cancels/restores session state.
- **Advanced transform actions (Edit menu)** — rotate 90° CW/CCW, rotate 180°, flip horizontal/vertical, skew, and perspective commands added.
- **Shift-constrained transforms** — Shift now constrains transform interactions: axis-lock move, proportional scale, angle-snapped rotate, and axis-constrained skew.

### Changed
- **About panel release notes** — updated to surface the new 1.10.0 transform suite and behavior.

## [1.9.5] - 2026-05-21

### Added
- **Layer preview thumbnails** — layer preview icons now render live snapshot thumbnails of each layer canvas, scaled to fit the preview tile.

## [1.9.4] - 2026-05-21

### Fixed
- **Spray element move fidelity** — moved spray elements now preserve spray-dot rendering instead of being redrawn as a generic brush-like stroke.
- **Shape element move fidelity** — moved line/rectangle/ellipse elements now preserve their proper geometry and shape fill behavior after commit.

## [1.9.3] - 2026-05-21

### Fixed
- **Selected-element move commit cleanup** — when moving a selected layer element, previous drawn pixels are now fully cleared on mouseup commit.
- **Canvas coordinate precision under zoom** — tool drawing/interaction coordinates now map correctly to intrinsic canvas `x,y` under zoom/transforms.

### Changed
- **Layer element list auto-expand** — layers now automatically expand when a new element is created/recorded in that layer.

## [1.9.2] - 2026-05-21

### Fixed
- **Selected element move scope** — when a specific layer element is selected, Move tool drag now applies only to that selected element instead of moving the whole layer.
- **Selected element persistence after move** — after move/scale/rotate commit, the moved selected element now remains selected in the layer element list and on-canvas highlight.

## [1.9.1] - 2026-05-21

### Added
- **Live layer-element refresh** — layer element lists now refresh immediately when new brush/spray/shape/fill/text elements are created, without requiring extra clicks.

### Changed
- **History panel order** — most recent history entries are now shown at the top of the history list.
- **Element transform metadata sync** — moving selected elements now keeps registered geometry/coordinates synchronized with transformed positions.
- **Text element bounds after transform** — transformed text elements now recompute bounding boxes from transformed text corners for more accurate selection hit areas.

## [1.9.0] - 2026-05-21

### Added
- **Cursor ring extended** — line, rectangle, and ellipse tools now show the cursor ring; the circle diameter matches the stroke width so you can see how thick each stroke will be before drawing
- **Ruler guides** — 20 px pixel rulers along the top and left edges of the canvas; drag from either ruler onto the canvas to create a horizontal or vertical cyan dashed guide line; hover a guide to get a resize cursor; drag it to reposition; drag it off the canvas to delete; toggle all guides with View → Toggle Guides or `Ctrl+;`
- **Layer content move** — with the Move tool and no active selection, clicking and dragging now translates all pixels and strokes on the current layer as a block; an amber dashed border shows while moving; all stroke coordinates are updated on commit so future drawing stays aligned; locked layers show a toast instead
- **Expandable layer element list** — each layer row has a ▶ toggle; clicking it reveals a child list of every stroke in that layer (tool icon + auto-name like "brush #1"); clicking an element in the list selects it and draws a blue bounding-box outline on the canvas; with the Move tool active, dragging then moves just that selected stroke as a floating selection; double-clicking an element row opens an inline rename input; double-clicking a layer name already supported renaming

### Changed
- Move tool fallback changed from canvas pan to layer-content move; canvas pan still available via middle-mouse button or space+drag

## [1.8.1] - 2026-05-21

### Added
- **Brush cursor ring** — a circular outline follows the mouse for brush, pencil, eraser, and spray tools, showing the exact brush diameter at the current zoom level; system cursor hidden while the ring is shown
- **Layer lock** — each layer now has a lock button (🔓/🔒) in the layer panel; locking a layer prevents drawing, filling, spraying, shapes, text edits, and floating-selection lifts; deleting a locked layer shows a toast notification instead; locked layers display an amber left-border indicator

## [1.8.0] - 2026-05-21

### Added
- **Elliptical Marquee tool** — drag to select oval/elliptical areas; Shift=perfect circle; supports all combination modes (Add/Subtract/Intersect); marching ants trace the actual ellipse curve; shortcut `Shift+M`
- **Polygonal Lasso tool** — click to place polygon vertices; double-click or click near start (< 10 px) to close; rubber-band preview line tracks cursor while placing points; Escape cancels mid-polygon; shortcut `Shift+L`
- **Filled shapes** — "Fill Shape" checkbox appears in the toolbar when rectangle or ellipse is selected; draws a solid fill instead of stroke-only outline
- **Noise filter** — adds uniform random color noise to the current layer; available in Filter menu and side panel
- **Emboss filter** — classic emboss convolution kernel producing a 3-D relief effect
- **Edge Detect filter** — Laplacian edge detection that highlights outlines and contrast boundaries
- **Vignette filter** — applies a smooth radial darkening toward the corners of the canvas
- **Categorised tool panel** — tools are now grouped under labeled sections (Nav, Select, Paint, Shape, Utility) with dividers for faster scanning
- **Improved tool icons** — all tool panel icons updated to clearer, more Photoshop-like SVG shapes

### Changed
- Keyboard shortcut `M` still selects rectangular marquee; `Shift+M` now selects elliptical marquee
- Keyboard shortcut `L` still selects freehand lasso; `Shift+L` now selects polygonal lasso
- Zoom tool moved to the Navigation group at the top of the tool panel

## [1.7.1] - 2026-05-21

### Fixed
- Editing tools (brush, pencil, fill, eraser, spray, text, etc.) can now be selected at any time when a selection tool is active — switching to a drawing tool silently keeps the active selection in place (Photoshop behavior). Previously, a "Deselect / Keep Selection" modal blocked tool switching entirely.

## [1.7.0] - 2026-05-21

### Added
- **Marching ants animation** — selection borders now animate with classic black+white alternating dashes instead of a static line
- **Selection combination modes** — Shift=Add, Alt=Subtract, Shift+Alt=Intersect across all three selection tools (marquee, lasso, magic wand); persistent mode buttons (☐ ⊕ ⊖ ⊗) appear in the toolbar when any selection tool is active
- **Move selection border** — dragging inside an existing selection with a selection tool repositions the border without lifting pixels; move tool still extracts content
- **Shift to constrain square** — Shift+drag in marquee New mode snaps to a perfect square
- **Magic wand drawing constraint** — brush, pencil, eraser, and spray now paint only within the magic wand selection (pixel-accurate mask)
- **Magic wand contiguous toggle** — Contiguous checkbox in toolbar; unchecked selects all matching pixels across the canvas non-contiguously
- **Magic wand tolerance** — dedicated tolerance slider (0–255) in toolbar replaces the fill-tool slider when magic wand is active

### Changed
- Selection border now uses dual-stroke marching ants (white + black offset by 4 px, animated at 12.5 fps)
- Magic wand bounding box gets a 10% blue tint overlay in addition to marching ants border
- Selection mode buttons automatically appear in toolbar for marquee/lasso/magic wand tools and hide for all other tools
- Modifier keys always override the sticky mode button on each new mouse-down

## [1.6.0] - 2026-05-20

### Added
- **Select Menu** — new top-level menu between Layer and Help with:
  - **Select All** (`Ctrl+A`) — selects the entire canvas as a marquee
  - **Deselect** (`Ctrl+D`) — clears the active selection
  - **Reselect** (`Ctrl+Shift+D`) — restores the last cleared selection
  - **Inverse** (`Ctrl+Shift+I`) — inverts the current selection (swaps selected ↔ unselected pixels)
  - **Grow** — expands the selection outward by 1 px in 4-connected directions
  - **Similar** — selects all pixels across the entire canvas whose color matches the average color of the current selection (within Magic Wand tolerance), regardless of contiguity
  - **Expand...** — morphological dilation by a user-specified number of pixels (circular kernel)
  - **Contract...** — morphological erosion by a user-specified number of pixels
  - **Feather...** — softens selection edges via a box-blur pass followed by a 0.5 threshold
- **Deselect prompt** — switching from a selection tool (Marquee, Lasso, Magic Wand) to a drawing tool while a selection is active shows a modal offering: **Deselect** (clear and switch), **Keep Selection** (switch while constraining drawing to selection), or **Cancel**.
- **Reselect state** — `clearSelectionState()` now persists the last selection for `Reselect` to restore.

### Changed
- `Ctrl+D` unified into `selectionDeselect()` (same behaviour, now also commits floating selection).
- Keyboard shortcuts `Ctrl+A` and `Ctrl+Shift+I` added to the global key handler.

## [1.5.5] - 2026-05-20

### Added
- **WebM export** (restored from contributor commit 68d4e49 by a2937) — File → Export/Save As → Export as WebM... records a 3-second animation cycling through layers at 500 ms per frame and downloads as `<name>.webm`.

### Fixed
- **Magic wand hang** — replaced the `Set<string>` visited tracker (`'x,y'` key per pixel) with a `Uint8Array` flat bitmask and a pre-allocated `Int32Array` stack. Eliminates all string allocation in the hot flood-fill loop; an 800×600 canvas that previously froze the browser now completes in milliseconds.
- **Magic wand selects the correct object** — the flood fill now composites all visible layers into a temporary canvas before sampling, so clicking on a painted stroke selects the stroke's pixels rather than the transparent background underneath it.
- **localStorage quota exceeded** — `historyStates` (up to 20 full canvas PNG snapshots × N layers ≈ 6–12 MB) was being written to localStorage on every action, reliably blowing the 5 MB browser quota. Canvas snapshots now live in memory only; only the small action-name list is persisted. Undo/redo works normally within a session and resets on page reload (standard behaviour).
- **WebM export broken** — `redrawCanvas()` (non-existent) replaced with `renderLayers()`; layer cycling slowed from 60 fps to 500 ms per frame for legible output; `MediaRecorder.start(100)` timeslice ensures data is collected during recording rather than only at stop; `captureStream(30)` sets a stable frame rate.

## [1.5.4] - 2026-05-20

### Added
- **Export with Transparency (PNG)** — new File menu item that flattens all visible non-Background layers and exports as `<name>_transparent.png` with alpha channel preserved; ideal for stickers, overlays, and compositing assets.

### Changed
- **File menu reorganised** — the 8 "Save As" format items are now grouped in a flyout **Export / Save As ▶** submenu, split into two labelled sections:
  - *With background* (JPEG, BMP, GIF, TIFF)
  - *Supports transparency* (PNG, WebP, AVIF, SVG)

## [1.5.3] - 2026-05-20

### Added
- **Expanded Export Formats** — File → Save As now offers all 8 formats:
  - **WebP** — native Canvas API (`toBlob`); falls back with a notification on unsupported browsers.
  - **BMP** — inline 24-bit BMP encoder; rows bottom-up per spec; white background composited.
  - **GIF** — inline GIF89a encoder with 3-3-2 color quantization (256 colors) and LZW compression.
  - **AVIF** — native Canvas API (`toBlob`); requires Chrome/Edge/Firefox; falls back with notification.
  - **TIFF** — inline uncompressed 24-bit little-endian TIFF encoder (single strip, 72 DPI).
  - **SVG** — SVG wrapper embedding the canvas as a PNG `<image>` data URL; preserves transparency.
  - Unified `exportAs(format)` function dispatches all formats.
  - File menu updated with all 8 export items.
- **Import** — file picker now explicitly lists PNG, JPEG, WebP, GIF, BMP, SVG, TIFF, AVIF in addition to the wildcard `image/*`.

### Changed
- **Tool panel tooltips** now include the keyboard shortcut key in brackets for every tool (e.g. "Brush [B]", "Lasso [L]", "Line [\]").
- Shape tool tooltips no longer show the Shift-key hint (removed clutter).

### Fixed
- **Text tool inline editor** repositioned to use `position: fixed` on `document.body` with screen-space coordinates, so it is always visible regardless of canvas zoom level or parent transform. Dark themed styling makes it clearly visible over any canvas content.

## [1.5.2] - 2026-05-20

### Added
- **Zoom Tool**
  - New Zoom tool added to the tool panel (shortcut: `Z`).
  - Click to zoom in; Alt+click to zoom out through discrete zoom steps (10 → 25 → 33 → 50 → 67 → 75 → 100 → 150 → 200 → 300 → 400 → 500%).
  - Canvas cursor shows `zoom-in` / `zoom-out` and flips when Alt is held.
- **Inline Text Editor**
  - Text tool now opens an inline input directly on the canvas at the clicked position instead of using a browser `prompt()` dialog.
  - Styled with the current primary color and font size (Size slider × 2).
  - Press **Enter** to commit text to the layer; press **Escape** to cancel.
  - All keyboard shortcuts are blocked while the inline editor is open — no accidental tool switches while typing.
  - Clicking elsewhere on the canvas commits the text automatically.
  - Respects selection clip and the current opacity setting.

### Fixed
- **Keyboard Shortcut Guard for Text Mode**
  - Inline text editor uses `stopPropagation` on all `keydown` events, preventing tool shortcuts from firing while typing.
  - `selectTool()` now calls `commitTextEdit()` before switching, so switching via panel click also commits in-progress text.
  - A `textEditState` guard in `handleKeyDown` provides an additional safety net.

## [1.5.1] - 2026-05-20

### Added
- **Full Keyboard Shortcuts for All Tools**
  - Tool selection: `V` Move · `M` Marquee · `L` Lasso · `W` Magic Wand · `B` Brush · `P` Pencil · `E` Eraser · `A` Spray · `T` Text · `G` Fill · `C` Crop · `\` Line · `R` Rectangle · `O` Ellipse
  - Brush size: `[` decrease 5 px · `]` increase 5 px
  - Opacity: `Shift+[` decrease 10% · `Shift+]` increase 10%
  - Zoom: `Ctrl+=` zoom in · `Ctrl+-` zoom out · `Ctrl+0` fit to screen · `Ctrl+1` actual size (100%)
  - `Ctrl+D` — deselect / commit floating selection
  - `Delete` — clear the current layer
  - `Escape` — commit floating selection and clear selection

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

- **v1.10.2** - Added Retouch category with Gradient/Pattern/Clone Stamp/Blur/Sharpen/Burn tools and contextual options
- **v1.10.1** - Smoothed first-drag selected-element movement, auto-selected Move tool on element pick, and added top-toolbar rotate/flip quick icons
- **v1.10.0** - Added full Free Transform workflow, 90° rotate/flip/skew/perspective actions, and Shift-constrained transform behavior
- **v1.9.5** - Added live layer thumbnail snapshots in the layer preview icons
- **v1.9.4** - Preserved spray rendering and shape geometry correctly after moving selected elements
- **v1.9.3** - Selected-element move commit cleanup, corrected canvas coordinate mapping at zoom, and auto-expand layer on new element creation
- **v1.9.2** - Move tool now strictly targets the selected layer element and preserves selection after commit
- **v1.9.1** - Layer element list auto-refresh on create; history newest-first; selected-element move keeps registered coordinates synced; improved transformed text bounds
- **v1.9.0** - Cursor ring for shape tools; ruler guides; layer content move; expandable layer element list with per-element select/rename/move
- **v1.8.1** - Brush cursor ring for paint tools; layer lock/unlock controls and lock-state safeguards
- **v1.8.0** - Elliptical marquee, polygonal lasso, filled shapes, noise/emboss/edge/vignette filters, grouped/categorized tool panel
- **v1.7.1** - Fixed selection-mode tool-switch blocking so drawing tools can be selected while preserving active selection
- **v1.7.0** - Marching ants animation; selection combine modes (Add/Subtract/Intersect); move selection border; magic wand contiguous/tolerance controls
- **v1.6.0** - Select menu (Select All, Deselect, Reselect, Inverse, Grow, Similar, Expand, Contract, Feather); deselect prompt on tool switch
- **v1.5.5** - WebM export restored & fixed; magic wand performance (Uint8Array bitmask, no browser hang); wand samples composite canvas; localStorage quota fix (historyStates removed from auto-save)
- **v1.5.4** - Export with Transparency (PNG); flyout Export/Save As submenu grouped by transparency support
- **v1.5.3** - Shortcut keys in tool tooltips; all 8 export formats (PNG/JPEG/WebP/BMP/GIF/AVIF/TIFF/SVG); fixed inline text editor; clean shape tooltips
- **v1.5.2** - Inline text editor on canvas; zoom tool added; keyboard shortcuts blocked during text editing
- **v1.5.1** - Full keyboard shortcuts for all 15 tools, bracket size/opacity control, zoom shortcuts, Ctrl+D deselect, Delete clear layer
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

