# QUICKSTART — what to do, in order

Five steps. Copy each one in order. Done in ~10 minutes.

---

## 1 · Get all the project files into your repo

You're working from a folder on your machine. In **File Explorer**, open the Cowork outputs folder for this session and copy **every file** into your local clone of `jacksonjstewart/lab`. After the copy, your repo should look like:

```
lab/
├── .nojekyll
├── 404.html
├── README.md
├── QUICKSTART.md
├── index.html
├── assets/                   ← empty, library.jpg goes here
├── docs/
│   └── SHEETS_SCHEMA.md
└── apps-script/
    ├── biweekly-finance.gs
    └── biweekly-home-health.gs
```

Subfolders matter. Keep `docs/` and `apps-script/` intact.

---

## 2 · Add the library background photo

1. Click this link (image opens in your browser):
   `https://upload.wikimedia.org/wikipedia/commons/thumb/4/4b/Long_Room_Interior%2C_Trinity_College_Dublin%2C_Ireland_-_Diliff.jpg/2560px-Long_Room_Interior%2C_Trinity_College_Dublin%2C_Ireland_-_Diliff.jpg`
2. **Right-click → Save image as…** → save as `library.jpg`
3. Move the file into your repo at `lab/assets/library.jpg`

The CSS already dims, sepias, and adds vignette + grain on top. You don't need to edit anything visual.

Verify locally by double-clicking `index.html` — the Long Room photo should appear.

---

## 3 · Push to GitHub

In your terminal, from the `lab/` folder:

```bash
git add .
git commit -m "Dashboard build — Office, Weekly, Statistics, live CSV wired"
git push origin main
```

---

## 4 · Enable GitHub Pages (one-time, skip if already on)

1. Repo on GitHub → **Settings** → **Pages**
2. **Source:** `Deploy from a branch`
3. **Branch:** `main` / `/ (root)` → **Save**
4. Wait ~60 seconds. Site lives at `https://jacksonjstewart.github.io/lab/`

---

## 5 · (Optional) Wire the biweekly email reports

When you want Wednesday/Saturday email reports turned on:

1. Open the Google Sheet → **Extensions** → **Apps Script**
2. Paste the contents of `apps-script/biweekly-finance.gs` AND `apps-script/biweekly-home-health.gs` into the editor
3. Add the `onEdit` dispatcher shown in the comments at the top of `biweekly-home-health.gs`
4. Add Sarah's email to the `TO_EMAILS` array in both files
5. **Triggers** → **Add Trigger** → `onEdit`, from spreadsheet, on edit
6. First save will prompt for authorization — accept

---

## What's already wired

- **Live weather** — Open-Meteo, Edmonton, refreshes every 30 min. No API key needed.
- **Live physique data** — your published CSV is hooked in. Statistics page fills in once Sheet has data, falls back to sample data if the fetch fails.
- **Day-aware Office tab** — Morning Routine items show/hide based on day (Rest Day on Monday, Steam/Sauna not Monday, biweekly Finance Wed from May 27, biweekly H&H Sat from May 23, monthly Travel Planning first Thursday from June 4).
- **Weekly view** — Mon–Sun grid, today's column glows gold.
- **Time-aware greeting** — Good morning / afternoon / evening / working late, Dr. Stewart.

---

## What I need from you next

Open `index.html` locally and tell me one of:

- "Looks good, ship it" (then push, you're done)
- "Change X" — anything about the look, copy, structure
- Specific edits to the morning routine list, supplements list, etc.

That's it. The whole pipeline is set up.
