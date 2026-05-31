# Tichu Scorer — PWA build

This folder is your complete, ready-to-host web app. Everything is self-contained:
React is bundled into `app.js`, so there is **no build step** and **no internet
dependency** at runtime — the app works fully offline once installed.

## Files in this folder

| File | What it is |
|------|------------|
| `index.html` | The page that loads the app |
| `app.js` | Your whole app + React, bundled and minified |
| `manifest.json` | App name, colors, icons (makes it installable) |
| `service-worker.js` | Offline caching |
| `icon-192.png` / `icon-512.png` | App icons (Tichu red/yellow/green) |
| `privacy.html` | Privacy policy (needed for the Play listing) |
| `.nojekyll` | Tells GitHub Pages to serve the `.well-known` folder later — **don't delete it** |

> The `.nojekyll` file is intentionally empty and may look invisible in Finder/Explorer.
> Make sure it gets committed to GitHub anyway — you'll need it in Phase 3.

## What changed from your Claude artifact

1. `window.storage` → standard `localStorage` (same two keys, identical behavior).
2. Added the service-worker registration and the app-shell bootstrap.
3. Bundled React locally so nothing depends on Claude's environment or a CDN.

Your game logic, design, fonts, and features are otherwise untouched.

---

## Phase 2 — Put it online with GitHub Desktop

1. **Make a GitHub account** at github.com (free) if you don't have one, and sign
   into GitHub Desktop with it.
2. In GitHub Desktop: **File → New Repository**.
   - Name: `tichu-scorer`
   - Local path: anywhere you like
   - Leave the rest default, click **Create Repository**.
3. Open that new repository folder on your computer (GitHub Desktop shows the path,
   or use **Repository → Show in Finder/Explorer**). Copy **all the files from this
   folder** into it (including the hidden `.nojekyll`).
4. Back in GitHub Desktop you'll see the files listed as changes. Add a summary like
   "Initial app", then click **Commit to main**, then **Publish repository**
   (uncheck "Keep this code private" so Pages can serve it).
5. Turn on hosting: go to **github.com/your-username/tichu-scorer →
   Settings → Pages**. Under "Build and deployment", set Source to **Deploy from a
   branch**, branch **main**, folder **/ (root)**, and Save.
6. Wait ~1 minute, then visit **https://your-username.github.io/tichu-scorer/**.
   Open it on your Android phone — you should be able to "Add to Home screen" and it
   runs full screen. That live URL is what you'll paste into PWABuilder next.

### Updating the app later
Edit files, drag the new versions into the repo folder, commit, and push from
GitHub Desktop. The live site updates within a minute. (When you change `app.js`,
also bump `CACHE_VERSION` in `service-worker.js` — e.g. `tichu-v2` — so installed
copies refresh.)
