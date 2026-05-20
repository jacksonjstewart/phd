# QUICKSTART — when you're back from the walk

Six discrete steps. Each one is a copy-paste, in order. If anything errors, send me the error message and I'll handle it.

---

## 1 · Get the files onto your machine

In **File Explorer**, open the outputs folder you can see in this Cowork session, and copy **everything** into your local clone of `jacksonjstewart/lab`. After copy, your repo should look like:

```
lab/
├── .nojekyll
├── 404.html
├── README.md
├── QUICKSTART.md
├── index.html
├── assets/
├── docs/
│   └── SHEETS_SCHEMA.md
└── apps-script/
    ├── biweekly-finance.gs
    └── biweekly-home-health.gs
```

---

## 2 · Add the library photo (`assets/library.jpg`)

This is the only piece I can't ship — the image is on Wikimedia and I'm not allowed to bulk-download binaries through this session.

Open **PowerShell**, `cd` into your repo, and run:

```powershell
Invoke-WebRequest `
  -Uri "https://upload.wikimedia.org/wikipedia/commons/thumb/4/4b/Long_Room_Interior%2C_Trinity_College_Dublin%2C_Ireland_-_Diliff.jpg/2560px-Long_Room_Interior%2C_Trinity_College_Dublin%2C_Ireland_-_Diliff.jpg" `
  -OutFile "assets/library.jpg"
```

If you're on Mac/Linux:

```bash
curl -L -o assets/library.jpg \
  "https://upload.wikimedia.org/wikipedia/commons/thumb/4/4b/Long_Room_Interior%2C_Trinity_College_Dublin%2C_Ireland_-_Diliff.jpg/2560px-Long_Room_Interior%2C_Trinity_College_Dublin%2C_Ireland_-_Diliff.jpg"
```

The `2560px-` thumbnail keeps the file around 500–700 KB — sharp on a 4K monitor, fast on mobile. If you want a different library photo, drop any JPG at `assets/library.jpg` and the dashboard will use it.

Verify locally by double-clicking `index.html` — the photo should be visible.

---

## 3 · Push to GitHub

```bash
git add .
git commit -m "Initial dashboard build — splash, Office, Weekly, Statistics scaffold"
git push origin main
```

If you'd rather I push it: paste a fine-grained PAT scoped to `jacksonjstewart/lab` with **Contents: Read and write**, 7-day expiration. I'll commit, push, and you revoke the token immediately after.

---

## 4 · Enable GitHub Pages (one-time)

If Pages isn't already on for this repo:

1. Repo → **Settings** → **Pages**
2. **Source:** `Deploy from a branch`
3. **Branch:** `main` / `/ (root)` → **Save**
4. Wait ~60 seconds. Your site will live at `https://jacksonjstewart.github.io/lab/`.

---

## 5 · Publish the Sheet as CSV and paste the URL back to me

1. Open the Sheet → **File** → **Share** → **Publish to web**
2. Tab: **`PHYSIQUE ACADEMY🦇`** · Format: **Comma-separated values (.csv)**
3. Click **Publish**, confirm, copy the URL (ends in `/pub?output=csv` or has `gid=…&single=true&output=csv`)
4. Paste that URL in your next message to me. I'll wire it into `index.html` (Statistics page goes live the moment you push the change).

---

## 6 · (Optional) Apps Script — biweekly emails

When you're ready to turn on Wednesday/Saturday email reports:

1. Sheet → **Extensions** → **Apps Script**
2. Paste both `.gs` files from `apps-script/` into the editor
3. Add an `onEdit` dispatcher (template is in the comments at the top of `biweekly-home-health.gs`)
4. Add Sarah's email to `TO_EMAILS` in both files
5. **Triggers** → **Add Trigger** → `onEdit`, from spreadsheet, on edit
6. First save will prompt for authorization — accept

---

## What I need from you (the short version)

When you message me, just paste these three things:

1. **The CSV publish URL** for the PHYSIQUE ACADEMY tab.
2. **A fine-grained GitHub PAT** if you want me to push for you (otherwise say "I'll push myself").
3. **Anything you want changed** about what you see when you open `index.html` — typography, colour, layout, content.

Then we iterate.

---

## What I shipped while you were walking

- **Self-hosted library image** path (`./assets/library.jpg`) with three-layer fallback. If the file is missing, you'll see the CSS atmospheric background and a "No image" amber dot bottom-left.
- **Live weather** — Open-Meteo, no API key. Edmonton coords baked in. Refreshes every 30 minutes.
- **Weekly view built** — Mon–Sun grid, today's column highlighted in gold, weekly rituals on the right days (Tuesday family activity, Wednesday finance review, Thursday boys, Friday family/date, Saturday activity + home/health review, Sunday cafe + professional review). Weekly minimums tracker below: resistance, cardio, 50/50/20, screen cutoff.
- **Statistics scaffold built** — Phase header, status pill, four stat cells (current/lost/this week/remaining), Chart.js weight trajectory with all four lines (min/target/max/actual), 12-week heatmap with current week glowing in gold. Uses sample data until your CSV is wired.
- **Accessibility pass** — visible focus rings on every interactive element, keyboard support (Tab/Enter/Space) for all checkboxes and block toggles, `prefers-reduced-motion` respected, ARIA labels on nav and status regions.
- **404 page** matching the aesthetic — "This shelf is empty."
- **`.nojekyll`** so GitHub Pages serves your `assets/` folder cleanly.
- **README** and **SHEETS_SCHEMA** documenting the project.
- **Two Apps Scripts** ready to drop into the Sheet for biweekly email reports.

Version: **v0.6**. Visible in the bottom-left of the splash.
