# IdeaMap

A local-first mind-mapping workspace built with React, TypeScript, Vite, and React Flow. This is a browser-based redesign of the supplied Rust/egui app, not a modification of the native Rust executable.

## Storage

- **Desktop app**: maps, settings, backups **and attachment files** are saved in a folder on disk — by default `Documents\IdeaMap` (`ideamap-workspace.json`, `ideamap-backups.json`, and a `media\` subfolder). Change the location any time in **Settings → Storage → Choose folder**; existing data is carried over automatically.
- **Browser version**: the workspace stays in this browser's local storage and IndexedDB. Clearing site data removes local maps and backups, so export documents for durable storage.

No backend, account, or cloud service is required. The interface reports save failures rather than claiming the document was saved.

## Run

```sh
npm install
npm run dev
```

## Electron

```sh
npm run electron:dev     # develop with hot reload
npm run electron:start   # build, then open in Electron
npm run electron:build   # build + package Windows installers into release/
node scripts/make-icon.mjs   # regenerate public/icon.png + icon.ico
```

## Verify

```sh
npm run build
npx tsc --noEmit
npx playwright install --with-deps chromium
npx playwright test
```

To check the built production app instead of the development server, run `PLAYWRIGHT_PRODUCTION=1 npx playwright test` after building.

## Workspace

- Drag, select, copy, duplicate, and connect ideas on a zoomable canvas.
- Customize node colors, five shapes, and six visual styles.
- Edit semantic connections, arrows, labels, line patterns, and thickness.
- Explore nested maps, an outline view, map search, and the keyboard command center.
- Organize multiple maps with favorites and starter templates.
- Attach images or documents up to 2 MB per file.
- Autosave in browser storage, keep local backups, and undo or redo edits.
- Import Markdown, exported web documents, and the original Rust/serde JSON format.
- Export a complete JSON document or readable Markdown, including nested maps.
- Choose from ten workspace themes, with responsive desktop and mobile navigation.

## Source

- `src/App.tsx`: application entry point, canvas, navigation, and commands.
- `src/useWorkspace.ts`: persistence, editing operations, history, and project management.
- `src/model.ts`: document types, templates, validation, and import/export helpers.
- `src/components/`: custom nodes, inspector, sidebar, and accessible dialogs.
- `src/index.css`: responsive visual system and themes.
- `tests/workspace.spec.ts`: real-browser workflow checks.

DM Sans is hosted locally. Its license is included in `public/fonts/OFL.txt`.
"# IdeaMap" 
