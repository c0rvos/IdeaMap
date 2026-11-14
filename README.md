# IdeaMap

A local-first mind-mapping workspace. Spread your ideas across a zoomable canvas, connect them, drop in files and videos, and go a level deeper inside any idea — all saved on your own machine, with no account and no server.

Built with React, TypeScript, Vite, and React Flow, packaged as a Windows desktop app with Electron. It is a browser-based redesign of a supplied Rust/egui app, not a modification of the native Rust executable.

![Tech](https://img.shields.io/badge/React-19-blue) ![Tech](https://img.shields.io/badge/TypeScript-5.9-blue) ![Tech](https://img.shields.io/badge/Electron-45-green) ![Tech](https://img.shields.io/badge/Vite-7-purple)

---

## Highlights

- **Infinite idea canvas** — drag, select, copy, duplicate, and connect ideas on a zoomable map (20%–250%), with a dot grid, snap-to-grid, mini-map overview, and one-key fit-to-view.
- **Everything on one canvas** — ideas, sticky notes, images, videos, audio, documents, and web links live side by side.
- **Nested maps** — double-click any idea to open a map *inside* it, with breadcrumbs and up-level navigation. Maps within maps, as deep as your thinking goes.
- **Local-first desktop app** — your whole workspace is plain files in a folder you choose. No cloud, no login, works offline.
- **Command center** — `Ctrl K` opens a fuzzy search over every idea *and* every command in the app.
- **Ten visual themes** — from Light and Paper to Nord, Dracula, Cyberpunk, and AMOLED.

---

## Features in detail

### The canvas

| Feature | What it does |
|---|---|
| Ideas | Cards with a label, subtitle, notes, tags, five icon styles, and a color from the palette |
| Sticky notes | Small non-connected thoughts, one keypress away (`S`) |
| Media items | Drop or paste images, videos, audio, and documents (up to 200 MB per file) directly onto the canvas |
| Web links | Paste a URL to create a link card — YouTube, Instagram, TikTok, Vimeo, and more get thumbnails, author, and play **in-app**; other sites open in a new tab |
| Connections | Draw semantic links between ideas: direction, arrows, labels, line patterns, and thickness |
| Multiple selection | Rubber-band select, `Ctrl`-click, select-all (`Ctrl A`), then move, copy, or delete together |
| Undo / redo | 80-step history (`Ctrl Z` / `Ctrl Shift Z`) |
| Clipboard | Copy and paste ideas — and paste *system* content too: files, screenshots, links (`Ctrl V` anywhere) |
| Zoom & pan | Scroll to zoom, drag to pan, hand tool (`H`), fit to view (`F`), live zoom indicator |

### Organization

- **Multiple maps** with a library sidebar: all maps, favorites (`★`), and recents, each with a name and description.
- **Starter templates** — Blank, Discovery, Research, Brainstorm, and Reading — each pre-drawn with example ideas and connections.
- **Nested maps** with a breadcrumb trail; drill down and back up without losing your place.
- **Outline view** — a compact table of every idea with notes and connection counts, for when you want lists instead of arrows.
- **Map search** (`Ctrl F`) highlights matches and dims the rest; cycle through results with one click.
- **Command center** (`Ctrl K`) — fuzzy-search ideas (including inside nested maps) and run commands: add, theme switching, export, focus mode, and more.
- **Layout control** — hide the sidebar (`Ctrl \`), the top bar (`Ctrl Shift \`), or everything at once in focus mode (`Ctrl .`). Each choice is remembered.
- **Details panel** — edit the selected idea's label, notes, tags, color, icon; manage attachments; flip through connected ideas and links.

### Persistence (your data, your disk)

- **Autosave** — every change is saved shortly after you make it (delay adjustable: 400 ms – 1 s).
- **Local backups** — automatic every two minutes, plus one-click manual backups; the last 12 are kept and restorable from Settings → Storage.
- **A storage folder you control** — the desktop app keeps everything in a normal folder on disk (default `Documents\IdeaMap`):

  | File | Contents |
  |---|---|
  | `ideamap-workspace.json` | All maps, ideas, connections, and settings |
  | `ideamap-backups.json` | Local backups |
  | `media\` | Every attached file, as real files on disk |

  Change the folder in **Settings → Storage → Choose folder**; existing maps, backups, and media are carried over automatically. The save indicator tells you honestly whether the document was written.
- **Import & export** — export one map as an IdeaMap `.json` document (files embedded) or readable `.md` Markdown; import Markdown, exported documents, or the original Rust/serde JSON format. Export the *whole workspace* as one file. Open shared documents dropped onto the canvas.

### Look and feel

- **Ten themes** — Light, Dark, Midnight, Paper, Nord, Dracula, Monochrome, Cyberpunk, Icon Blue, AMOLED — applied instantly, with automatic dark-mode awareness for canvas internals.
- **Responsive** — desktop three-pane layout down to a mobile slide-in navigation.
- **Accessible** — labeled controls, keyboard-friendly dialogs, focus management, reduced-motion-aware animations.
- **Keyboard shortcuts** — the full list is in-app under `?`; highlights:

  | Action | Keys |
  |---|---|
  | Command center | `Ctrl K` |
  | New idea / sticky note | `A` / `S` |
  | Add link / files | `L` / `U` |
  | New map | `N` |
  | Fit to view / Hand / Select / Connect | `F` / `H` / `V` / `C` |
  | Undo / Redo | `Ctrl Z` / `Ctrl Shift Z` |
  | Copy / Paste / Duplicate | `Ctrl C` / `Ctrl V` / `Ctrl D` |
  | Open nested map | Double-click an idea |
  | Add idea | Double-click the canvas |
  | Focus mode | `Ctrl .` |

### The desktop app (Electron)

- **Frameless window** with in-app minimize / maximize / close controls; the header doubles as the draggable title bar (double-click it to maximize).
- **Native file storage** — see *Persistence* above; the browser version falls back to browser storage automatically.
- **Open with the system** — send attached files to their registered desktop application (image viewer, PDF reader, media player…).
- **Real app icon** and taskbar presence.
- **Packaged for Windows** — an NSIS installer and a standalone portable `.exe`.

---

## Privacy

Local-first. Private by default. Always yours. No backend, account, telemetry, or cloud service is involved — saving failures are reported honestly rather than pretending the document was saved.

## Project structure

| Path | Purpose |
|---|---|
| `src/App.tsx` | Application entry point, canvas, navigation, and commands |
| `src/useWorkspace.ts` | Persistence, editing operations, history, and project management |
| `src/model.ts` | Document types, templates, validation, and import/export helpers |
| `src/blobs.ts` | Attachment storage (disk folder in the desktop app, IndexedDB in the browser) |
| `src/links.ts` | Link recognition, metadata, and embed resolution |
| `src/desktop.ts` | Typed bridge to the Electron main process |
| `src/components/` | Custom nodes, inspector, sidebar, and accessible dialogs |
| `src/index.css` | Responsive visual system and themes |
| `electron/` | Main process, preload bridge, and dev runner |
| `public/` | App icon and fonts (DM Sans, license included) |
| `scripts/make-icon.mjs` | Generates the app icon from the logo design |
| `tests/` | Real-browser Playwright workflow checks |

DM Sans is hosted locally; its license is included in `public/fonts/OFL.txt`.
"# IdeaMap" 
