---
name: animaguru-exploded-teardown-3d
description: Build 3D Exploded Teardown visuals and motion in an AnimaGuru video workspace, with a real three.js model whose parts separate along their assembly axes while the camera orbits and leader labels follow each part. Use when this visual style is chosen for an explainer, advertisement or general video.
disable-model-invocation: true
---

# 3D Exploded Teardown

A product in real 3D on a clean studio set: the camera orbits while the parts lift apart along their assembly axes in the order they come off, hold so each one can be read, and close again. Every part keeps a leader label that stays on it through the turn. Subject, audience, emotional tone and story come from the user's brief. This style supports Explainer, Advertisement and General Video.

## Establish direction

Follow sibling `animaguru-video` for purpose → style → compact interview before new production. Reuse explicit choices and completed briefs; honor a requested interview skip. Share [the style gallery](https://animaguru.com/animation-styles#exploded-teardown-3d). Fold missing visual questions into the shared interview:

- Which product, and do you have its CAD (STEP, glTF/GLB, OBJ), scans or a bill of materials? Is it a real product the film makes claims about, or an invented or illustrative one?
- Which parts deserve a label, and which one is the hero the camera should end on?

## Where the parts come from

The parts are the evidence, so their source decides what the film may say.

- **A real product, or any factual claim** (dimensions, materials, capacities, part counts): use the user's own CAD or scans. Convert STEP to GLB offline (for example with FreeCAD or Blender), keep one mesh per part with its real name, and take every on-screen number from the product's files or spec sheet. Keep `production/FACTS.md` (each claim, its source and quoted wording) and `production/CREDITS.md`, and deliver both. Never stand a generated model in for the real product.
- **An invented or illustrative product**: model the parts in code (rounded boxes, bevelled extrusions with real holes, lathed caps, canvas textures for boards and screens) or in Blender, or generate the object with AnimaGuru and split it. `animaguru-3d-models` covers generation; Tripo's part generation and Hunyuan3D's part splitting give separate meshes, but check every split by eye and rebuild parts that come out fused. Say on screen that the product is invented and its specs illustrative, and show no real brand.

## Build the look and movement

Read `animaguru-3d-models` for the kit's `ThreeStage` (load, environment or `room()`, `post`, `draw`, `project`), the asset pipeline and determinism rules, and `pixijs` for the 2D layers. Read `animaguru` before generating assets.

- **Axes and order.** Give each part an assembly axis (usually the stack's normal; screws along their own axes, spinning as they back out), a separation distance and a start time. Fasteners come out first, then parts lift in the order a technician would remove them, staggered by about 0.15–0.2 s with eased travel; close in reverse. Every offset is a function of absolute seconds.
- **Space.** Open gaps wide enough that a part under a larger plate stays visible from the camera's elevation; widen the gaps above hidden parts rather than shrinking the parts. Pull the camera back as the stack opens and push in as it closes. Keep the frame neutral (studio grey or dark plate) so the product is the brightest thing, with one accent colour for indices.
- **Labels that follow.** Project one anchor per part with `stage.project()` every frame, choosing a point on the camera-facing edge so it is never hidden by the part above. Assign each part a fixed side, place labels just outside the stack's projected silhouette, and keep each side's labels at least one label apart in anchor order so leaders never cross. Fade a label in when its part arrives and out before the stack closes. Labels are Pixi Text: index, name and one spec line.
- **Light.** An HDR or `room()` environment plus one shadow-casting key light; a `ShadowMaterial` floor under the floating stack grounds it over a 2D backdrop. Avoid bloom over a transparent stage.

Use the [production recipe](references/recipe.md) for sources, the bundled study and port decisions. Keep essential type editable and localized.

## Review and delivery

Step through the separation frame by frame: each label's dot sits on its own part at every moment of the orbit (never on the part in front of it), no two labels or leaders overlap, nothing passes through anything while parts travel (check screws against their bosses and keys against their holes), the separation reads in order, and the hold is long enough to read every label. Check every number against `FACTS.md` for a real product. Check representative full-resolution frames, moving playback, desktop/mobile fit and cold seeks. Follow `animaguru-video` for production records, audio mixing and HTML5 delivery; export MP4 when requested. Describe the method accurately as real-time 3D rendered with three.js.
