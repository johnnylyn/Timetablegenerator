# Timetable Generator

A flexible, offline-capable school timetable generator. Set up your teachers, subjects, classes, and constraints once — then auto-generate a conflict-free weekly timetable, with every cell still editable by hand afterward.

Built as a single self-contained web app (no backend, no external dependencies) that installs like a native app on any phone via "Add to Home Screen."

## Features

- **Teachers** — add, rename, or remove teachers, with editable IDs
- **Subjects** — mark which subjects need double (back-to-back) periods
- **Classes** — add/remove class arms, with a live workload summary (periods assigned vs. free)
- **Periods & Breaks** — toggle active days, edit period times, and define breaks (a double period can never span a break)
- **Teacher Availability** — block specific periods or whole days per teacher; the generator treats this as a hard constraint
- **Curriculum** — assign subjects, teachers, and periods-per-week for every class
- **Generate & Edit** — one-tap auto-scheduling using a backtracking algorithm that:
  - never double-books a teacher across classes at the same time
  - respects marked-unavailable slots
  - keeps double periods inside a single unbroken block
  - limits each subject to one appearance per class per day (aside from its own double)
  - nudges free periods away from period 1–2
  - flags anything it couldn't place, and every cell stays manually editable with live conflict warnings
- **Teacher View** — a read-only weekly schedule per teacher, computed from the generated timetable
- **Exports** — CSV (opens in Excel/Sheets) and a print-ready view for saving as PDF via your browser's print dialog
- **Data** — export/import your whole setup as JSON for backup or moving between devices

## Using it

Open `generator.html` (via the live GitHub Pages link, or directly from disk) and start with the **Teachers**, **Subjects**, and **Classes** tabs, or tap **Load starter data** on the **Data** tab for a ready-made example dataset to explore or adapt.

All data is saved automatically in your browser's local storage — nothing is sent to a server. Use **Export as JSON** periodically as a backup, and to move your setup to another device.

## Installing as an app

1. Open the hosted link in your phone's browser
2. Use your browser's **"Add to Home Screen"** option
3. It opens full-screen with its own icon, and keeps working offline after the first load (via the included service worker)

## Tech notes

Plain HTML/CSS/JavaScript — no build step, no frameworks, no external services. `manifest.json` and `sw.js` provide the installable/offline PWA behavior. All five files (`generator.html`, `manifest.json`, `sw.js`, `icon-192.png`, `icon-512.png`) need to be deployed together, in the same folder, for the app to install and cache correctly.
