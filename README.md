# Civitas Vaticana — interactive map

Single-page MapLibre map of Vatican City built from live OpenStreetMap data.
Opens instantly from a **preloaded snapshot** (`data/snapshot.json`); the **Renovare / Update live** button fetches fresh data from Overpass.

## Publish on GitHub Pages
1. Create a repository and push these files to `main`.
2. *Settings → Pages →* Source: **Deploy from a branch**, branch `main`, folder `/ (root)`.
3. *Actions → Update data → Run workflow* once. It writes a real `data/snapshot.json` and then refreshes it every Monday.
   (Or run `node scripts/fetch-snapshot.mjs` locally and commit the result.)

Until a real snapshot exists, the page loads live data automatically, so it works from the very first deploy.

## LinkedIn / social preview
In `index.html` replace `YOUR-USERNAME` (and the repo name, if different) in the `og:url` and `og:image` tags with your real GitHub Pages address, commit, then re-scrape the link at linkedin.com/post-inspector so the card picks up `og-image.png`.

## Notes
- Data © OpenStreetMap contributors (ODbL). Map tiles © OpenFreeMap.
- The Overpass query lives in `buildOverpassQuery()` in `index.html`; the snapshot script reads it from there.
- Opening `index.html` from disk (`file://`) skips the snapshot and loads live data.
