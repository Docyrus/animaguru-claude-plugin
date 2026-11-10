# 3D Product Turntable production recipe

The workspace includes an executable original 3D study in `src/studies/three/product-turntable-3d.ts`, selected with `product-turntable-3d`. It renders through `src/studies/three-film.ts` and the kit's `ThreeStage` (three.js drawn as one Pixi Sprite, with Pixi text and leaders on top). Its copy lives in `shared/locales/en/style-studies.json` under `threeStyles`.

In an untouched starter, run `npm run example -- product-turntable-3d`, then `npm run dev`. The command refuses to replace an authored film, retains starter backups in `production/example-backup/`, and writes an 8-second study. `npm run export:html` and `npm run export:mp4` use this installed film normally. To use the recipe inside an existing film, copy the study's stage, set and camera code into a scene module and draw it from the film's own update.

## Sources

- **The product.** The user's CAD, GLB or scan comes first. Otherwise generate a `model` asset from their product photo, or from a clean reference image drawn for the purpose (see `animaguru-3d-models`): Idol's Gaussian splats (`--model idol`) keep the photo's exact look, a Tripo or Hunyuan3D mesh takes the scene's light. Splats are drawn with `stage.splat()` and `return stage.draw(…)`, need a `softShadow()` instead of a cast shadow, and their focus and callouts work like a mesh's. A generated model of a real product is an illustration of it: never invent specifications, materials, certifications or claims for a real product. Callouts name only what the user approved or what is plainly visible. For an invented product, say so on screen (an eyebrow such as "Invented product · generated with AnimaGuru") and invent a brand that is clearly fictional.
- **Lighting.** Studio HDRs from [Poly Haven](https://polyhaven.com/hdris/studio) are CC0 (`studio_small_09` lit the gallery preview). `ThreeStage.room()` gives a neutral studio with no file at all.
- **Records.** Keep each generation's request, job and cost in `production/`, and every asset's source and licence in `production/CREDITS.md`.

## Adaptation decisions

- One product group turns at a constant rate. The camera is a spherical offset (azimuth, elevation, distance) from a target that eases from a macro point on one part to the product's centre, keyframed with `vecAt()`. For the closing lockup, slide camera and target along the camera's right vector so the product sits on a third and the type gets clear space.
- Rack focus: keep a list of focus stops (part, start time) and lerp the focus point between their world positions; the depth-of-field pass's `focus` uniform is the camera's distance to that point, and its `aperture` closes as the camera pulls back.
- Callout anchors are points in the model's normalised space, transformed with `product.localToWorld()` and `stage.project()` every frame. Each callout has an appearance window that matches when its part faces the camera, a preferred side and a rise; measure the label and flip sides when it would leave the frame.
- Correct materials in the shader rather than in the copy: a band of mid metalness to matte graphite, a little extra roughness on polished aluminium so highlights spread into a brushed sheen.
- A soft contact shadow is a transparent radial-gradient plane just above the plinth, parented to the product so it turns with it.

The study is silent, original procedural art: a lathe-turned product with a polished band and a dark cap built in code, lit by `stage.room()`, with a macro, an orbit and push-in, rack focus and a callout pinned to the band's front through the turn. It demonstrates staging, focus and anchoring, not a real product. Replace it with the supplied or generated model and configure the subject, palette, shot sequence, duration and soundtrack from the brief.

`window.animaguru.texts` exposes visible study text bounds for `npm run review`; text declarations alone do not count as visual proof. Inspect the actual frames as well.

## Sources and attribution

Original to AnimaGuru. Study geometry and art are generated in code; the gallery preview uses headphones generated with Tripo H3.1 (the generator AnimaGuru's `model` assets use) and Poly Haven's CC0 `studio_small_09` HDR.
