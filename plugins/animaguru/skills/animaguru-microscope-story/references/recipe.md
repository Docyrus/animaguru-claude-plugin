# Microscope Story production recipe

The workspace includes an executable original study in `src/studies/scenes.ts`, selected with `microscope-story`. Its drawing commands are consumed by `src/studies/pixi-renderer.ts`; geometry and time sampling are shared with the gallery renderer. All copy lives in `shared/locales/en/style-studies.json`.

In an untouched starter, run `npm run example -- microscope-story`, then `npm run dev`. The command refuses to replace an authored film, retains starter backups in `production/example-backup/`, and writes an 8-second study with its own resource tracks. `npm run export:html` and `npm run export:mp4` use this installed film normally. To use the recipe inside an existing film, import `studyFrame()` and `StudyRenderer`, then compose the selected scene into the project's timeline instead of running the installer.

## Evidence and sources

OpenSlide test data (check each file's licence line), NCI Imaging Data Commons (licence per collection), the Cell Image Library, Wellcome Collection, Wikimedia Commons filtered by licence, and NIH or CDC galleries; prefer files whose metadata carries the pixel size. Not usable: NC images, journal figures, AI images. Download into the film's `public/` or `production/` folders, log every request, and record each asset in `production/CREDITS.md` and each claim in `production/FACTS.md`. Burn a readable credit into the frame where the medium calls for one.

## Adaptation decisions

- Export pyramid levels as textures registered in one world frame (level-0 pixels). Draw the finest level that is not upsampled and cross-blend the next one; the camera is a similarity transform interpolated as a log spiral about the target point.
- Focus breaths use a `BlurFilter` whose strength follows the objective events; the focal sweep blends sharp and blurred copies through a tilted gradient mask.
- Count pixels offline from the plate and a stated threshold, reveal the counted mask behind a scan front as a tinted sprite, and build frosted panels from a blurred, darkened copy under a mask.

The study is silent, original procedural art with illustrative values, labelled as such; it demonstrates material, light, layout and motion, not evidence. Replace its stand-ins with the real data, imagery or scans described above, never with generated imagery. The gallery preview is a procedural specimen drawn in code, labelled on screen as not a real slide. Configure the subject, palette, scene sequence, duration and soundtrack from the brief.

Use `src/studies/timing.ts` for deterministic easing, seeded variation, measured stroke truncation and cue helpers. `window.animaguru.texts` exposes visible study text bounds for `npm run review`; text declarations alone do not count as visual proof. Inspect the actual frames as well.

## Sources and attribution

Inspired by the following pinned references; source-specific 3D/media dependencies are not bundled. New study art and scene geometry are original. The workspace's `VIDEO-STYLE-NOTICES.txt` preserves the repository notices and clarifies third-party asset scope.

- [styles/microscope/STYLE.md](https://github.com/lemomo-ai/lemo-opuscar/blob/b5e8ef93930b6d828f352055a689320f138237b1/styles/microscope/STYLE.md)
- [styles/microscope/demo/film.js](https://github.com/lemomo-ai/lemo-opuscar/blob/b5e8ef93930b6d828f352055a689320f138237b1/styles/microscope/demo/film.js)
