# Broadcast News Package production recipe

The workspace includes an executable original study in `src/studies/scenes.ts`, selected with `news-package`. Its drawing commands are consumed by `src/studies/pixi-renderer.ts`; geometry and time sampling are shared with the gallery renderer. All copy lives in `shared/locales/en/style-studies.json`.

In an untouched starter, run `npm run example -- news-package`, then `npm run dev`. The command refuses to replace an authored film, retains starter backups in `production/example-backup/`, and writes an 8-second study with its own resource tracks. `npm run export:mp4` uses this installed film normally. To use the recipe inside an existing film, import `studyFrame()` and `StudyRenderer`, then compose the selected scene into the project's timeline instead of running the installer.

## Evidence and sources

The company's or institution's own page, the exchange's own data, or a government statistics portal for every number (log the claim and quoted wording). For pictures, ask in order: the user's own images first; generated illustrative plates only if the user wants them, tagged `ILLUSTRATION` for as long as visible and never standing in for the event, a place in the news or a person; failing that, Wikimedia Commons (CC0, public domain or CC BY only), U.S. federal agencies (NASA, NOAA, NARA, USGS — public domain), Internet Archive (public domain, CC0 or CC BY items; U.S. works before 1931 are public domain), or abstract backgrounds drawn in code. Record every asset in `production/CREDITS.md` and every claim in `production/FACTS.md`.

## Adaptation decisions

- Build the brand plate as one `Graphics` parallelogram reused for the sting, the bug, the desk front and the end card, driven by a single position/scale tween rather than four separate assets.
- Build the split-flap board as two `Container`s clipped to top and bottom halves, cross-fading the old and new tile faces on the flip; drive the threshold chart's line head and bars from one shared series.
- Draw the strap, tab, source line and corner tag inside each wipe's own clip (one state per side of the transition), never as a single overlay drawn once on top of everything, so the package never lags the picture by a frame.

The study is silent, original procedural art with illustrative values, labelled as such; it demonstrates material, layout and motion, not evidence. Replace its stand-ins with the real data, pictures or footage described above, never with unlabelled generated imagery. The gallery preview runs the package graphics end to end with no footage, illustrative throughout and labelled as such. Configure the subject, palette, scene sequence, duration and soundtrack from the brief.

Use `src/studies/timing.ts` for deterministic easing, seeded variation, measured stroke truncation and cue helpers. `window.animaguru.texts` exposes visible study text bounds for `npm run review`; text declarations alone do not count as visual proof. Inspect the actual frames as well.

## Sources and attribution

Inspired by the following pinned references; source-specific 3D/media dependencies are not bundled. New study art and scene geometry are original. The workspace's `VIDEO-STYLE-NOTICES.txt` preserves the repository notices and clarifies third-party asset scope.

- [styles/news-package/STYLE.md](https://github.com/lemomo-ai/lemo-opuscar/blob/77ee8318df779b0736d7de0abe24387e51023735/styles/news-package/STYLE.md)
- [styles/news-package/demo/main.js](https://github.com/lemomo-ai/lemo-opuscar/blob/77ee8318df779b0736d7de0abe24387e51023735/styles/news-package/demo/main.js)
