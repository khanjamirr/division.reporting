# Division Reporting by JK (v3.6)

A single-page, client-side reporting dashboard for division/branch staffing data. Upload an Excel file, filter and group by client/location, flag records that need attention, and export the results — all in the browser, with no backend.

## Features

- **North / SE / SC** and **West** report modules with their own metrics and reporting-date fields
- **Red flags** view with recruiter/date filtering and sorting
- Client & location filters, search, hide/merge/group rows, saved groupings
- Excel import (`.xlsx` / `.xls`) via [SheetJS](https://sheetjs.com/) and Excel export / copy-to-clipboard
- All data and settings are kept in the browser's `localStorage` — nothing is sent to a server
- Responsive layout with a dark sidebar, mobile toggle, and print styles

## Project structure

```
.
├── index.html      # the entire app (markup, styles, and logic)
├── README.md
└── .gitignore
```

Everything lives in `index.html`. The only external dependency is the SheetJS library, loaded from a CDN (`cdnjs.cloudflare.com`) — no build step, no `node_modules`, no server-side code.

## Running locally

Since it's a static file, any local web server works. For example:

```bash
npx serve .
# or
python3 -m http.server 8000
```

Then open the printed URL in your browser. Opening `index.html` directly by double-clicking should also work in most browsers.

## Deploying to GitHub

If you haven't already, turn this folder into a repo and push it:

```bash
cd division-reporting
git init
git add .
git commit -m "Initial commit: Division Reporting v3.6"
git branch -M main
git remote add origin https://github.com/<your-username>/<your-repo>.git
git push -u origin main
```

## Deploying to Vercel

This is a plain static site, so it needs **zero configuration** on Vercel — no `vercel.json`, no build command, no framework preset.

**Option A — via the Vercel dashboard**
1. Push the repo to GitHub (see above).
2. Go to [vercel.com/new](https://vercel.com/new) and import the GitHub repository.
3. Leave the Framework Preset as **Other**, and leave Build Command / Output Directory empty.
4. Click **Deploy**. Vercel will serve `index.html` as-is.

**Option B — via the Vercel CLI**
```bash
npm i -g vercel
cd division-reporting
vercel        # first deploy, follow the prompts
vercel --prod # promote to production
```

## Notes

- Because all app state (uploaded data, filters, saved groups) is stored in each browser's `localStorage`, data does **not** sync between devices or browsers, and clearing site data/cache will reset it.
- No environment variables or API keys are needed for this app to run.
