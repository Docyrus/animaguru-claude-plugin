# Photo & Footage Editorial production recipe

The workspace includes an executable original study in `src/studies/scenes.ts`, selected with `photo-footage-editorial`. Its drawing commands are consumed by `src/studies/pixi-renderer.ts`; geometry and time sampling are shared with the gallery renderer. All copy lives in `shared/locales/en/style-studies.json`.

In an untouched starter, run `npm run example -- photo-footage-editorial`, then `npm run dev`. The command refuses to replace an authored film, retains starter backups in `production/example-backup/`, and writes an 8-second study with its own resource tracks. `npm run export:html` and `npm run export:mp4` use this installed film normally. To use the recipe inside an existing film, import `studyFrame()` and `StudyRenderer`, then compose the selected scene into the project's timeline instead of running the installer.

## Adaptation decisions

- Use local supplied or generated media and one crop model for thumbnail-to-hero transitions. Important faces, product labels and controls guide crop choices.
- Await decoded video frames before resolving renderFrame. Large image sequences are optional and can make HTML5 packages impractical.
- Use a timeline trim/source-time contract for footage, not an independent live video clock. The bundled study uses original illustrated cards as stand-ins; replace them with real media for a real-product film.

The study is silent, original procedural art. Photographic studies use illustrated media cards and product studies use an illustrative object; replace these with actual supplied/generated assets for production. It demonstrates material, transforms and layout rather than proving real product claims. Configure an original subject, palette, scene sequence, duration and soundtrack from the brief.

Use `src/studies/timing.ts` for deterministic easing, seeded variation, measured stroke truncation and cue helpers. `window.animaguru.texts` exposes visible study text bounds for `npm run review`; text declarations alone do not count as visual proof. Inspect the actual frames as well.

## Sources and attribution

Inspired by the following pinned references; source-specific 3D/media dependencies are not bundled. New study art and scene geometry are original. The workspace's `VIDEO-STYLE-NOTICES.txt` preserves the repository notices and clarifies third-party asset scope.

- [prompts/twoclipping-000267.md](https://github.com/yihui-dev/awesome-opus5-5-videos/blob/3d54892e2ae5b0e8d337171e6508bba4cec01ab8/prompts/twoclipping-000267.md)
- [prompts/twoclipping-496100.md](https://github.com/yihui-dev/awesome-opus5-5-videos/blob/3d54892e2ae5b0e8d337171e6508bba4cec01ab8/prompts/twoclipping-496100.md)
- [prompts/bilimfili1-459762.md](https://github.com/yihui-dev/awesome-opus5-5-videos/blob/3d54892e2ae5b0e8d337171e6508bba4cec01ab8/prompts/bilimfili1-459762.md)
