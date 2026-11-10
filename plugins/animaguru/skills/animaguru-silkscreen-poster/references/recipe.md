# Silkscreen Poster production recipe

The workspace includes an executable original study in `src/studies/scenes.ts`, selected with `silkscreen-poster`. Its drawing commands are consumed by `src/studies/pixi-renderer.ts`; geometry and time sampling are shared with the gallery renderer. All copy lives in `shared/locales/en/style-studies.json`.

In an untouched starter, run `npm run example -- silkscreen-poster`, then `npm run dev`. The command refuses to replace an authored film, retains starter backups in `production/example-backup/`, and writes an 8-second study with its own resource tracks. `npm run export:html` and `npm run export:mp4` use this installed film normally. To use the recipe inside an existing film, import `studyFrame()` and `StudyRenderer`, then compose the selected scene into the project's timeline instead of running the installer.

## Adaptation decisions

- Compose the finished image before scheduling the print. Each opaque ink has its own silhouette, knockout and registration offset.
- A squeegee pull moves steadily, with a ragged but seeded front; do not substitute an opacity fade for the printing action.
- Keep shape unions free of internal seams and preserve paper-white holes. Poster facts arrive with their layer and remain long enough to read.

The study is silent, original procedural art. Photographic studies use illustrated media cards and product studies use an illustrative object; replace these with actual supplied/generated assets for production. It demonstrates material, transforms and layout rather than proving real product claims. Configure an original subject, palette, scene sequence, duration and soundtrack from the brief.

Use `src/studies/timing.ts` for deterministic easing, seeded variation, measured stroke truncation and cue helpers. `window.animaguru.texts` exposes visible study text bounds for `npm run review`; text declarations alone do not count as visual proof. Inspect the actual frames as well.

## Sources and attribution

Inspired by the following pinned references; source-specific 3D/media dependencies are not bundled. New study art and scene geometry are original. The workspace's `VIDEO-STYLE-NOTICES.txt` preserves the repository notices and clarifies third-party asset scope.

- [styles/silkscreen-poster/STYLE.md](https://github.com/lemomo-ai/lemo-opuscar/blob/b65efe6ea393fdc71212898ea4c57c754cfefa46/styles/silkscreen-poster/STYLE.md)
- [styles/silkscreen-poster/demo/engine/silk.js](https://github.com/lemomo-ai/lemo-opuscar/blob/b65efe6ea393fdc71212898ea4c57c754cfefa46/styles/silkscreen-poster/demo/engine/silk.js)
