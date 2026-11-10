# Caption News production recipe

The workspace includes an executable original study in `src/studies/scenes.ts`, selected with `caption-news`. Its drawing commands are consumed by `src/studies/pixi-renderer.ts`; geometry and time sampling are shared with the gallery renderer. All copy lives in `shared/locales/en/style-studies.json`.

In an untouched starter, run `npm run example -- caption-news`, then `npm run dev`. The command refuses to replace an authored film, retains starter backups in `production/example-backup/`, and writes an 8-second study with its own resource tracks. `npm run export:mp4` uses this installed film normally. To use the recipe inside an existing film, import `studyFrame()` and `StudyRenderer`, then compose the selected scene into the project's timeline instead of running the installer.

## Evidence and sources

Wikimedia Commons (read the licence on each file page: CC0, public domain or CC BY are fine; not CC BY-SA, "no known restrictions", unclear licences or YouTube re-uploads), U.S. federal agencies (USDA, USGS, NASA, NOAA, NARA — works of federal employees are public domain), Internet Archive (public domain or CC0/CC BY items only; U.S. works published before 1931 are public domain), Library of Congress (read each item's rights statement). Official documents and data (reports, statistics, filings) come from the agency's own site. Download into the film's `public/` or `production/` folders, log every request, and record each asset in `production/CREDITS.md` and each claim with its quoted wording in `production/FACTS.md`. Burn a readable footage credit into the frame where the medium calls for one.

## Adaptation decisions

- Build the caption card and the ledger (data-card) ground as `Text` and `Graphics` over a `Sprite` or video-texture footage layer; the keyword's yellow block is a masked rect wiped left to right behind the chunk.
- Roll numbers in fixed-width digit cells (a monospace `Text` or `BitmapText` per digit, updated on the ticker) so a counter never jitters; keep its source tag in the same shot.
- Sweep the document highlight as a `Graphics` rect in a multiply-like blend over the scanned page sprite, animated by an exact clip mask rather than opacity, so the sentence reads as marked, not merely tinted.

The study is silent, original procedural art with illustrative values, labelled as such; it demonstrates material, layout and motion, not evidence. Replace its stand-ins with the real footage, photos, documents or data described above, never with generated imagery. The gallery preview uses procedural placeholder footage and documents, labelled illustrative, to demonstrate the caption, keyword-wipe and highlight system without claiming any real source. Configure the subject, palette, scene sequence, duration and soundtrack from the brief.

Use `src/studies/timing.ts` for deterministic easing, seeded variation, measured stroke truncation and cue helpers. `window.animaguru.texts` exposes visible study text bounds for `npm run review`; text declarations alone do not count as visual proof. Inspect the actual frames as well.

## Sources and attribution

Inspired by the following pinned references; source-specific 3D/media dependencies are not bundled. New study art and scene geometry are original. The workspace's `VIDEO-STYLE-NOTICES.txt` preserves the repository notices and clarifies third-party asset scope.

- [styles/caption-news/STYLE.md](https://github.com/lemomo-ai/lemo-opuscar/blob/77ee8318df779b0736d7de0abe24387e51023735/styles/caption-news/STYLE.md)
- [styles/caption-news/demo/main.js](https://github.com/lemomo-ai/lemo-opuscar/blob/77ee8318df779b0736d7de0abe24387e51023735/styles/caption-news/demo/main.js)
