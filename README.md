# The Stewart Lab

Personal PhD-prep dashboard. Dark academic library aesthetic. Hosted as a static site on GitHub Pages, fed live data from a Google Sheet.

Daily home base for research, habits, clinical work, and family — not a productivity app, a command centre.

## Stack

- Static HTML / CSS / vanilla JS — no build step, no framework.
- Google Fonts (Cormorant Garamond, DM Mono) loaded from the Google Fonts CDN.
- Chart.js 4.4.0 loaded from cdnjs (deferred).
- Live weather from Open-Meteo (no API key).
- Data source: Google Sheet published as CSV — fetched every 30 seconds.

## File layout

```
/
├── index.html              · the whole dashboard (single file)
├── 404.html                · matching dark-academic 404 page
├── .nojekyll               · tells GitHub Pages not to run Jekyll
├── README.md               · this file
├── QUICKSTART.md           · setup checklist
├── assets/
│   └── library.jpg         · Long Room, Trinity Dublin (CC BY-SA 3.0, Diliff)
├── docs/
│   └── SHEETS_SCHEMA.md    · planned Sheet tabs and columns
└── apps-script/
    ├── biweekly-finance.gs       · Wednesday email report
    └── biweekly-home-health.gs   · Saturday email report
```

## Sections

- **Splash** — time-aware greeting; top-left holds nav, day, date, time, weather; bottom-left sync indicator.
- **Office** — daily minimums (left column) + cascading time-aware sections (right column) + today's agenda.
- **Weekly** — Mon–Sun grid with fixed daily blocks and weekly rituals on the right days; weekly minimums tracker below.
- **Statistics** — physique phase header, status pill, stat grid, Chart.js trajectory, 12-week heatmap. Currently uses sample data; awaits live CSV URL.

## Data flow (planned)

```
Google Sheet  →  published-as-CSV URL  →  fetch() every 30s  →  Statistics + Office checkboxes
```

The frontend is read-only display. All data entry happens in the Sheet during the day's review cadences.

## Licence

Code: personal use, no licence asserted.
Background photograph: Long Room interior, Trinity College Dublin, by Diliff via Wikimedia Commons, [CC BY-SA 3.0](https://creativecommons.org/licenses/by-sa/3.0/). Attribution preserved in the page footer.
