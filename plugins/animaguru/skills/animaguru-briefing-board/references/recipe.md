# Engineering Briefing Board production recipe

The workspace includes an executable original study in `src/studies/scenes.ts`, selected with `briefing-board`. Its drawing commands are consumed by `src/studies/pixi-renderer.ts`; geometry and time sampling are shared with the gallery renderer. All copy lives in `shared/locales/en/style-studies.json`.

In an untouched starter, run `npm run example -- briefing-board`, then `npm run dev`. The command refuses to replace an authored film, retains starter backups in `production/example-backup/`, and writes an 8-second study with its own resource tracks. `npm run export:mp4` uses this installed film normally. To use the recipe inside an existing film, import `studyFrame()` and `StudyRenderer`, then compose the selected scene into the project's timeline instead of running the installer.

## Evidence and sources

Wikimedia Commons (read each file page's licence and author), national libraries and archives (check each item's rights statement), agency media pages and Flickr Commons; for the user's own product, site or people, ask for their photos. Every number comes from a cited spec, a measurement or the user's documents. Download into the film's `public/` or `production/` folders, log every request, and record each asset in `production/CREDITS.md` and each claim in `production/FACTS.md`. Burn a readable credit into the frame where the medium calls for one.

## Adaptation decisions

- Build the wall as one large `Container` in board pixels with layers by height (board, prints, props, tray). A camera container moves, scales and rolls it; raised layers get a slightly larger scale, which gives parallax.
- Bake the enamel, erased ghosts and frame into one texture. Draw ink with `Graphics` strokes revealed by measured length (`strokePoints`), lettering by slicing glyphs, and a slow reflection band as a blurred sprite.
- Prints are sprites with a blurred shadow offset along one light vector; they land with an ease-out and one small bounce while the shadow tightens. Magnets pop, tags swing on damped springs, and the stamp scales down with a camera jolt.

The study is silent, original procedural art with illustrative values, labelled as such; it demonstrates material, light, layout and motion, not evidence. Replace its stand-ins with the real data, imagery or scans described above, never with generated imagery. The gallery preview is drawn in code with marker sketches and illustrative values. Configure the subject, palette, scene sequence, duration and soundtrack from the brief.

Use `src/studies/timing.ts` for deterministic easing, seeded variation, measured stroke truncation and cue helpers. `window.animaguru.texts` exposes visible study text bounds for `npm run review`; text declarations alone do not count as visual proof. Inspect the actual frames as well.

## Sources and attribution

Inspired by the following pinned references; source-specific 3D/media dependencies are not bundled. New study art and scene geometry are original. The workspace's `VIDEO-STYLE-NOTICES.txt` preserves the repository notices and clarifies third-party asset scope.

- [styles/briefing-board/STYLE.md](https://github.com/lemomo-ai/lemo-opuscar/blob/b5e8ef93930b6d828f352055a689320f138237b1/styles/briefing-board/STYLE.md)
- [styles/briefing-board/demo/kit/board.js](https://github.com/lemomo-ai/lemo-opuscar/blob/b5e8ef93930b6d828f352055a689320f138237b1/styles/briefing-board/demo/kit/board.js)
- [styles/briefing-board/demo/kit/README.md](https://github.com/lemomo-ai/lemo-opuscar/blob/b5e8ef93930b6d828f352055a689320f138237b1/styles/briefing-board/demo/kit/README.md)
