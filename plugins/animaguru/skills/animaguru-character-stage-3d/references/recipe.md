# 3D Character Stage production recipe

The workspace includes an executable original study in `src/studies/three/character-stage-3d.ts`, selected with `character-stage-3d`. It is a 3D study: `src/studies/three-film.ts` runs it through the kit's `ThreeStage`, at 1920×1080 scaled to the film. Its copy lives in `shared/locales/en/style-studies.json` under `threeStyles`.

In an untouched starter, run `npm run example -- character-stage-3d`, then `npm run dev`. The command refuses to replace an authored film, retains starter backups in `production/example-backup/`, and writes an 8-second study. `npm run export:html` and `npm run export:mp4` use this installed film normally. To use the recipe inside an existing film, copy the study's camera matching, light and posing into your own scene module and compose it into the project's timeline.

## Sources

- **Painting:** generate one wide image asset (`--type image --aspect-ratio 16:9`) describing the place, the painterly medium, an eye-level view with a stated horizon height, an empty ground where the character will walk, one light direction with its shadows, and "no people, no text". Or use the user's own background art, at least 1920×1080. Note its horizon height, light direction and shadow colour before staging.
- **Character:** generate a reference image (full body, T- or A-pose, arms clear of the body, plain white background, even light, no props) in the painting's look, then a rigged `model` asset from it with the clips the story needs. A design from the user (character sheet, mascot art) can be the reference; follow its proportions and colours.
- Record every prompt, asset ID and job in `production/`.

## Adaptation decisions

- The study's character is a jointed wooden mannequin built from primitives, posed by functions of t (leg swing, knee bend, arm swing, a raised waving arm), so it needs no files. A film replaces it with the generated rigged model posed with `Rig.pose()`: the walk at its measured speed, then idle, gesture and talk clips crossfaded by weight.
- The study's square is drawn with Pixi `Graphics` behind the transparent 3D sprite, with paving joints receding to the same horizon the 3D camera uses, so you can see the ground plane and the painting agree. A film uses a painting instead and matches the camera to it the same way: lens shift to the painted horizon, eye height and field of view from painted objects of known size.
- The study's sun is placed back left like its painted sun, so the shadow falls right and toward the camera; place the film's light from the painting, not from a default.
- The gallery preview composes a generated, auto-rigged baker on a generated painted plaza: camera matched to the painting, Meshy's in-place walk moved at the planted foot's speed and played 1.2× faster, walk crossfaded to idle, a one-hand wave and a talk gesture, a warm brown `ShadowMaterial` shadow, ACES tone mapping, a slight warm grade and glow on the figure, and a slow 2D push that follows him.

The study is silent, original procedural art; it demonstrates the camera match, the shadow and the posing, not a finished story. Configure the character, painting, scene sequence, captions, duration and soundtrack from the brief.

Use `src/studies/timing.ts` and the kit's motion helpers for deterministic easing and seeded variation. `window.animaguru.texts` exposes visible study text bounds for `npm run review`; text declarations alone do not count as visual proof. Inspect the actual frames as well.

## Sources and attribution

The study's art, geometry and posing are original. three.js (MIT) is a template dependency. Generated paintings and models are the account's assets; record them like other generated media.
