# Data Physicalization production recipe

The workspace includes an executable original study in `src/studies/scenes.ts`, selected with `data-physicalization`. Its drawing commands are consumed by `src/studies/pixi-renderer.ts`; geometry and time sampling are shared with the gallery renderer. All copy lives in `shared/locales/en/style-studies.json`.

In an untouched starter, run `npm run example -- data-physicalization`, then `npm run dev`. The command refuses to replace an authored film, retains starter backups in `production/example-backup/`, and writes an 8-second study with its own resource tracks. `npm run export:mp4` uses this installed film normally. To use the recipe inside an existing film, import `studyFrame()` and `StudyRenderer`, then compose the selected scene into the project's timeline instead of running the installer.

## Evidence and sources

Our World in Data (credit OWID and the original source), World Bank Open Data and Eurostat (CC BY 4.0), US Census, BLS and EIA (public domain), national statistics offices, or the user's own reports with the document they come from. Textures and HDRIs from Poly Haven or ambientCG (CC0). Download into the film's `public/` or `production/` folders, log every request, and record each asset in `production/CREDITS.md` and each claim in `production/FACTS.md`. Burn a readable credit into the frame where the medium calls for one.

## Adaptation decisions

- Lay out the stacks from one table of values and the unit. Draw each piece as a small shaded box (`Graphics` faces in painter's order, or one shaded piece sprite per material reused with per-piece tint and offset), back to front.
- Bake the base (for example a walnut slab with inlaid ticks and labels) into a texture, cast shadows as blurred sprites along one light vector, and soften far layers with a `BlurFilter` for depth of field.
- Pin readings to projected piece corners with a leader, a material swatch and a paper plate, and keep them inside a safe box while the camera tracks.

The study is silent, original procedural art with illustrative values, labelled as such; it demonstrates material, light, layout and motion, not evidence. Replace its stand-ins with the real data, imagery or scans described above, never with generated imagery. The gallery preview is rendered in code with illustrative values. Configure the subject, palette, scene sequence, duration and soundtrack from the brief.

Use `src/studies/timing.ts` for deterministic easing, seeded variation, measured stroke truncation and cue helpers. `window.animaguru.texts` exposes visible study text bounds for `npm run review`; text declarations alone do not count as visual proof. Inspect the actual frames as well.

## Sources and attribution

Inspired by the following pinned references; source-specific 3D/media dependencies are not bundled. New study art and scene geometry are original. The workspace's `VIDEO-STYLE-NOTICES.txt` preserves the repository notices and clarifies third-party asset scope.

- [styles/data-physical/STYLE.md](https://github.com/lemomo-ai/lemo-opuscar/blob/b5e8ef93930b6d828f352055a689320f138237b1/styles/data-physical/STYLE.md)
- [styles/data-physical/demo/set.js](https://github.com/lemomo-ai/lemo-opuscar/blob/b5e8ef93930b6d828f352055a689320f138237b1/styles/data-physical/demo/set.js)
- [styles/data-physical/demo/film.js](https://github.com/lemomo-ai/lemo-opuscar/blob/b5e8ef93930b6d828f352055a689320f138237b1/styles/data-physical/demo/film.js)
