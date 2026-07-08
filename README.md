# Vitals

Turn your Garmin data export into a calm, complete health dashboard — resting heart rate, VO₂ max, sleep, training, and the correlations between them.

## Privacy

Everything runs **client-side in your browser**. Your Garmin export is parsed and charted locally — nothing is ever uploaded to a server. When hosted, the host only serves a single static file; it never sees your data.

## Run locally

Open `index.html` in a browser and drop your Garmin export `.zip` on the page. (Needs an internet connection to load the chart and parsing libraries from a CDN.)

## Deploy

Static site, no build step. See `DEPLOY.md` for Vercel (CLI or GitHub import) instructions. In short, on Vercel: framework preset **Other**, no build command, output directory `.`.

## How to get your Garmin export

Sign in at garmin.com/account → **Export Your Data**. Garmin emails a download link within a few days. Upload the `.zip` as-is.

---

*Wellness insights from your own data — not medical advice.*
