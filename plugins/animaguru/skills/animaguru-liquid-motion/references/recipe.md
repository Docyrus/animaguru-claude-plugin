# Liquid Motion production recipe

The workspace includes an executable original study in `src/studies/scenes.ts`, selected with `liquid-motion`. Its drawing commands are consumed by `src/studies/pixi-renderer.ts`; geometry and time sampling are shared with the gallery renderer. All copy lives in `shared/locales/en/style-studies.json`.

In an untouched starter, run `npm run example -- liquid-motion`, then `npm run dev`. The command refuses to replace an authored film, retains starter backups in `production/example-backup/`, and writes an 8-second study with its own resource tracks. `npm run export:mp4` uses this installed film normally. To use the recipe inside an existing film, import `studyFrame()` and `StudyRenderer`, then compose the selected scene into the project's timeline instead of running the installer.

## Adaptation decisions

- Render the liquid with one custom `Filter` or `Mesh` shader that receives the drops, necks and wave fronts as uniforms (centres, radii, capsule ends, front offsets per bulge) and evaluates a smooth-minimum distance field per pixel. Lettering or logos join the field as a distance texture: rasterize the type once to a canvas, run a distance transform, round it with a small closing and opening, and upload it as a texture. Morph a mark by interpolating distances (drop → pill → letters), never by cross-fading sprites.
- Shade inside the same shader: derive the edge bead's normal from the field gradient and a quarter-circle height profile, reflect a softbox and a strip light, add a sharp key highlight and a Fresnel rim, and blend colours by each primitive's distance so merged zones stay crisp. Draw drop shadows as a blurred, offset copy of the coverage under each layer.
- Without custom shaders, use the gooey route: draw circles and capsules into a `Container`, apply a `BlurFilter` of about 20 px and an alpha-threshold `ColorMatrixFilter`, then add `Graphics` highlights along the top-left edges. It reads flatter; keep its colours few and its highlights consistent.
- Build wave fronts per row (or per sample along the edge) from an eased sweep, a lean, a running ripple and 3–5 bulges with their own phases; spawn spray droplets at the bulge tips. Layer two fronts to swap scenes, and swap the background only once the second front has covered every row.
- Drive necks, snaps, rebounds and late droplets from closed-form functions of time (eased paths, damped cosines, ballistic arcs), so any frame can be sought cold.

The study is silent, original procedural art. It demonstrates material, transforms and layout rather than proving real product claims. The gallery preview is drawn entirely in code for an invented brand; replace its wordmark, palette and copy with the brief's. Configure an original subject, palette, scene sequence, duration and soundtrack from the brief. Liquid sound design (pours, gloops, splashes, drips) lands on the same cues as the visuals.

Use `src/studies/timing.ts` for deterministic easing, seeded variation, measured stroke truncation and cue helpers. `window.animaguru.texts` exposes visible study text bounds for `npm run review`; text declarations alone do not count as visual proof. Inspect the actual frames as well.

## Sources and attribution

Inspired by the following pinned references; no source code, meshes, samples or media are bundled. New study art and scene geometry are original. The workspace's `VIDEO-STYLE-NOTICES.txt` preserves the repository notices and clarifies third-party asset scope.

- [prompts/07-liquid.md](https://github.com/Vincentwei1021/mg-styles-15/blob/49052d80bfaf9fa8412cc9710530e5e95a3b8d8c/prompts/07-liquid.md)
- [demos/07-liquid/js/scene.js](https://github.com/Vincentwei1021/mg-styles-15/blob/49052d80bfaf9fa8412cc9710530e5e95a3b8d8c/demos/07-liquid/js/scene.js)
