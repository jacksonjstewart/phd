# PhD Pro©

Single-file personal dashboard (dark doctoral theme) hosted on GitHub Pages. Live at https://jacksonjstewart.github.io/phd/

## Files

| File | Purpose |
|---|---|
| `index.html` | The whole app (HTML + CSS + vanilla JS, no build step) |
| `library.jpg` | Background photograph (Long Room, Trinity College Dublin, Diliff, CC BY-SA 3.0) |
| `manifest.json` | PWA / home-screen install metadata |
| `404.html` | Matching "off the map" page |
| `.nojekyll` | Tells GitHub Pages not to run Jekyll |
| `Code.gs` | Google Apps Script backend — lives in the Sheet's script editor, not served by Pages (keep a copy here) |

## How it works

- **Nightwing Dailies** — five daily tiles, synced across devices through the Apps Script backend. Completing all five opens the weight splash; completing them also unlocks Office.
- **Office** — read-only mirror of the *Pers Casc* and *PhD Casc* tabs. Desks unlock when the weekly cascade goal is met (surplus carries forward).
- **Statistics** — program calendar, consistency, and weight graph.
- **Program dates and weights** come from the Sheet (tab "THE GREAT WINTER": `Start Date`, `End Date`, `Date`/`Weight` columns; tab "PHYSIQUE ACADEMY": `Starting Weight` and the weekly Min/Exact/Max plan). Everything is found by tab name and cell label, so extending the end date or adding rows needs no code change.

## Updating

1. **Dashboard:** commit `index.html` (and any other changed file) to `main`; Pages redeploys in about a minute.
2. **Backend:** paste `Code.gs` into Extensions → Apps Script → Deploy → Manage deployments → edit → *New version* → Deploy (the web-app URL stays the same).

## Starting a new cycle

Change `Start Date` / `End Date` on the program tab, add the new weekly plan rows, and the dashboard follows after its next sync.

## Licence

Code: personal use. Background photograph: CC BY-SA 3.0, attribution preserved in the page footer.
