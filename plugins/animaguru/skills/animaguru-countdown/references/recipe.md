# Live Countdown Split-screen production recipe

The workspace includes an executable original study in `src/studies/scenes.ts`, selected with `countdown`. Its drawing commands are consumed by `src/studies/pixi-renderer.ts`; geometry and time sampling are shared with the gallery renderer. All copy lives in `shared/locales/en/style-studies.json`.

In an untouched starter, run `npm run example -- countdown`, then `npm run dev`. The command refuses to replace an authored film, retains starter backups in `production/example-backup/`, and writes an 8-second study with its own resource tracks. `npm run export:mp4` uses this installed film normally. To use the recipe inside an existing film, import `studyFrame()` and `StudyRenderer`, then compose the selected scene into the project's timeline instead of running the installer.

## Evidence and sources

NASA (images.nasa.gov, svs.gsfc.nasa.gov — U.S. federal government works, public domain; check each item for third-party material and never imply endorsement), other U.S. federal agencies (NOAA, National Archives, DoD DVIDS), Internet Archive (only items whose record shows public domain, pre-1931 U.S. publication or CC0/CC BY; skip YouTube mirrors), Wikimedia Commons (CC0, public domain or CC BY only), Library of Congress (read each rights statement). Download only the seconds needed, log every request, and record each asset in `production/CREDITS.md` and each claim, time and call in `production/FACTS.md`.

## Adaptation decisions

- Model each camera as a `Sprite` or video texture inside its own `Container`, whose rectangle is driven by layout keyframes (grid, merge, cut, swap) interpolated with an `easeInOutCubic`, never a hand-typed per-shot duration.
- Draw the fixed-slot clock as individual `Text` or `BitmapText` glyphs in equal-width cells, swapped on the whole second so digits never jitter; drive the sub-second bar and ticks from the same clock state.
- Build the zero merge by animating every cell's rectangle to its tile of one full-screen frame while chip and border graphics fade in the transition's first half, then flip the clock's colour and header state from counting down to counting up.

The study is silent, original procedural art with illustrative values, labelled as such; it demonstrates material, layout and motion, not evidence. Replace its stand-ins with the real synced footage, documents and data described above, never with generated imagery. The gallery preview uses illustrative camera cells with no real launch or event behind them, labelled as such. Configure the subject, palette, scene sequence, duration and soundtrack from the brief.

Use `src/studies/timing.ts` for deterministic easing, seeded variation, measured stroke truncation and cue helpers. `window.animaguru.texts` exposes visible study text bounds for `npm run review`; text declarations alone do not count as visual proof. Inspect the actual frames as well.

## Sources and attribution

Inspired by the following pinned references; source-specific 3D/media dependencies are not bundled. New study art and scene geometry are original. The workspace's `VIDEO-STYLE-NOTICES.txt` preserves the repository notices and clarifies third-party asset scope.

- [styles/countdown/STYLE.md](https://github.com/lemomo-ai/lemo-opuscar/blob/77ee8318df779b0736d7de0abe24387e51023735/styles/countdown/STYLE.md)
- [styles/countdown/demo/index.html](https://github.com/lemomo-ai/lemo-opuscar/blob/77ee8318df779b0736d7de0abe24387e51023735/styles/countdown/demo/index.html)
