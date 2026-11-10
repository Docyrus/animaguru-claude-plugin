# Exploded Teardown production recipe

The workspace includes an executable original study in `src/studies/scenes.ts`, selected with `exploded-teardown`. Its drawing commands are consumed by `src/studies/pixi-renderer.ts`; geometry and time sampling are shared with the gallery renderer. All copy lives in `shared/locales/en/style-studies.json`.

In an untouched starter, run `npm run example -- exploded-teardown`, then `npm run dev`. The command refuses to replace an authored film, retains starter backups in `production/example-backup/`, and writes an 8-second study with its own resource tracks. `npm run export:html` and `npm run export:mp4` use this installed film normally. To use the recipe inside an existing film, import `studyFrame()` and `StudyRenderer`, then compose the selected scene into the project's timeline instead of running the installer.

## Evidence and sources

The user's own CAD, layout files and BOM first. For a public product, open hardware (GitHub, the OSHWA list, Hackaday.io) with its original CAD, and component datasheets from the maker. CC0, public domain, CC BY and MIT are fine with credit; CERN-OHL, CC BY-SA and GPL hardware: name the terms and ask first. Download into the film's `public/` or `production/` folders, log every request, and record each asset in `production/CREDITS.md` and each claim in `production/FACTS.md`. Burn a readable credit into the frame where the medium calls for one.

## Adaptation decisions

- Convert the CAD offline to simple extruded outlines per layer (outline, holes, heights). Draw each layer's faces with `Graphics` from one camera, layer by layer along the lift axis, and map the board artwork onto the board's top face with a `PerspectiveMesh`.
- Paint the board texture once from the layout (copper, pads, silkscreen). Emitters are additive sprites that switch on while the layers are apart.
- Project labels and dimension lines with `Graphics` and `Text` every frame, and interpolate camera keys monotonically so a macro hold really holds.

The study is silent, original procedural art with illustrative values, labelled as such; it demonstrates material, light, layout and motion, not evidence. Replace its stand-ins with the real data, imagery or scans described above, never with generated imagery. The gallery preview is rendered in code from an original model whose dimensions it labels. Configure the subject, palette, scene sequence, duration and soundtrack from the brief.

Use `src/studies/timing.ts` for deterministic easing, seeded variation, measured stroke truncation and cue helpers. `window.animaguru.texts` exposes visible study text bounds for `npm run review`; text declarations alone do not count as visual proof. Inspect the actual frames as well.

## Sources and attribution

Inspired by the following pinned references; source-specific 3D/media dependencies are not bundled. New study art and scene geometry are original. The workspace's `VIDEO-STYLE-NOTICES.txt` preserves the repository notices and clarifies third-party asset scope.

- [styles/teardown/STYLE.md](https://github.com/lemomo-ai/lemo-opuscar/blob/b5e8ef93930b6d828f352055a689320f138237b1/styles/teardown/STYLE.md)
- [styles/teardown/demo/src/main.js](https://github.com/lemomo-ai/lemo-opuscar/blob/b5e8ef93930b6d828f352055a689320f138237b1/styles/teardown/demo/src/main.js)
- [styles/teardown/demo/src/overlay.js](https://github.com/lemomo-ai/lemo-opuscar/blob/b5e8ef93930b6d828f352055a689320f138237b1/styles/teardown/demo/src/overlay.js)
