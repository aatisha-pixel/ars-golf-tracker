# Ars Golf Analytics

A mobile-first, installable, offline-ready golf score tracker. It has no backend, no dependencies, and no build step. All data stays in the browser until exported.

## Run locally

Service workers require HTTP (not `file://`). From the folder above this project, run:

```bash
python3 -m http.server 8000
```

Open `http://localhost:8000/ars-golf-tracker/`.

## Deploy to GitHub Pages

1. Sign in to GitHub as **aatisha-pixel**.
2. Create a new public repository named **ars-golf-tracker**. Do not add a README or other starter files.
3. In Terminal, open this unpacked project folder and run:

```bash
git init
git add .
git commit -m "Launch Ars Golf Analytics"
git branch -M main
git remote add origin https://github.com/aatisha-pixel/ars-golf-tracker.git
git push -u origin main
```

4. On GitHub, open **Settings → Pages**.
5. Under **Build and deployment**, choose **Deploy from a branch**.
6. Choose branch **main**, folder **/(root)**, then click **Save**.
7. After GitHub finishes publishing, open:
   `https://aatisha-pixel.github.io/ars-golf-tracker/`

All asset, manifest, and service-worker URLs are relative, so the app works under the `/ars-golf-tracker/` repository path.

## Install on iPhone

Open the published site in Safari, tap **Share**, then **Add to Home Screen**. Launching the new icon opens the standalone app. Visit it once online before relying on offline mode.

## Data notes

- Browser storage is device- and browser-specific. Use **More → Export JSON backup** regularly.
- Import replaces the current local dataset after confirmation.
- Summary-only historical rounds contribute to scoring, front-nine, and back-nine averages, but not to fairway, GIR, putt, or per-hole analytics.
- Holes 2, 3, and 8 are marked as construction-shortened for historical interpretation.

## Copy a round to ChatGPT

Open **Rounds**, tap the round you want, then tap **Copy ChatGPT Summary**. Open your pinned golf-scores chat and paste the copied summary into the message box.

## Cancel a practice or accidental round

While a round is open, scroll below the hole controls and tap **Cancel this round**. Confirm the warning to discard the unfinished round. Saved rounds are not affected.

## Advanced round intelligence

- Mark any hole as modified and choose Construction, Temporary Green, Temporary Tee, Shortened, Lengthened, or Other.
- Modified holes always count toward the round total. Long-term hole and shot analysis excludes them by default; use the toggle at the top of **Stats** to include them.
- Record tee club, detailed tee-shot result, penalty type, weather, wind, and course conditions.
- **Coach’s Corner** provides rules-based takeaways at round completion and on the Stats screen. Its recommendations improve as more detailed rounds are recorded.
- Backups use a structured, versioned round object with `conditions` and per-hole records, making future database/cloud migration straightforward.
