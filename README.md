# BM0OS Desktop

A single-page, browser-based desktop built with plain HTML, CSS, and JavaScript. Create tabs, add draggable boxes, play a Game Boy game, chat with BMO, and fiddle with a few desktop toys. No build step and no dependencies to install. Built for Hackclub Stardance!!

## Features

### Desktop
- **Tabs:** add, rename, reorder (◀ ▶), and delete tabs. The Games tab can't be deleted.
- **Boxes:** add draggable boxes to any tab.
  - Click a box's text to edit it.
  - Close a box with the ✕ in its titlebar.
  - Move a box with the mouse or touch, or focus its titlebar (Tab key) and use the arrow keys. Hold Shift for bigger steps.
- **Saved layout:** tabs, boxes, positions, sizes, and box text are stored in your browser (`localStorage`) and restored on load.

### Ask BMO
A small chat helper in the bottom-right corner. It answers greetings, the time, simple arithmetic, and general questions via Wikipedia. The last 50 messages are kept between visits.

### Games
A Game Boy emulator (EmulatorJS) that loads Kirby's Dream Land 2 from a bundled ZIP. Use the emulator's toolbar to save and load states. A fixed game name is set so saves still match after a page refresh.

### Confusion tab
A grid of dancing BMOs. Enter the Konami code (↑ ↑ ↓ ↓ ← → ← → B A) while on this tab for a short party mode.

### Toys
Draggable widgets that float over every tab:
- **Micro Pad:** a mechanical keypad with click sounds.
- **Star:** click it to send it flying across the screen.
- **Pixel clock:** a sideways pixel-art clock with:
  - a 12h / 24h toggle
  - an MM/DD date line
  - a time zone dropdown
  - an alarm (the colon flashes and a beep plays, with a Stop button; it auto-stops after one minute)

## Getting started

1. Put `index.html` (or `bm0os-desktop.html`) and the asset files below in the same folder.
2. Open the HTML file in a modern browser.

The Games tab fetches the ZIP with `fetch()`, which browsers often block on `file://` pages. If the game won't load, serve the folder locally:

```bash
python3 -m http.server 8000
# then open http://localhost:8000
```

### Required asset files

| File | Used for |
| --- | --- |
| `bmo-bmo-dance.jpg` | Page background and Confusion tab |
| `bmo-sad.png`, `bmo-happy.png`, `bmo-loading.png` | Ask BMO button states |
| `retro controller.png` | Games dock button |
| `Kirby's Dream Land 2.zip` | Bundled game (must contain a `.gb` ROM) |

You must supply your own legally obtained ROM.

## Saved data

Everything is stored locally in your browser. Nothing is sent to a server, apart from Ask BMO's Wikipedia lookups and the emulator and ZIP libraries loaded from a CDN.

| Key | Contents |
| --- | --- |
| `bm0os-layout-v1` | Tabs, boxes, positions, text |
| `bm0os-chat-v1` | Ask BMO chat history |
| `bm0os-clock-v1` | Clock format, time zone, alarm |

To reset the desktop, run this in the browser console and refresh:

```js
localStorage.removeItem("bm0os-layout-v1");
```

## Customizing

- **Konami code:** edit the `konami` array in the main script.
- **Clock time zones:** edit the list passed to `tzSel.add(new Option(...))`. To list every zone, use `Intl.supportedValuesOf("timeZone")`.
- **Chat history length:** change `.slice(-50)` in `addAssistantMessage`.
- **Default tabs:** edit `defaultDesktopTabs` and the matching `<section class="desktop-view">` blocks.

## Notes and limitations

- `saveLayout` and `restoreLayout` must stay at the **end** of the main script, after everything else is defined.
- The alarm sound needs a prior click or keypress on the page (browser autoplay rules).
- Box text is saved as HTML in your own browser. That's fine for a personal page, but don't paste untrusted content into boxes.
- Ask BMO's replies come from Wikipedia and a few built-in answers, so treat them as quick lookups, not authoritative answers.
- Pixel clock and star animations respect `prefers-reduced-motion`.

## Tech

Plain HTML, CSS, and JavaScript. [EmulatorJS](https://emulatorjs.org/) and [JSZip](https://stuk.github.io/jszip/) load from a CDN.

## Ai disclosure
I used Ai to tell me the steps to creating a demo url as I didn't understand the documentation, I also used Ai to help me with wirting the README, and used it to teach me how to link files to the website, and create a wikipedia bot. I also used AI to explain me how to run the emulator.