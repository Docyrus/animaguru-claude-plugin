# Dark Tech Stage production recipe

The workspace includes an executable original study in `src/studies/scenes.ts`, selected with `dark-tech-stage`. Its drawing commands are consumed by `src/studies/pixi-renderer.ts`; geometry and time sampling are shared with the gallery renderer. All copy lives in `shared/locales/en/style-studies.json`.

In an untouched starter, run `npm run example -- dark-tech-stage`, then `npm run dev`. The command refuses to replace an authored film, retains starter backups in `production/example-backup/`, and writes an 8-second study with its own resource tracks. `npm run export:html` and `npm run export:mp4` use this installed film normally. To use the recipe inside an existing film, import `studyFrame()` and `StudyRenderer`, then compose the selected scene into the project's timeline instead of running the installer.

## Kit pieces for this look

For a new film, start from the shared kit (`runtime/kit` in a workspace) rather than the study renderer:

- `darkStage(film, { primary, accent, pulse })` adds the backdrop: deep vertical gradient, a slowly scrolling 72 px hairline grid at 3.5% alpha, two drifting brand glows, a centre bloom driven by `pulse` (for example `t => bump(win(t, drop - 0.1, 2.6))` on the music drop), seeded dust and a vignette.
- `gradientFill(["#B45FC4", "#8E77E0", "#5566E8"])` on one emphasized headline line, never on body text. Headlines use the heading family at weight 800, 72–96 px on a 1080-wide frame.
- `panel(w, h, { fill, stroke: primary, strokeAlpha: 0.22 })` for interface cards, `Pill` for source and status chips (fade `highlight.alpha` in to light one), and `Badge` to flip a problem "!" into a check when the product resolves it.
- `partialLine` with `bezier` draws wires and connections on with time; `pointAt` moves data packets along them.
- `rasterSvg(logoUrl, width)` gives crisp logo textures at the exact size needed.

## Adaptation decisions

- Give each subject a presentation plane and a quiet text region; accent light marks hierarchy rather than decorating every edge.
- Derive accumulated items and their final grid positions from one table; arrivals can land on a cue while the camera remains continuous.
- Preserve real interface labels and supported states. Abstract panels are conceptual illustrations, not evidence of shipped features.

The study is silent, original procedural art. Photographic studies use illustrated media cards and product studies use an illustrative object; replace these with actual supplied/generated assets for production. It demonstrates material, transforms and layout rather than proving real product claims. Configure an original subject, palette, scene sequence, duration and soundtrack from the brief.

Use `src/studies/timing.ts` for deterministic easing, seeded variation, measured stroke truncation and cue helpers. `window.animaguru.texts` exposes visible study text bounds for `npm run review`; text declarations alone do not count as visual proof. Inspect the actual frames as well.

## Sources and attribution

Inspired by the following pinned references; source-specific 3D/media dependencies are not bundled. New study art and scene geometry are original. The workspace's `VIDEO-STYLE-NOTICES.txt` preserves the repository notices and clarifies third-party asset scope.

- [styles/dark-keynote/STYLE.md](https://github.com/lemomo-ai/lemo-opuscar/blob/b65efe6ea393fdc71212898ea4c57c754cfefa46/styles/dark-keynote/STYLE.md)
- [styles/dark-keynote/demo/engine.js](https://github.com/lemomo-ai/lemo-opuscar/blob/b65efe6ea393fdc71212898ea4c57c754cfefa46/styles/dark-keynote/demo/engine.js)
- [prompts/howdevelop-733090.md](https://github.com/yihui-dev/awesome-opus5-5-videos/blob/3d54892e2ae5b0e8d337171e6508bba4cec01ab8/prompts/howdevelop-733090.md)
