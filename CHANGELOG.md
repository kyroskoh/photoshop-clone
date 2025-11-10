# Changelog

All notable changes to ProPhoto Editor will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

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

- **v1.1.0** - Project management, auto-save, and .prophoto file format
- **v1.0.0** - Initial release with core editing features

---

For detailed information about features and usage, please refer to the [README.md](README.md) file.

