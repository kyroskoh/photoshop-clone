# ProPhoto Editor - Complete Image Editor

A feature-rich, browser-based Photoshop clone built with pure HTML5, CSS3, and JavaScript. No dependencies required!

**🌐 [Live Demo](https://kyroskoh.github.io/photoshop-clone/)**

![ProPhoto Editor](https://img.shields.io/badge/version-1.8.1-blue.svg)
![License](https://img.shields.io/badge/license-MIT-green.svg)
![HTML5](https://img.shields.io/badge/HTML5-E34F26?logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?logo=javascript&logoColor=black)

## 🎨 Features

### Drawing Tools
- **Move Tool** - Pan and navigate the canvas
- **Marquee Tool** - Create rectangular selections
- **Lasso Tool** - Freehand selection tool
- **Magic Wand** - Select similar colored regions
- **Brush Tool** - Paint with customizable brushes
- **Pencil Tool** - Draw precise lines
- **Eraser Tool** - Remove content with customizable size
- **Spray Tool** - Airbrush-style painting with Gaussian particle distribution and pressure simulation
- **Text Tool** - Click canvas to open inline text editor; type directly, Enter to commit, Escape to cancel
- **Fill Tool** - Flood fill with color
- **Crop Tool** - Draw, reposition, and apply crop areas
- **Zoom Tool** - Click to zoom in; Alt+click to zoom out; shortcut: Z
- **Line Tool** `[\]` - Draw straight lines; hold **Shift** to snap to 45° increments
- **Rectangle Tool** `[R]` - Draw outlined rectangles; hold **Shift** to constrain to square
- **Ellipse Tool** `[O]` - Draw outlined ellipses; hold **Shift** to constrain to circle

### Image Filters (7 Total)
- Brightness adjustment
- Contrast enhancement
- Blur effect
- Sharpen effect
- Grayscale conversion
- Invert colors
- Sepia tone

### Layer Management
- Multiple layers support
- Layer visibility toggle
- Layer opacity control
- Duplicate layers
- Delete layers
- Merge layers down
- Flatten all layers
- Transparency displayed with checkered pattern
- Background layer system (white by default)

### Advanced Features
- **History System** - Full undo/redo functionality with clickable history panel (up to 20 steps)
- **Zoom Controls** - Zoom from 10% to 500%
- **Grid Overlay** - Toggle grid for precise alignment
- **Color Palette** - 32 predefined colors + custom color picker
- **Export Options** - Save as PNG, JPEG, WebP, BMP, GIF, AVIF, TIFF, SVG, or WebM (animated)
- **Project Management** - Save and load projects in custom .prophoto format
- **Auto-Save** - Automatic session state saving to localStorage (resume work later)
- **Unsaved Changes Indicator** - Visual indicator (*) shows when project has unsaved changes
- **Keyboard Shortcuts** - For faster workflow
- **Responsive Design** - Works on different screen sizes
- **Mobile Touch Support** - Full touch support for drawing, brushing, and all tools on mobile devices

## 🚀 Getting Started

### Prerequisites
- A modern web browser (Chrome, Firefox, Safari, Edge)
- No installation or dependencies required!

### Running the Application

1. **Clone or download the repository**
   ```bash
   git clone https://github.com/kyroskoh/photoshop-clone.git
   cd photoshop-clone
   ```

2. **Open the application**
   - Simply open `index.html` in your web browser
   - Or use a local server:
     ```bash
     # Python 3
     python -m http.server 8000
     
     # Python 2
     python -m SimpleHTTPServer 8000
     
     # Node.js (with http-server)
     npx http-server
     ```
   - Then navigate to `http://localhost:8000`

## 🎯 Usage Guide

### Getting Started
1. Open the application in your browser
2. Use **File → New Document** to create a new canvas
3. Or **File → Open Image** to load an existing image

### Basic Workflow
1. **Select a Tool** - Click on any tool in the toolbar
2. **Adjust Settings** - Use sliders for size, opacity, and zoom
3. **Draw/Edit** - Click and drag on the canvas
4. **Apply Filters** - Use the Filters menu for effects
5. **Use History** - Click any history item to restore that state, or use Ctrl+Z/Ctrl+Shift+Z
6. **Save Your Work** - File → Save Project to save as .prophoto file, or File → Save As PNG/JPEG to export image

### Crop Workflow
- Draw a crop rectangle by clicking and dragging with the Crop tool
- Reposition the crop area by dragging inside the rectangle
- Apply the crop with `Enter` or by double-clicking inside the crop area
- Cancel the active crop area with `ESC`

### Selection Workflow
- Draw **Marquee** selections; hold **Shift** to constrain to square.
- Draw **Lasso** selections freehand; release the mouse to auto-close.
- Click with **Magic Wand** to select contiguous pixels; uncheck *Contiguous* to select matching pixels across the whole canvas. Adjust tolerance (0–255) in the toolbar.
- **Combine selections** with modifier keys while any selection tool is active:
  - **Shift** — Add to selection
  - **Alt** — Subtract from selection
  - **Shift+Alt** — Intersect with selection
  - Persistent mode buttons (☐ ⊕ ⊖ ⊗) in the toolbar let you lock a mode without holding keys.
- **Move selection border** — drag inside an existing selection with a selection tool to reposition the boundary without lifting pixels; switch to the Move tool to lift and move content.
- Active selections animate with **marching ants** (black + white dashed border).
- Drawing tools (brush, pencil, eraser, spray, fill, text) are constrained to the active selection — pixels outside are protected.
- When switching from a selection tool to a drawing tool with an active selection, a prompt lets you **Deselect**, **Keep Selection** (drawing stays constrained), or **Cancel**.

### Working with Layers
- **Background Layer** - Starts with white color, provides a base
- **Add New Layers** - Click "+ Add Layer" to create transparent layers on top
- **Draw on Layers** - Select a layer first, then draw on it
- **Hide Background** - Toggle visibility to see transparency (checkered pattern)
- **Layer Order** - Layers stack from bottom to top (Background at bottom)

### Mobile Usage
- **Touch Drawing** - Use your finger to draw, brush, and paint just like with a mouse
- **All Tools Work** - Brush, Pencil, Eraser, Spray, Fill, and all other tools support touch
- **Touch-Friendly UI** - Larger touch targets (44px minimum) for easy interaction
- **Prevent Scrolling** - Touch events are optimized to prevent accidental page scrolling
- **Pan & Zoom** - Use Move tool with touch to pan the canvas
- **Works Offline** - No internet required after initial load

### Keyboard Shortcuts

#### Tool Selection
| Key   | Tool       | Key   | Tool      |
|-------|------------|-------|-----------|
| `V`   | Move       | `B`   | Brush     |
| `M`   | Marquee    | `P`   | Pencil    |
| `L`   | Lasso      | `E`   | Eraser    |
| `W`   | Magic Wand | `A`   | Spray     |
| `C`   | Crop       | `T`   | Text      |
| `G`   | Fill       | `Z`   | Zoom      |
| `\`   | Line       | `R`   | Rectangle |
| `O`   | Ellipse    |       |           |

#### Canvas & Editing
- `Ctrl+N` - New Document
- `Ctrl+O` - Open Image
- `Ctrl+S` - Save / Export
- `Ctrl+Z` - Undo
- `Ctrl+Shift+Z` - Redo
- `Ctrl+A` - Select All
- `Ctrl+D` - Deselect / commit floating selection
- `Ctrl+Shift+D` - Reselect
- `Ctrl+Shift+I` - Inverse selection
- `Delete` - Clear current layer
- `ESC` - Commit floating selection / clear selection

#### Crop
- `Enter` - Apply crop area
- `ESC` - Cancel crop area

#### Zoom
- `Ctrl+=` - Zoom in (steps: 10 → 25 → 33 → 50 → … → 500%)
- `Ctrl+-` - Zoom out
- `Ctrl+0` - Fit canvas to screen
- `Ctrl+1` - Actual size (100%)

#### Brush / Tool Size & Opacity
- `[` - Decrease size by 5 px
- `]` - Increase size by 5 px
- `Shift+[` - Decrease opacity by 10%
- `Shift+]` - Increase opacity by 10%

## 📋 Menu Guide

### File Menu
- **New Document** - Create a blank canvas (800×600)
- **Open Image...** - Load an image from your computer
- **Save Project...** - Save project as .prophoto file (includes all layers, history, settings)
- **Load Project...** - Load a previously saved .prophoto project file
- **Export with Transparency (PNG)...** - Flatten all visible non-Background layers and export as PNG with alpha preserved; useful for stickers, overlays, and assets
- **Export / Save As ▶** (flyout submenu)
  - *With background* — JPEG, BMP, GIF, TIFF
  - *Supports transparency* — PNG, WebP, AVIF, SVG
  - *Video (3 s)* — WebM (cycles through layers, 500 ms per frame)

### Edit Menu
- **Undo** - Revert last action
- **Redo** - Restore undone action
- **Clear Canvas** - Clear the current layer

### View Menu
- **Toggle Grid** - Show/hide alignment grid
- **Fit to Screen** - Auto-zoom to fit canvas
- **Actual Size** - Reset zoom to 100%
- **Zoom In** - Increase zoom level
- **Zoom Out** - Decrease zoom level

### Filters Menu
- **Brightness** - Increase image brightness
- **Contrast** - Enhance contrast
- **Blur** - Apply blur effect
- **Sharpen** - Sharpen image details
- **Grayscale** - Convert to black and white
- **Invert Colors** - Invert all colors
- **Sepia** - Apply sepia tone effect

### Layer Menu
- **New Layer** - Add a new transparent layer
- **Duplicate Layer** - Copy the current layer
- **Delete Layer** - Remove the current layer
- **Merge Down** - Merge with layer below
- **Flatten Image** - Combine all layers

### Select Menu
- **Select All** — Select the entire canvas (`Ctrl+A`)
- **Deselect** — Clear the active selection (`Ctrl+D`)
- **Reselect** — Restore the last cleared selection (`Ctrl+Shift+D`)
- **Inverse** — Invert the selection; everything unselected becomes selected and vice versa (`Ctrl+Shift+I`)
- **Grow** — Expand the selection outward by 1 pixel
- **Similar** — Select all pixels in the image similar in colour to the current selection (uses Magic Wand tolerance; not restricted to contiguous regions)
- **Expand...** — Dilate the selection by a specified number of pixels (circular kernel)
- **Contract...** — Erode the selection by a specified number of pixels
- **Feather...** — Soften the selection edge by a specified radius

### Help Menu
- **About ProPhoto Editor** - View project information and credits

## 🎨 Tool Settings

### Brush/Pencil/Eraser
- **Size**: 1-100 pixels
- **Opacity**: 1-100%
- **Color**: Choose from palette or custom color picker

### Zoom Controls
- **Range**: 10% - 500%
- **Quick Actions**: Fit to Screen, Actual Size
- **Keyboard**: +/- to zoom in/out

### Color Selection
- **Primary Color**: Main drawing color
- **Secondary Color**: Alternative color
- **Palette**: 32 preset colors
- **Custom**: Use color picker for any color

## 🛠️ Technical Details

### Technologies Used
- **HTML5 Canvas** - For rendering and drawing operations
- **CSS3** - Modern styling with flexbox and grid
- **Vanilla JavaScript** - No frameworks or libraries
- **LocalStorage API** - Automatic session state persistence
- **File API** - Save/load project files (.prophoto format)
- **XOR Encoding** - Custom file format encryption for project files

### Browser Compatibility
- ✅ Chrome 90+ (Desktop & Mobile)
- ✅ Firefox 88+ (Desktop & Mobile)
- ✅ Safari 14+ (Desktop & iOS)
- ✅ Edge 90+ (Desktop & Mobile)
- ✅ Mobile browsers (iOS Safari, Chrome Mobile, Samsung Internet)

### Performance
- Lightweight: Single HTML file (~60KB)
- Fast: Hardware-accelerated canvas rendering
- Efficient: Optimized pixel manipulation algorithms

## 📁 Project Structure

```
photoshop-clone/
├── .github/
│   └── workflows/
│       └── deploy.yml  # GitHub Pages deployment workflow
├── index.html          # Main application file (all-in-one)
├── README.md           # This file
├── DELIVERY.md         # Project delivery information
├── test-assets/        # Test resources
│   ├── test_image.png
│   └── test_image.json
├── test_website.py     # Automated test script
├── test-progress.md    # Testing documentation
└── test-report.md      # Test results
```

## 🚀 Deployment

### GitHub Pages (Automatic)

This project includes a GitHub Actions workflow that automatically deploys to GitHub Pages:

1. **Push to main/master branch** - Deployment triggers automatically
2. **Manual deployment** - Use the "Actions" tab → "Deploy to GitHub Pages" → "Run workflow"

#### First-Time Setup:
1. Go to your repository **Settings** → **Pages**
2. Under "Source", select **GitHub Actions**
3. Push code to trigger deployment
4. Your site will be live at `https://kyroskoh.github.io/photoshop-clone/`

The workflow file is located at `.github/workflows/deploy.yml`

### Local Deployment

Run locally with a simple HTTP server:

```bash
# Python 3
python -m http.server 8000

# Python 2
python -m SimpleHTTPServer 8000

# Node.js (with http-server)
npx http-server
```

Then visit `http://localhost:8000`

## 🧪 Testing

The project includes automated tests:

```bash
# Run automated tests
python test_website.py
```

Tests verify:
- Canvas initialization
- Tool selection functionality
- Layer management
- Filter application
- Export functionality
- UI responsiveness

## 🔧 Customization

### Adding Custom Colors
Modify the color palette in the `initColorPalette()` function:

```javascript
const colors = [
    '#yourcolor1', '#yourcolor2', // Add your colors here
];
```

### Adjusting Canvas Size
Change default canvas dimensions in `init()` or `fileActions('new')`:

```javascript
canvas.width = 1920;  // Your width
canvas.height = 1080; // Your height
```

### Adding Custom Filters
Add new filter cases in the `applyFilter()` function:

```javascript
case 'yourfilter':
    // Your filter logic here
    break;
```

## 🎨 Transparency & Layers

ProPhoto Editor uses a true transparency system like professional editors:

### Layer Behavior
- **Background Layer** - Created with solid white color by default (named "Background")
- **New Layers** - All additional layers start completely transparent
- **Checkered Pattern** - Transparent areas display a gray/white checkered pattern
- **Layer Naming** - Background layer = "Background", new layers = "Layer 2", "Layer 3", etc.

### Transparency Features
- **True Alpha Channel** - Full transparency support on all layers except Background
- **Visibility Toggle** - Hide the Background layer to see transparency
- **Delete Background** - Remove the Background layer for a fully transparent canvas
- **Export** - PNG exports preserve transparency; JPEG exports with white background

## 💾 Project Management

ProPhoto Editor includes comprehensive project management features:

### Project Title Bar
- **Project Name Display** - Shows current project name (default: "Untitled")
- **Unsaved Changes Indicator** - Asterisk (*) appears when project has unsaved changes
- **Auto-Update** - Title updates automatically when project is saved or loaded

### Save/Load Projects
- **Save Project** - Save complete project state as .prophoto file
  - Includes all layers, history, settings, colors, and tool states
  - Custom XOR-encoded file format
  - Prompts for project name if saving "Untitled" project
- **Load Project** - Restore previously saved .prophoto files
  - Fully restores all project data including layers and history
  - Project name is restored from saved file

### Auto-Save & Session State
- **Automatic Saving** - Session state saves to localStorage automatically:
  - After 1 second of inactivity (debounced)
  - On page unload
  - On visibility change (tab switch)
- **Resume Work** - When returning to the page:
  - Restore dialog appears if saved state exists
  - Shows last saved time, canvas size, and layer count
  - Choose to restore previous work or start new session
- **Project Name Persistence** - Project name is saved with session state

## 📝 Known Limitations

- Undo/Redo history is capped at 20 steps; canvas snapshots are not persisted across page reloads (history labels are restored but pixel-level undo is reset on reload)
- Magic wand selection border shows a bounding-box outline rather than a pixel-accurate contour (marching ants trace the bounding rectangle, not the individual selected pixels)
- WebP and AVIF export requires a modern browser with codec support (Chrome 85+, Firefox 93+); not available in older Safari
- GIF export uses 3-3-2 color quantization (256-colour palette); complex images may show banding
- No non-destructive adjustment layers; filters are applied directly to pixel data

## 🚧 Future Enhancements

- [x] Export with transparency (PNG alpha)
- [x] Advanced selection manipulation — Feather, Expand, Contract, Grow, Similar, Inverse, Reselect
- [x] Selection combination modes — Add (Shift), Subtract (Alt), Intersect (Shift+Alt) across all selection tools
- [x] Photoshop-style floating selection — lift, move, scale, and rotate selected content
- [x] Marching ants animation on selection borders
- [x] Move selection border without moving content
- [x] Elliptical marquee tool — oval selections with marching ants ellipse, Shift=circle, combine modes
- [x] Polygonal lasso tool — click-to-place vertices, rubber-band preview, close on double-click or near start
- [x] Filled shape option — Fill Shape toggle for rectangle and ellipse tools
- [x] Additional filters — noise, emboss, edge detect, vignette
- [x] Categorised tool panel — tools grouped into Nav / Select / Paint / Shape / Utility sections
- [ ] Pixel-accurate marching ants contour for magic wand selection
- [ ] Transform tools — skew and perspective in addition to move/scale/rotate
- [ ] Gradient tool
- [ ] Pattern / clone-stamp tool
- [ ] Adjustment layers (non-destructive brightness, curves, hue/saturation)
- [ ] Per-layer blend modes (multiply, screen, overlay, etc.)
- [ ] Batch processing / scripting
- [ ] Project templates
- [ ] Cloud save integration

## 🤝 Contributing

Contributions are welcome! Here's how you can help:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see below for details:

```
MIT License

Copyright (c) 2025 ProPhoto Editor

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```

## 👨‍💻 Author

**ProPhoto Editor** - A Photoshop clone created with ❤️ by **Kyros Koh**

This browser-based image editor brings professional-grade photo editing capabilities to the web, inspired by Adobe Photoshop's powerful toolset and interface design.

## 🙏 Acknowledgments

- Inspired by Adobe Photoshop and GIMP
- Created as a demonstration of modern web technologies
- Built with pure HTML5 Canvas, CSS3, and Vanilla JavaScript
- Thanks to the open-source community

## 📞 Support

If you encounter any issues or have questions:
- Open an issue on GitHub
- Check existing documentation
- Review the test reports

## 🌟 Show Your Support

If you found this project helpful, please consider:
- ⭐ Starring the repository
- 🐛 Reporting bugs
- 💡 Suggesting new features
- 📖 Improving documentation

---

**Happy Editing! 🎨**

