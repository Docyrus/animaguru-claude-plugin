# Bauhaus Geometry production recipe

The workspace includes an executable original study in `src/studies/scenes.ts`, selected with `bauhaus-geometry`. Its drawing commands are consumed by `src/studies/pixi-renderer.ts`; geometry and time sampling are shared with the gallery renderer. All copy lives in `shared/locales/en/style-studies.json`.

In an untouched starter, run `npm run example -- bauhaus-geometry`, then `npm run dev`. The command refuses to replace an authored film, retains starter backups in `production/example-backup/`, and writes an 8-second study with its own resource tracks. `npm run export:mp4` uses this installed film normally. To use the recipe inside an existing film, import `studyFrame()` and `StudyRenderer`, then compose the selected scene into the project's timeline instead of running the installer.

## Assets

The style needs no footage or generated imagery: shapes, grid and type are drawn in code. Use fonts licensed for commercial use and bundle them with the film (for example Jost or League Spartan for a Futura-like display face, Barlow Condensed or Oswald for small caps, all under the SIL Open Font License). A paper texture, if used, is procedural or CC0. Record each font and texture in `production/CREDITS.md`. Invent names and copy; do not imitate a real school's, museum's or brand's identity.

## Adaptation decisions

- Keep the grid as data: one module `M`, origin `(X0, Y0)` and `gx(c) = X0 + c * M`, `gy(r) = Y0 + r * M`. Store every element's resting position and size in modules and derive pixels from them, so a layout change never breaks alignment.
- Draw each shape once as `Graphics` (circle, polygon, an `arc` for a quarter disc) inside a `Container` whose `pivot` is the action's pivot: the shape's centre, the vertex it swings about, or the frame centre for a whole-composition turn. Animate only `position` and `rotation` from absolute time; growing bars and rules are a width or a mask derived from time.
- Schedule actions from a cue table in beats (`seconds = beat * 60 / bpm`) and ease with easeInOutQuad (`k < .5 ? 2k² : 1 - (2 - 2k)² / 2`) or linear. Avoid `spring()` from `timing.ts` here: its exponential settle reads organic rather than mechanical, and any initial velocity makes it overshoot.
- For an array wave, start each tile at `beat + column * step + row * step / 2` and keep `step × columns + turn length` inside the beat, so the next cut-in lands on a still frame.
- Printed finish: a paper `Sprite` from a procedural canvas texture under the shapes, each ink colour on its own `Container` offset by a pixel for misregistration, and a light grain overlay. A multiply-style blend keeps overprints honest where colours cross. Registration marks go in every ink layer so the offset is visible.
- Vertical type is a `Text` rotated −90° about its baseline corner; set it to the grid like any shape. Load the fonts before the first frame so seeks never show fallback faces.
- Reserve motion blur for genuinely fast moves (a 180° turn in one beat), using a few sub-steps or a directional blur filter; keep held frames sharp.

The study is silent, original procedural art. It demonstrates the grid, the beat-locked actions, the pivot alternation and the phase-offset array, not a prescribed film. The gallery preview renders the same choreography as a printed poster: separate ink layers on a paper stock, off register by a pixel, finishing on a pull-back to the sheet on a wall. Configure the subject, palette, scene sequence, duration and soundtrack from the brief.

Use `src/studies/timing.ts` for deterministic easing, seeded variation, measured stroke truncation and cue helpers. `window.animaguru.texts` exposes visible study text bounds for `npm run review`; text declarations alone do not count as visual proof. Inspect the actual frames as well.

## Sources and attribution

Inspired by the following pinned references; no source code, assets or audio are bundled. New study art and scene geometry are original. The workspace's `VIDEO-STYLE-NOTICES.txt` preserves the repository notices and clarifies third-party asset scope.

- [prompts/09-bauhaus.md](https://github.com/Vincentwei1021/mg-styles-15/blob/49052d80bfaf9fa8412cc9710530e5e95a3b8d8c/prompts/09-bauhaus.md)
- [demos/09-bauhaus/film.js](https://github.com/Vincentwei1021/mg-styles-15/blob/49052d80bfaf9fa8412cc9710530e5e95a3b8d8c/demos/09-bauhaus/film.js)
