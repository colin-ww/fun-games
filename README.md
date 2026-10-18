# 🌀 Spin Party

Four figures spinning on the spot, for a 4- and a 10-year-old. One static page, no build step, no dependencies.

**Play:** `index.html` on GitHub Pages (Settings → Pages → Deploy from a branch → `main` / `(root)`).

## Levels

Each level is its own `register({...})` block in `index.html`, tagged with the version that introduced it.

| Level | Version | What |
|---|---|---|
| 1 | 0.1.0 | 4 stick figures spinning on the spot (loops forever) |
| 2 | 0.2.0 | Beep beep tune: each spinning figure plays its own beat. Needs one tap (phones block autoplay) |
| 3 | 0.3.0 | Rounder figures: faces, colours, silly hats |
| 5 | 0.4.0 | Tap a figure to freeze / free it |
| 7 | 0.5.0 | Animals instead of people |
| 4 | 0.6.0 | Real faces as heads, picked from the device (in memory only, never uploaded or saved) |
| 6 | 0.7.0 | Noise starts the spin, silence stops it (mic; needs HTTPS) |
| 8 | 0.8.0 | Shake the phone to toggle spin or make a figure vanish (iOS asks permission; desktop: press `S`) |

## Picking a version

Open **⚙️ Versions & options** on the page, or use the URL:

- `?v=0.3.0` – show everything up to and including v0.3.0 (no `v` = latest)
- `?v=0.3.0&f=spin,sound,animals` – hand-picked levels (ids: `spin sound round tap animals photo mic shake`)

The URL updates as you click, so any state is a shareable link. The header shows the version you're *showing* and the version of the *build* you loaded; if they disagree with what you expect, your phone has a cached copy (GitHub Pages caches ~10 min): reload, or add any junk param like `&r=2`.

## Versioning

Semver, staying on `0.x.y` until it's been verified on real devices (especially mic and shake, which can't be tested headlessly). Then `1.0.0`. New level → minor bump; fix → patch.

## Adding / reverting a level

- Add: write a `register({ id, level, since, title, desc, ... })` block above the `FEATURES ABOVE THIS LINE` marker. Hooks: `skin.draw(i, photo)`, `css`, `enable({app, ui, listen, every, onDispose})`, `decorate(fig, i, app)`, `controls: true` for anything that can stop the spin.
- Revert: `git revert` that level's commit, or delete its block. Levels don't know about each other.

## Privacy

No photos in this repo, ever (`.gitignore` blocks common image types as a safety net). The photo level crops to a small square in memory and never stores or sends it.
