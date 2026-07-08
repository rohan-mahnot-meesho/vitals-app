# Deploying Vitals to Vercel

This folder (`vitals-app/`) is self-contained and safe to deploy — it holds only the app (`index.html`) and its config (`vercel.json`). **Deploy this folder, never the parent `Garmin Data` folder**, which contains your private health export.

There's no build step — Vercel just serves `index.html`.

---

## Option A — Vercel CLI (fastest)

1. Install the CLI (one time):
   ```
   npm i -g vercel
   ```
2. Open a terminal in this folder:
   ```
   cd "~/Downloads/Garmin Data/vitals-app"
   ```
3. Deploy:
   ```
   vercel
   ```
   The first run asks you to log in (browser), then a few questions — accept the defaults:
   - Set up and deploy? **Y**
   - Which scope? **your account**
   - Link to existing project? **N**
   - Project name? **vitals** (or anything)
   - In which directory is your code located? **./**
   - Modify settings? **N** (it auto-detects a static site)

   You'll get a preview URL immediately.
4. Publish to production:
   ```
   vercel --prod
   ```
   That gives you the live URL (e.g. `https://vitals.vercel.app`).

To update later: change the file, run `vercel --prod` again.

---

## Option B — GitHub + Vercel dashboard (best for ongoing updates)

1. Put this folder in a GitHub repo (only this folder's contents at the repo root):
   ```
   cd "~/Downloads/Garmin Data/vitals-app"
   git init
   git add index.html vercel.json
   git commit -m "Vitals app"
   ```
   Create an empty repo on GitHub, then follow its "push an existing repo" lines.
   > Only add `index.html` and `vercel.json`. Do not `git add .` from the parent folder.
2. Go to **vercel.com → Add New → Project → Import** your repo.
3. On the configure screen:
   - Framework Preset: **Other**
   - Build Command: leave empty
   - Output Directory: **`.`** (a single period)
4. Click **Deploy**. Every future `git push` auto-deploys.

---

## Custom domain (optional, free)

In the Vercel project → **Settings → Domains**, add a domain you own (e.g. `vitals.yourname.com`) and follow the DNS instructions. HTTPS is automatic.

---

## Notes

- The app loads Chart.js, JSZip, Inter, and Tabler icons from public CDNs, so a live internet connection is needed to view it (normal for a web app).
- `vercel.json` adds a few sensible security headers. `cleanUrls` is on but harmless for a single page.
- Privacy is unchanged when hosted: parsing still happens entirely in the visitor's browser. Vercel only ever serves the static file — it never sees anyone's Garmin data.
