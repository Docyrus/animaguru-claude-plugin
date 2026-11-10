# One-Line Art production recipe

The workspace includes an executable original study in `src/studies/scenes.ts`, selected with `one-line-art`. Its drawing commands are consumed by `src/studies/pixi-renderer.ts`; geometry and time sampling are shared with the gallery renderer. All copy lives in `shared/locales/en/style-studies.json`.

In an untouched starter, run `npm run example -- one-line-art`, then `npm run dev`. The command refuses to replace an authored film, retains starter backups in `production/example-backup/`, and writes an 8-second study with its own resource tracks. `npm run export:html` and `npm run export:mp4` use this installed film normally. To use the recipe inside an existing film, import `studyFrame()` and `StudyRenderer`, then compose the selected scene into the project's timeline instead of running the installer.

## Assets and sources

The line is authored, not generated. When the brief supplies a logo or product, trace its outline from the client's own vector file (SVG, AI or PDF exported to SVG) and record the file in `production/CREDITS.md`. Paper or fabric textures for the ground come from CC0 sources (Poly Haven, ambientCG) or are generated in code; fonts must be licensed for video (SIL OFL families such as Cormorant, Playfair Display or Bodoni Moda, or the client's own licensed brand fonts). Invent brand names in examples; never trace a real trademark the user does not own.

## Adaptation decisions

- Store the path once as sampled points with cumulative arc length, the time each point is reached and a role (outline or engraved). Sample curves by distance (about 1.5–2 px) so long curves do not race. `strokePoints()` in `src/studies/timing.ts` truncates a polyline by measured length for simple cases.
- Draw the visible part each frame as a `Graphics` stroke in screen space after applying the camera transform, at a fixed width with round caps and joins, so zooming never thins or thickens the line. Draw the nib as a small additive glow at the interpolated tip.
- Dim older line by its age (time since its point was drawn) rather than by position, and run a highlight along arc length for the closing sheen; both stay pure functions of time.
- Build the fill as a `Graphics` shape of the closed figure, masked by a circle that grows from the closing anchor; add a brushed-metal or ink texture as a `Sprite` inside the same mask. Re-colour engraved line segments where the fill covers them.
- Set the wordmark as live `Text` with letter-spacing that tightens as it fades up, and a hairline rule beneath it.

The study is silent, original procedural art with an invented brand; it demonstrates material, layout and motion. The gallery preview renders the same idea at higher fidelity: a champagne line on a midnight ground passes through a sun on the horizon, a three-arch loggia, a woman's profile and a brand ring that fills with gold before the wordmark. Configure the subject, palette, figure sequence, duration and soundtrack from the brief.

Use `src/studies/timing.ts` for deterministic easing, seeded variation, measured stroke truncation and cue helpers. `window.animaguru.texts` exposes visible study text bounds for `npm run review`; text declarations alone do not count as visual proof. Inspect the actual frames as well.

## Sources and attribution

Inspired by the following pinned references; no source code, assets or fonts are bundled. New study art and scene geometry are original. The workspace's `VIDEO-STYLE-NOTICES.txt` preserves the repository notices and clarifies third-party asset scope.

- [prompts/02-line-art.md](https://github.com/Vincentwei1021/mg-styles-15/blob/49052d80bfaf9fa8412cc9710530e5e95a3b8d8c/prompts/02-line-art.md)
- [demos/02-line-art/film.js](https://github.com/Vincentwei1021/mg-styles-15/blob/49052d80bfaf9fa8412cc9710530e5e95a3b8d8c/demos/02-line-art/film.js)
