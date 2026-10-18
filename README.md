# 🌀 TIMER CHECK!

Four figures spinning on the spot, for a 4- and a 10-year-old. One static page, no build step, no dependencies. Built for Android Chrome; also works on iPhone/iPad Safari.

**Play:** `index.html` on GitHub Pages (Settings → Pages → Deploy from a branch → `main` / `(root)`).

## What's on the page

Title, animation, then visual tiles (lit = active, dimmed = not), descriptions, and at the very bottom a **🛠 Something broken? Turn things off** panel.

| Group | Options |
|---|---|
| Look | Stick · Round people · Animals · Photos (just your picture, no body) |
| Background | Sky · Space · Disco · 🔁 Cycle |
| Beat | Tune · Together · Gallop · Scale |
| Sound | Beep · Toot · Ding · Ooo! · Aah! · Animals (frog / monkey / pig / dog noises) |

Also: tap a figure to stop/start it, **hold** it to spin faster, 🔔 bell and 🥁 drum buttons, and four volume squares (tap the last lit square again to go quieter, down to mute).

Sound is always on. Phones need one tap before they allow audio, so a big yellow button asks for it; any tap works.

## When something breaks

Open the panel at the bottom and untick the feature. The page remembers it in the URL, so the link can be shared with the feature already off:

`?off=hold,backgrounds` (ids: `round animal image tap hold backgrounds patterns voices animalsounds instruments volume`)

"Turn everything back on & reset" undoes it all. There's also a **Mute all sound** switch there.

## Privacy

No photos in this repo, ever (`.gitignore` blocks common image types as a safety net). The Photos look crops to a small square in memory; nothing is uploaded or saved, and a reload forgets it.

## Versioning

Semver. `1.0.0` is the first release. Earlier `0.x` builds (including the mic and shake levels, removed in 1.0.0) are in git history.

## Working on it

Everything is in `index.html`. Each feature is one `register({...})` block above the `FEATURES ABOVE THIS LINE` marker:

- `tiles`: visual toggles it adds (`group` = `look | bg | beat | voice`; `toggle: true` for on/off tiles)
- `skin: { id, draw(i) }`: how the figures look
- `css`, `enable({ app, ui, on, every, onDispose })`, `decorate(fig, i)`, `controls: true` if it can stop the spin
- sounds live in `VOICES` / `PATTERNS`, built from a tiny synth kit (`tone`, `buzz`, `vowel`, `noise`)

To remove a feature for good, `git revert` its commit or delete its block.
