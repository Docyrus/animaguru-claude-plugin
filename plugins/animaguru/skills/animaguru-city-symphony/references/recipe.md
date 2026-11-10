# Time-lapse Symphony production recipe

The workspace includes an executable original study in `src/studies/scenes.ts`, selected with `city-symphony`. Its drawing commands are consumed by `src/studies/pixi-renderer.ts`; geometry and time sampling are shared with the gallery renderer. All copy lives in `shared/locales/en/style-studies.json`.

In an untouched starter, run `npm run example -- city-symphony`, then `npm run dev`. The command refuses to replace an authored film, retains starter backups in `production/example-backup/`, and writes an 8-second study with its own resource tracks. `npm run export:mp4` uses this installed film normally. To use the recipe inside an existing film, import `studyFrame()` and `StudyRenderer`, then compose the selected scene into the project's timeline instead of running the installer.

## Evidence and sources

Wikimedia Commons (modern time-lapse, aerial and slow-motion footage under CC BY/CC0; the Carol M. Highsmith Archive for public-domain photographs; check the licence on each file page, and that a YouTube/Vimeo import carries a passed review, not merely a pending one), Library of Congress (archive film published in the US before 1931 is public domain; a "no known restrictions" statement alone is not enough), NASA (orbital night photography of cities, public domain), Internet Archive (scanned books marked NOT_IN_COPYRIGHT with a pre-1931 date for the closing quote), Natural Earth (public domain map geometry). Download into the film's `public/` or `production/` folders, log every request, and record each asset in `production/CREDITS.md` and each number, with its quoted wording, in `production/FACTS.md`.

## Adaptation decisions

- Approximate frame-blended "light rivers" by accumulating a short trail of recent texture samples into a `RenderTexture` with decaying alpha, or by motion-blurring a sped-up `Sprite`/video texture; cap the blend window so clouds don't turn to mush.
- Drive every cut, slam and grid stage from one shared `bar(n, beat)` timing function, so density always matches the score's current subdivision rather than a typed shot length.
- Build the number card and the day-ring clock as `Graphics`/`Text`, locking digits one per sixteenth note; apply the release-print grade (S-curve, warm highlights, bloom above a luma threshold, grain) with a `ColorMatrixFilter` plus a small bloom pass, shared by every shot including archive film.

The study is silent, original procedural art with illustrative values, labelled as such; it demonstrates material, layout and motion, not evidence. Replace its stand-ins with the real time-lapse, aerial, archive or photographic footage described above, never with generated imagery. The gallery preview is a procedural city rendered in code, not a real skyline, labelled as such. Configure the subject, palette, scene sequence, duration and soundtrack from the brief.

Use `src/studies/timing.ts` for deterministic easing, seeded variation, measured stroke truncation and cue helpers. `window.animaguru.texts` exposes visible study text bounds for `npm run review`; text declarations alone do not count as visual proof. Inspect the actual frames as well.

## Sources and attribution

Inspired by the following pinned references; source-specific 3D/media dependencies are not bundled. New study art and scene geometry are original. The workspace's `VIDEO-STYLE-NOTICES.txt` preserves the repository notices and clarifies third-party asset scope.

- [styles/city-symphony/STYLE.md](https://github.com/lemomo-ai/lemo-opuscar/blob/77ee8318df779b0736d7de0abe24387e51023735/styles/city-symphony/STYLE.md)
- [styles/city-symphony/demo/index.html](https://github.com/lemomo-ai/lemo-opuscar/blob/77ee8318df779b0736d7de0abe24387e51023735/styles/city-symphony/demo/index.html)
