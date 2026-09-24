# BM0OS

BM0OS is a lightweight, browser-based desktop environment inspired by BMO. It combines a playful interface with customizable tabs, draggable windows, a small question-and-answer assistant, and a browser-based games area.

**Live demo:** [reyaanshgd.github.io/BM0Os](https://reyaanshgd.github.io/BM0Os/)

![BM0OS](bmo-bmo-dance.jpg)

## Overview

BM0OS is designed as a small, self-contained WebOS-style experiment. Everything runs from a static webpage, so there is no server or installation process required for the main interface. Open the demo, explore the tabs, create your own workspace, and rearrange the on-screen boxes by dragging their title bars.

The project is also useful as a simple reference for building an interactive HTML page with vanilla JavaScript, responsive CSS, draggable elements, dynamic tabs, file inputs, and browser-based emulation.

## Features

- **Desktop-style interface** with a dark, glass-like visual design and BMO-inspired artwork.
- **Built-in tabs** for Home, Work, Tutorial, About, and Games.
- **Custom tabs** that can be created from the top toolbar.
- **Tab management** including renaming, moving tabs left or right, and removing tabs.
- **Draggable windows** that can be moved around each desktop view using pointer controls.
- **Custom boxes** that can be added to the currently active tab.
- **Tutorial content** covering common HTML elements such as headings, paragraphs, lists, links, images, and semantic page structure.
- **Ask BMO assistant** for general questions through the floating assistant button.
- **Browser-based games area** that can locally apply a BPS patch to a user-provided ROM and launch the result in a WebAssembly SNES emulator.
- **Responsive layout** that adapts the interface for smaller screens and touch devices.
- **Static hosting friendly** and deployable through GitHub Pages or another static web host.

## Using BM0OS

1. Open the [live demo](https://reyaanshgd.github.io/BM0Os/).
2. Select a tab from the navigation bar.
3. Add a new tab by entering a name in **New tab name** and selecting **Add tab**.
4. Add a window to the active tab by entering a title in **New box title** and selecting **Add box**.
5. Drag a window by its title bar to reposition it.
6. Use the floating BMO button to open the assistant.
7. Select the controller button or open the **Games** tab to view the emulator area.

New tabs and window positions are currently held in the browser session while the page is open; the project does not currently provide persistent account-based workspaces or cloud storage.

## Games and emulator support

The Games tab contains a local patching workflow for **Kirby's Dream Land 2 DX v1.2**. The browser reads the files selected by the user, searches a ZIP archive for a BPS patch when necessary, applies the patch locally, and passes the patched ROM to a WebAssembly-based SNES emulator.

To use this feature, provide:

- A legally owned original ROM in `.sfc` or `.smc` format.
- The corresponding `.bps` patch, either directly or inside a `.zip` archive.

The ROM patching process is intended to happen locally in the browser. The repository includes downloadable emulator and patch assets, but users are responsible for following the laws and licenses that apply in their country and for using only ROMs they are legally allowed to possess and modify. No copyrighted ROM is included in this project.

## Running locally

BM0OS is a static site and does not require a build step or package installation for the main interface.

### Option 1: Open the file directly

Download or clone the repository and open `index.html` in a modern browser. Some browser features, external resources, or emulator behavior may work more reliably when the project is served over HTTP instead of opened with a `file://` URL.

### Option 2: Use a local web server

With Python installed, run:

```bash
python3 -m http.server 8000
```

Then visit [http://127.0.0.1:8000](http://127.0.0.1:8000).

You can also use any static web server or editor extension that provides a local preview server.

## Project structure

```text
.
├── index.html                         # Main application, styles, and client-side logic
├── README.md                          # Project documentation
├── bmo-bmo-dance.jpg                  # Page background artwork
├── bmo-happy.png                      # BMO assistant artwork
├── bmo-loading.png                    # Loading-state artwork
├── bmo-sad.png                        # Default assistant artwork
├── retro controller.png               # Games launcher artwork
├── snes9x emulator.zip                # Emulator download asset
├── Kirby's Dream Land 2 DX v1.2.zip   # Patch asset
└── .nojekyll                          # GitHub Pages configuration marker
```

The core application is currently contained in `index.html`, including the HTML structure, CSS styling, and JavaScript behavior. This keeps the project easy to inspect and makes it suitable for experimentation and learning.

## Technology

BM0OS uses browser-native technologies:

- HTML5 for the interface and accessible form controls.
- CSS3 for the responsive layout, visual effects, windows, tabs, and mobile styling.
- Vanilla JavaScript for tab management, dynamic window creation, dragging, the assistant UI, and local file handling.
- WebAssembly emulator support for running the patched game in the browser.
- GitHub Pages for the public demo deployment.

No framework or compilation toolchain is required for the current version.

## Browser compatibility

Use a recent version of Chrome, Edge, Firefox, or Safari for the best experience. The Games tab may require additional browser capabilities such as WebAssembly, file input support, and JavaScript enabled. Performance can vary depending on the device and browser.

## Development ideas

Possible future improvements include:

- Saving tabs, boxes, and window positions with `localStorage`.
- Adding resizable windows and minimize/maximize controls.
- Improving keyboard navigation and screen-reader support.
- Splitting the application into separate HTML, CSS, and JavaScript files.
- Adding more built-in mini-apps and games.
- Supporting themes, custom backgrounds, and workspace export/import.
- Improving assistant responses and adding clearer offline behavior.

## Contributing

Suggestions, bug reports, and improvements are welcome. To contribute:

1. Fork the repository.
2. Create a feature branch.
3. Make and test your changes in a modern browser.
4. Open a pull request with a description of the change.

For interface changes, please check both desktop and mobile layouts before submitting a pull request.

## License and third-party content

This repository does not currently declare a formal software license. Unless a license is added, the source should not be assumed to be freely reusable beyond the permissions granted by copyright law.

The project also contains artwork and third-party emulator or patch-related assets. Review the relevant upstream licenses and copyright notices before redistributing any part of the repository.

## Credits

Created by [reyaanshgd](https://github.com/reyaanshgd).
Kirby dreamland2 and snes9x emulator: https://www.romhacking.net


Enjoy exploring BM0OS!
