# Aurora & Glass production recipe

The workspace includes an executable original study in `src/studies/scenes.ts`, selected with `aurora-glass`. Its drawing commands are consumed by `src/studies/pixi-renderer.ts`; geometry and time sampling are shared with the gallery renderer. All copy lives in `shared/locales/en/style-studies.json`.

In an untouched starter, run `npm run example -- aurora-glass`, then `npm run dev`. The command refuses to replace an authored film, retains starter backups in `production/example-backup/`, and writes an 8-second study with its own resource tracks. `npm run export:mp4` uses this installed film normally. To use the recipe inside an existing film, import `studyFrame()` and `StudyRenderer`, then compose the selected scene into the project's timeline instead of running the installer.

## Assets and licences

Draw the colour fields, glass and interface in code. When the cards should show real product screens, photographs or icons, use the user's own material or licence-clean sources (CC0, public domain, or a licence the user confirms), and record each in `production/CREDITS.md`. Use fonts the project may embed (OFL or licensed faces); a light, open sans suits the style. Never reproduce another company's interface or trademark unless the user owns it.

## Adaptation decisions

- Render the colour fields as large `Graphics` circles in one container behind a single `BlurFilter` (strength 80–150) at a reduced filter resolution, or as a small mesh-gradient fragment shader; the field holds no detail, so half resolution is invisible.
- For each card, render the layers behind it into a `RenderTexture`, show the card's region of that texture through a `BlurFilter` (strength 20–40) masked by a rounded-rectangle `Graphics`, then add the white fill, the one-pixel inner stroke and a sheen gradient. Drive edge brightness from the angle between each edge's normal and the moving light, with a gradient stroke or a small shader.
- Make the lens a small filter over the back texture: sample magnified toward its centre, displace along the rim normal with a slightly different offset per colour channel, and add the specular rim. Morph it into a capsule by animating its half sizes and corner radius together.
- Overlay a fixed noise sprite or a noise filter at 3–5 % and export at a bitrate that keeps it, or banding returns in the MP4.

The study is silent, original procedural art with an invented product; it demonstrates material, layout and motion rather than real product claims. Its stacked translucent ellipses and flat panes stand in for the blur and frosting described above. Configure an original subject, palette, scene sequence, duration and soundtrack from the brief.

Use `src/studies/timing.ts` for deterministic easing, seeded variation, measured stroke truncation and cue helpers. `window.animaguru.texts` exposes visible study text bounds for `npm run review`; text declarations alone do not count as visual proof. Inspect the actual frames as well.

## Sources and attribution

Inspired by the following pinned references; source-specific 3D/media dependencies are not bundled. New study art and scene geometry are original. The workspace's `VIDEO-STYLE-NOTICES.txt` preserves the repository notices and clarifies third-party asset scope.

- [prompts/12-aurora-glass.md](https://github.com/Vincentwei1021/mg-styles-15/blob/49052d80bfaf9fa8412cc9710530e5e95a3b8d8c/prompts/12-aurora-glass.md)
- [demos/12-aurora-glass/main.js](https://github.com/Vincentwei1021/mg-styles-15/blob/49052d80bfaf9fa8412cc9710530e5e95a3b8d8c/demos/12-aurora-glass/main.js)
