---
name: animaguru-product-turntable-3d
description: "Build 3D Product Turntable visuals and motion in an AnimaGuru video workspace: a real three.js product model turning on a studio set with HDR reflections, an orbiting push-in camera, rack focus and callouts pinned to its parts. Use when this visual style is chosen for an explainer, advertisement or general video."
disable-model-invocation: true
---

# 3D Product Turntable

A real 3D product turns on a plinth in a controlled studio while the camera orbits and pushes in, studio light slides across its materials, focus racks from part to part and callouts stay pinned to the parts they name. Subject, audience, emotional tone and story come from the user's brief. This style supports Explainer, Advertisement and General Video.

## Establish direction

Follow sibling `animaguru-video` for purpose → style → compact interview before new production. Reuse explicit choices and completed briefs; honor a requested interview skip. Share [the style gallery](https://animaguru.com/animation-styles#product-turntable-3d). Fold missing visual questions into the shared interview:

- Do you have product photos (front, three-quarter, back) or a CAD/GLB file, and which details and materials should the film show?
- Which callouts may name parts or materials, and which claims, specs or wording are approved?

## Build the model and the set

Read sibling `animaguru-3d-models` before generating anything: it covers the `model` asset type, costs, optimisation and the kit's `ThreeStage`. Read `animaguru` for credits and jobs, and `pixijs` for the Text and Graphics layers.

- Use the user's own CAD or GLB when there is one. Otherwise build from their best product photo, or from a clean reference image you draw first (plain white background, the whole product in frame, three-quarter view). For the photo's exact look (glass, liquids, labels, fabric), make photoreal Gaussian splats with `assets generate --type model --model idol --reference SHA`: they keep the photo's light, so the set's light must agree with it, and the side the photo hid is softer, so keep the turn to about three-quarters and open on the photo's own view with `photoView()`. For a mesh the scene lights, use `assets generate --type model --reference SHA` (Tripo for clean shells and 2K PBR textures, Hunyuan3D 3.1 Pro with `--faces` for fine surface detail) and optimise to about 100–200k triangles with 2K WebP textures before staging.
- Look at a turnaround (front, side, back) before staging. Generated texture atlases sometimes give painted surfaces half metalness, which reads as chrome: correct a material in the shader (for example a `metalnessFactor` band in `onBeforeCompile`) rather than misdescribe it in a callout.
- Light meshes with an HDR studio environment (`stage.environment(...)`, a CC0 studio from Poly Haven, or `stage.room()`) plus one shadow-casting key spot and a warm rim. Rotate `scene.environmentRotation` with time so reflections slide across metal, and choose its offset so polished parts don't mirror a softbox flat white in the macro shot. A thin `RectAreaLight` crossing in front adds a moving strip highlight.
- Build a seamless set: an inside-out sphere with a vertical gradient that ignores fog, a floor that fades into it through matching fog, and a plinth (dark stone or matte resin) with a soft contact shadow under the product. Keep the background opaque when using bloom.

## Build the movement

- Turn the product at a constant rate (a turntable, about 10° a second) and orbit the camera gently against it, so the parts come round on their beats. Open on a macro, pull back to the whole product, and finish on a slow push-in or a lockup with the product moved to a third.
- Rack focus with `stage.post(scene, camera, { bokeh })`: each frame, set the returned pass's `uniforms.focus.value` to the camera's distance from the part being named, easing from part to part. Open the aperture for the macro and close it for wide shots.
- Callouts are Pixi or canvas text with a dot, an elbow and a leader line, anchored with `stage.project(product.localToWorld(point), camera)` each frame. Pick anchor points by drawing candidate dots over a few rendered frames. Show each callout only while its part faces the camera, flip a label to the side with room, and never let one leave the frame.
- Every value is a function of film time: no `THREE.Clock`, no `mixer.update(delta)`, no unseeded randomness. Draw last, from the update registered after every 3D update.

Use the [production recipe](references/recipe.md) for sources, the bundled original study and port-specific decisions. It is a technique example, not a prescribed film. Prepare assets locally, preserve async seeking and register actual resource/cue times. Keep essential type editable and localized.

## Review and delivery

Inspect every callout on its part through the whole orbit (anchor on the right surface, label inside the frame and clear of the product), focus landing on the named part, metal that shows its finish rather than blowing out to white, leather and plastics that read as their materials, the contact shadow, the floor's horizon (no visible seam), texture sharpness at the closest framing, and the lockup's clearance from the product. Check representative full-resolution frames, moving playback, desktop/mobile fit and cold seeks. Follow `animaguru-video` for production records, audio mixing and HTML5 delivery; export MP4 when requested. Say that the product is a generated or supplied 3D model rendered in three.js, and label invented products and brands as such.
