# Visual Investigation production recipe

The workspace includes an executable original study in `src/studies/scenes.ts`, selected with `visual-investigation`. Its drawing commands are consumed by `src/studies/pixi-renderer.ts`; geometry and time sampling are shared with the gallery renderer. All copy lives in `shared/locales/en/style-studies.json`.

In an untouched starter, run `npm run example -- visual-investigation`, then `npm run dev`. The command refuses to replace an authored film, retains starter backups in `production/example-backup/`, and writes an 8-second study with its own resource tracks. `npm run export:html` and `npm run export:mp4` use this installed film normally. To use the recipe inside an existing film, import `studyFrame()` and `StudyRenderer`, then compose the selected scene into the project's timeline instead of running the installer.

## Evidence and sources

Internet Archive (NARA-donated Universal Newsreels 1929–1967 are public domain; other newsreel companies are not, even when tagged PD by an uploader), Wikimedia Commons (U.S. federal work — Navy, NASA, NARA, NOAA, USGS — is public domain; treat "not renewed" agency-photo claims, e.g. AP/INS/Wide World, as uncertain and skip), NASA (public domain except marked third-party items), Library of Congress and national archives (read each rights statement; "no known restrictions" is not a licence), USGS The National Map (historical topographic maps, public domain). Download into the film's `public/` or `production/` folders, log every request, and record each asset in `production/CREDITS.md` and each claim, with inferences kept separate, in `production/FACTS.md`.

## Adaptation decisions

- Build the sync grid and the evidence-map links as `Graphics` paths drawn progressively (stroke-by-length) from one shared `playhead()` keyframe list, reused by the audio mix so clockwork ticks and picture stay locked together.
- For the freeze-circle-magnify move, freeze a video texture's current frame, then render a cropped, scaled copy of the same texture inside a circular mask for the loupe, so the magnified detail is genuinely the same pixels.
- Keep the map and plan panels as `Graphics` line drawings (or a `Mesh` for an oblique plan) with one projection function mapping real survey coordinates to screen space, reused by every panel that cites a position.

The study is silent, original procedural art with illustrative values, labelled as such; it demonstrates material, layout and motion, not evidence. Replace its stand-ins with the real footage, documents, photographs and sound described above, never with generated imagery. The gallery preview uses illustrative evidence panels with no real case behind them, labelled as such. Configure the subject, palette, scene sequence, duration and soundtrack from the brief.

Use `src/studies/timing.ts` for deterministic easing, seeded variation, measured stroke truncation and cue helpers. `window.animaguru.texts` exposes visible study text bounds for `npm run review`; text declarations alone do not count as visual proof. Inspect the actual frames as well.

## Sources and attribution

Inspired by the following pinned references; source-specific 3D/media dependencies are not bundled. New study art and scene geometry are original. The workspace's `VIDEO-STYLE-NOTICES.txt` preserves the repository notices and clarifies third-party asset scope.

- [styles/visual-investigation/STYLE.md](https://github.com/lemomo-ai/lemo-opuscar/blob/77ee8318df779b0736d7de0abe24387e51023735/styles/visual-investigation/STYLE.md)
- [styles/visual-investigation/demo/index.html](https://github.com/lemomo-ai/lemo-opuscar/blob/77ee8318df779b0736d7de0abe24387e51023735/styles/visual-investigation/demo/index.html)
