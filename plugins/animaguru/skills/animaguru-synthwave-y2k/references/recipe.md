# Synthwave & Y2K production recipe

The workspace includes an executable original study in `src/studies/scenes.ts`, selected with `synthwave-y2k`. Its drawing commands are consumed by `src/studies/pixi-renderer.ts`; geometry and time sampling are shared with the gallery renderer. All copy lives in `shared/locales/en/style-studies.json`.

In an untouched starter, run `npm run example -- synthwave-y2k`, then `npm run dev`. The command refuses to replace an authored film, retains starter backups in `production/example-backup/`, and writes an 8-second study with its own resource tracks. `npm run export:mp4` uses this installed film normally. To use the recipe inside an existing film, import `studyFrame()` and `StudyRenderer`, then compose the selected scene into the project's timeline instead of running the installer.

## Assets and licences

The look needs no media: the grid, sun, mountains, palms, chrome type, windows and tape damage are all drawn. Generated media fits around it, never in place of editable type: a generated synthwave track, a narration, or a painted sky plate behind the code-drawn grid. Fonts must be OFL or bundled with the system that renders the film; record each in `production/CREDITS.md` with its licence. Do not reproduce real operating system interfaces, logos, startup sounds or cursors from commercial products; invent the desktop, its file names and its colours.

## Adaptation decisions

- Draw the floor grid as a `Mesh` or a full-screen `Filter` that intersects each pixel's ray with the ground plane (`z = eyeHeight · focal / (y − horizon)`), measures the distance to the nearest world-space line in screen pixels and fades lines into their average once a cell is under about 4 px. Scroll by adding camera travel to world `z`, not by moving sprites.
- Keep emissive parts (grid, horizon line, sun, crests, neon script, title outline) in one container rendered to a `RenderTexture`. Blur two copies (`BlurFilter` of about 4 and, at quarter resolution, about 30) and add them with `blendMode: "add"`; mask the emission under solid objects (palms, chrome face, windows) before blurring, so glow wraps their edges instead of washing over them.
- Build the chrome title once as a texture: stepped extrusion copies, a `FillGradient` face with a hard dark band at its middle, a thin light stroke for the bevel. Animate the slam by scaling that texture (average a few sub-frame scales for motion blur) and run the shine as a masked gradient sprite clipped to the face.
- Write the VHS chain as one custom `Filter` on the stage: per-row horizontal offsets from a hash of row and absolute time, YIQ chroma blur and delay (or an RGB split), luma noise, a moving tracking band, bottom-row skew and every-other-row darkening. Feed it a `glitch` uniform from a cue table so tears happen on purpose. Draw the on-screen display after the filter's damage stage, before scanlines.
- Quantise the scene clock for stepped passages (`Math.floor(t * 15) / 15`) and map a hit's next two frames to earlier scene times for the reverse stutter; the tape noise keeps reading the true time.
- Drive windows and the cursor from one cue table: pop (overshoot spring), move, press, drag outline, release, click (button down, ripple) and collapse (scale Y to a line, then X to a point).

The study is silent, original procedural art. It demonstrates material, transforms and layout rather than any real product or operating system. Configure an original subject, palette, scene sequence, duration and soundtrack from the brief.

Use `src/studies/timing.ts` for deterministic easing, seeded variation, measured stroke truncation and cue helpers. `window.animaguru.texts` exposes visible study text bounds for `npm run review`; text declarations alone do not count as visual proof. Inspect the actual frames as well.

## Sources and attribution

Inspired by the following pinned reference; no source code, assets or audio are bundled. New study art and scene geometry are original. The workspace's `VIDEO-STYLE-NOTICES.txt` preserves the repository notices and clarifies third-party asset scope.

- [prompts/10-synthwave.md](https://github.com/Vincentwei1021/mg-styles-15/blob/49052d80bfaf9fa8412cc9710530e5e95a3b8d8c/prompts/10-synthwave.md)
- [demos/10-synthwave/index.html](https://github.com/Vincentwei1021/mg-styles-15/blob/49052d80bfaf9fa8412cc9710530e5e95a3b8d8c/demos/10-synthwave/index.html)
