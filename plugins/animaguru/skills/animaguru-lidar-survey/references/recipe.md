# LiDAR Survey production recipe

The workspace includes an executable original study in `src/studies/scenes.ts`, selected with `lidar-survey`. Its drawing commands are consumed by `src/studies/pixi-renderer.ts`; geometry and time sampling are shared with the gallery renderer. All copy lives in `shared/locales/en/style-studies.json`.

In an untouched starter, run `npm run example -- lidar-survey`, then `npm run dev`. The command refuses to replace an authored film, retains starter backups in `production/example-backup/`, and writes an 8-second study with its own resource tracks. `npm run export:mp4` uses this installed film normally. To use the recipe inside an existing film, import `studyFrame()` and `StudyRenderer`, then compose the selected scene into the project's timeline instead of running the installer.

## Evidence and sources

USGS 3DEP (Entwine Point Tiles), OpenTopography (licence per collection), AHN (Netherlands, CC0), England's Environment Agency LiDAR (OGL), IGN LiDAR HD, PNOA-LiDAR, NLS Finland and LINZ (CC BY 4.0); read each portal's terms and fetch subsets by box. Ask for the user's own scans when the film is about their asset. Download into the film's `public/` or `production/` folders, log every request, and record each asset in `production/CREDITS.md` and each claim in `production/FACTS.md`. Burn a readable credit into the frame where the medium calls for one.

## Adaptation decisions

- Quantise the cloud offline (positions, height above ground, class, intensity) into a binary asset. Project points each frame on the CPU or in a vertex shader and draw them with a `ParticleContainer` or a custom point `Mesh` sized in world units, with distance fog.
- Bake the bare-earth surface into a hillshaded, contour-lined texture from the ground model (raking light at 20–35°) and reveal it behind the front with a mask while the points ahead of it remain.
- Draw traced features, the ruler and readings with `Graphics` through the same projection. Keep the camera on one C1 spline of target, distance, heading and pitch so it never stops.

The study is silent, original procedural art with illustrative values, labelled as such; it demonstrates material, light, layout and motion, not evidence. Replace its stand-ins with the real data, imagery or scans described above, never with generated imagery. The gallery preview is a procedural cloud drawn in code, labelled on screen as not a real survey. Configure the subject, palette, scene sequence, duration and soundtrack from the brief.

Use `src/studies/timing.ts` for deterministic easing, seeded variation, measured stroke truncation and cue helpers. `window.animaguru.texts` exposes visible study text bounds for `npm run review`; text declarations alone do not count as visual proof. Inspect the actual frames as well.

## Sources and attribution

Inspired by the following pinned references; source-specific 3D/media dependencies are not bundled. New study art and scene geometry are original. The workspace's `VIDEO-STYLE-NOTICES.txt` preserves the repository notices and clarifies third-party asset scope.

- [styles/lidar-survey/STYLE.md](https://github.com/lemomo-ai/lemo-opuscar/blob/b5e8ef93930b6d828f352055a689320f138237b1/styles/lidar-survey/STYLE.md)
- [styles/lidar-survey/demo/film.js](https://github.com/lemomo-ai/lemo-opuscar/blob/b5e8ef93930b6d828f352055a689320f138237b1/styles/lidar-survey/demo/film.js)
