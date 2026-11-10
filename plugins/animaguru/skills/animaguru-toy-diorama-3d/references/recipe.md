# 3D Toy Diorama production recipe

The workspace includes an executable original study in `src/studies/three/toy-diorama-3d.ts`, selected with `toy-diorama-3d`. It renders with three.js through the kit's `ThreeStage` and draws its type with Pixi on top; `src/studies/three-film.ts` runs it as an 8-second film. All copy lives in `shared/locales/en/style-studies.json` under `threeStyles`.

In an untouched starter, run `npm run example -- toy-diorama-3d`, then `npm run dev`. The command refuses to replace an authored film, retains starter backups in `production/example-backup/`, and writes an 8-second study with its own resource tracks. `npm run export:html` and `npm run export:mp4` use this installed film normally. To use the recipe inside an existing film, copy the study's helpers (the extruded land, the road ribbon, the tilt-shift pass) into a scene module and call them from `build()`.

## Sources

- Props: generate them with AnimaGuru (`animaguru assets generate PROJECT_ID --type model --reference SHA`), each from a concept image drawn with one shared style suffix so the set matches. The gallery preview used eleven painted-wood toys (terraced houses, a café, a clock tower, a lighthouse, a dock crane, a car, a van, a fishing boat, a sailboat and two kinds of tree), each a GPT Image 2.5 concept image and a Tripo H3.1 model, about $0.32 a prop, optimised to 120–520 KB with meshopt and WebP textures.
- The user's own GLB models, or CC0 low-poly packs, fit too; check each licence and record every asset in `production/CREDITS.md`.
- Lighting needs no file: `stage.room()` lights lacquered toys well. A CC0 studio HDR (Poly Haven) adds richer reflections.

## Adaptation decisions

- Keep one layout table: each prop's model, toy height, yaw and position, then one path per moving thing and one path each for the camera and its look target. Clone repeated props with `model.clone(true)` instead of loading them twice; mirror a clone (`scale.x *= -1`) for variety.
- The study's tilt-shift pass takes `center`, `band`, `falloff` and `amount`. `amount` is in pixels of the supersampled render, so scale it with the stage's size; 20–30 at 1920×1080 with 1.5× supersampling reads as a strong miniature.
- Ten to fifteen generated props at 20,000–40,000 faces with 1K–2K WebP textures, one 4096 shadow map and the two blur passes render well above real time on a laptop GPU.
- Extruded shapes with a bevel grow by the bevel on both faces: measure the bounding box and set the top to the exact surface height, or roads and paths drawn on it disappear underneath.

The study is silent, original procedural art: block houses, a clock tower, a lighthouse, lollipop trees, two cars and two boats built from three.js primitives on a base, bay, road and quay drawn in code. It demonstrates layout, paths, the focus band and the glide; replace its blocks with generated or supplied toy models for production. The gallery preview is a toy harbour town of AnimaGuru-generated models on a base built in code, labelled as such. Configure an original subject, palette, scene sequence, duration and soundtrack from the brief.

`window.animaguru.texts` exposes visible study text bounds for `npm run review`; text declarations alone do not count as visual proof. Inspect the actual frames as well.

## Sources and attribution

The study, its geometry and the gallery preview are original. The 2.5D sibling style, `animaguru-miniature-diorama`, keeps its own pinned references.
