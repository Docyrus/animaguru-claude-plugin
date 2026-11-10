# White Model Projection production recipe

The workspace includes an executable original study in `src/studies/scenes.ts`, selected with `white-model-projection`. Its drawing commands are consumed by `src/studies/pixi-renderer.ts`; geometry and time sampling are shared with the gallery renderer. All copy lives in `shared/locales/en/style-studies.json`.

In an untouched starter, run `npm run example -- white-model-projection`, then `npm run dev`. The command refuses to replace an authored film, retains starter backups in `production/example-backup/`, and writes an 8-second study with its own resource tracks. `npm run export:mp4` uses this installed film normally. To use the recipe inside an existing film, import `studyFrame()` and `StudyRenderer`, then compose the selected scene into the project's timeline instead of running the installer.

## Evidence and sources

3DBAG (Netherlands, CC BY 4.0), PLATEAU (Japan), city open-data portals (footprints with heights or floors, zoning, plans) or the user's own plans and surveys. OpenStreetMap and Overture are ODbL: name the terms and ask first. Compute the sun from the place's latitude and a real date (NOAA/Meeus). Download into the film's `public/` or `production/` folders, log every request, and record each asset in `production/CREDITS.md` and each claim in `production/FACTS.md`. Burn a readable credit into the frame where the medium calls for one.

## Adaptation decisions

- Precompute footprints and heights in model units. Draw extruded blocks as `Graphics` faces in painter's order from one camera, or render a set of white-model plates offline with matching per-building masks for heavy scenes; describe the method as 2.5D.
- Colour each visible face from its normal and the projector direction: white × house light, plus layer colour × (0.42 + 0.58 × facing) × throw mask. A layer is per-building state, not a texture.
- A rising level is a per-face clip at the current height with a soft bright crest; decades switch on per building with a short flash. Pins and readouts are `Graphics` and `Text` through the same projection.

The study is silent, original procedural art with illustrative values, labelled as such; it demonstrates material, light, layout and motion, not evidence. Replace its stand-ins with the real data, imagery or scans described above, never with generated imagery. The gallery preview is rendered in code from an illustrative district. Configure the subject, palette, scene sequence, duration and soundtrack from the brief.

Use `src/studies/timing.ts` for deterministic easing, seeded variation, measured stroke truncation and cue helpers. `window.animaguru.texts` exposes visible study text bounds for `npm run review`; text declarations alone do not count as visual proof. Inspect the actual frames as well.

## Sources and attribution

Inspired by the following pinned references; source-specific 3D/media dependencies are not bundled. New study art and scene geometry are original. The workspace's `VIDEO-STYLE-NOTICES.txt` preserves the repository notices and clarifies third-party asset scope.

- [styles/white-model/STYLE.md](https://github.com/lemomo-ai/lemo-opuscar/blob/b5e8ef93930b6d828f352055a689320f138237b1/styles/white-model/STYLE.md)
- [styles/white-model/demo/studio.js](https://github.com/lemomo-ai/lemo-opuscar/blob/b5e8ef93930b6d828f352055a689320f138237b1/styles/white-model/demo/studio.js)
- [styles/white-model/demo/overlay.js](https://github.com/lemomo-ai/lemo-opuscar/blob/b5e8ef93930b6d828f352055a689320f138237b1/styles/white-model/demo/overlay.js)
