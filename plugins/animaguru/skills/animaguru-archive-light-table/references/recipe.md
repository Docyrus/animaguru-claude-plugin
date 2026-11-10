# Archive Light Table production recipe

The workspace includes an executable original study in `src/studies/scenes.ts`, selected with `archive-light-table`. Its drawing commands are consumed by `src/studies/pixi-renderer.ts`; geometry and time sampling are shared with the gallery renderer. All copy lives in `shared/locales/en/style-studies.json`.

In an untouched starter, run `npm run example -- archive-light-table`, then `npm run dev`. The command refuses to replace an authored film, retains starter backups in `production/example-backup/`, and writes an 8-second study with its own resource tracks. `npm run export:html` and `npm run export:mp4` use this installed film normally. To use the recipe inside an existing film, import `studyFrame()` and `StudyRenderer`, then compose the selected scene into the project's timeline instead of running the installer.

## Evidence and sources

The Library of Congress (check each item's rights statement), Smithsonian Open Access and the Rijksmuseum (CC0), NARA, the NASA Image and Video Library (generally not copyrighted) and Europeana (rights per item). "No known restrictions" and CC BY-SA are not CC0: name the terms and ask first. For brand history, ask for the user's scans, archive numbers and right to use them. Download into the film's `public/` or `production/` folders, log every request, and record each asset in `production/CREDITS.md` and each claim in `production/FACTS.md`. Burn a readable credit into the frame where the medium calls for one.

## Adaptation decisions

- Lay the objects as sprites at true size on one table `Container` over a near-white emissive backdrop; a negative is its positive scan through a transmission curve in a small filter.
- The loupe renders a magnified copy of the table inside a circular mask, with a `DisplacementFilter` for the pincushion and slight per-channel offsets for fringes. The develop front is a growing radial mask between the negative and positive copies.
- Into the photograph: grow the lens mask past the frame while the view inside widens to the whole picture, then give it depth with two or three cut layers and a small dolly, small enough that fills stay hidden.

The study is silent, original procedural art with illustrative values, labelled as such; it demonstrates material, light, layout and motion, not evidence. Replace its stand-ins with the real data, imagery or scans described above, never with generated imagery. The gallery preview is three public-domain NASA Ames scans; their negatives are simulated from the positive scans, as the frame says. Configure the subject, palette, scene sequence, duration and soundtrack from the brief.

Use `src/studies/timing.ts` for deterministic easing, seeded variation, measured stroke truncation and cue helpers. `window.animaguru.texts` exposes visible study text bounds for `npm run review`; text declarations alone do not count as visual proof. Inspect the actual frames as well.

## Sources and attribution

Inspired by the following pinned references; source-specific 3D/media dependencies are not bundled. New study art and scene geometry are original. The workspace's `VIDEO-STYLE-NOTICES.txt` preserves the repository notices and clarifies third-party asset scope.

- [styles/archive-lighttable/STYLE.md](https://github.com/lemomo-ai/lemo-opuscar/blob/b5e8ef93930b6d828f352055a689320f138237b1/styles/archive-lighttable/STYLE.md)
- [styles/archive-lighttable/demo/film.js](https://github.com/lemomo-ai/lemo-opuscar/blob/b5e8ef93930b6d828f352055a689320f138237b1/styles/archive-lighttable/demo/film.js)
