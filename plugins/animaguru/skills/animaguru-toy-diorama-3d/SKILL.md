---
name: animaguru-toy-diorama-3d
description: Build 3D Toy Diorama visuals and motion in an AnimaGuru video workspace, a miniature world in real 3D rendered with three.js through the kit's ThreeStage. Use when this visual style is chosen for an explainer, advertisement or general video.
disable-model-invocation: true
---

# 3D Toy Diorama

A miniature world on a tabletop, built in real 3D: toy-scale props on a round base, little vehicles and figures running their loops, a free camera gliding over it, and a tilt-shift band that keeps one thin strip in focus so the whole place reads as small. Subject, audience, emotional tone and story come from the user's brief. This style supports Explainer, Advertisement and General Video.

## Establish direction

Follow sibling `animaguru-video` for purpose → style → compact interview before new production. Reuse explicit choices and completed briefs; honor a requested interview skip. Share [the style gallery](https://animaguru.com/animation-styles#toy-diorama-3d). Fold missing visual questions into the shared interview:

- Which place or system should the miniature show, and which few things move in it (cars, boats, trains, people, a machine)?
- Which toy material: painted wood, glossy plastic, felt and card, or clay?

## Build the look and movement

Read sibling `animaguru-3d-models` first: it covers model generation, costs, optimisation and the kit's `ThreeStage`, `normalize()`, `project()` and `stage.post()`. Read `pixijs` for the type drawn over the stage, and `animaguru` before generating assets; discover current models and estimates, respect the user's budget, and reuse completed media. Essential text belongs in authored Pixi Text, never in a texture.

- Build the world from several generated props on a base built in code. Draw one concept image per prop with a shared style suffix (the same material, paint and light words, a plain white background, a three-quarter view), then build each with `assets generate --type model --reference SHA --faces 20000` to `40000`. Optimise every GLB. Saved models face +Z, but check each toy once in a front, side and top render and keep a per-prop yaw table: a long toy can come out at an angle. Scale each prop to its own toy height and stand it on the surface it belongs on, never floating or sunk.
- Build the base, land, water, roads and paths in code: land extruded from a `THREE.Shape` with the shoreline as one edge, a resin-like water disc with a slowly offset tiling normal map, flat ribbons along curves for roads and quays. Peg people, lamps, crates and buoys are cheap procedural toys that add life between the generated pieces.
- Moving props follow `THREE.CatmullRomCurve3` paths, closed for loops, sampled with `getPointAt(u)` where u is a function of film seconds. Face them along the path with `rotation.y = Math.atan2(tangent.x, tangent.z)` from `getTangentAt(u)`. Bob boats with small sines. Keep speeds toy-slow, phase each loop so the thing the viewer should notice is in view, and keep every path on its road or water and clear of buildings.
- Tilt-shift is a screen-space band blur passed to `stage.post(scene, camera, { passes })`: a separable shader (a horizontal then a vertical `ShaderPass`) whose radius grows with distance from a band centre, or three's `HorizontalTiltShiftShader` and `VerticalTiltShiftShader` for a simpler version. Set the band centre each frame from `stage.project()` of the point the camera looks at, so the focus stays on the subject rather than a fixed stripe. Keep the band narrow (5–8% of the frame height) with a soft falloff. A `BokehPass` gives physical depth of field when the camera comes down low.
- Light and grade at toy scale: a warm, low key light whose soft shadow covers the whole base (one 2048–4096 map), a cool sky fill, `stage.room()` for lacquer reflections, a little extra saturation and warmth in a grade pass, and a dark vignette. Render an opaque background (a table plane fading into fog), so post effects never glow against transparency.
- The camera is a high, slow crane or glide, 25–45° down and far enough out to show the base's edge and the table for scale, with one eased function of t moving it along a CatmullRom path and another moving its look target. Hold one continuous glide per shot. The elevated angle and the narrow focus are what sell the miniature.

Use the [production recipe](references/recipe.md) for sources, the bundled original study and port-specific decisions. It is a technique example, not a prescribed film. Keep motions a function of absolute seconds; separate activity speed from camera movement when the material calls for time-lapse. Prepare assets locally, preserve async seeking and register actual resource/cue times. Keep essential type editable and localized.

## Review and delivery

Inspect every prop sitting on its surface (no floating, sinking or interpenetration), vehicles on the road and boats in the water through their whole loops, coherent scale between props, the focus band on the subject at every moment, blur that grows smoothly without ghosting or tiling glints, motion that reads at thumbnail size, and type that stays readable over the brightest part of the scene. Check representative full-resolution frames, moving playback, desktop/mobile fit and cold seeks. Follow `animaguru-video` for production records, audio mixing and HTML5 delivery; export MP4 when requested. Describe the rendering accurately: real-time three.js 3D with generated or supplied toy models.
