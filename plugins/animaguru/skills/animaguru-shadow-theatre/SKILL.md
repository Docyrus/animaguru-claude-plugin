---
name: animaguru-shadow-theatre
description: Build Shadow Theatre visuals and motion in an AnimaGuru PixiJS video workspace. Use when this visual style is chosen for an explainer, advertisement or general video.
disable-model-invocation: true
---

# Shadow Theatre

Articulated silhouettes or translucent carved puppets on a lit screen, with distance-driven softness and scale. Subject, audience, emotional tone and story come from the user's brief. This style supports Explainer, Advertisement and General Video.

## Establish direction

Follow sibling `animaguru-video` for purpose → style → compact interview before new production. Reuse explicit choices and completed briefs; honor a requested interview skip. Share [the style gallery](https://animaguru.com/animation-styles#shadow-theatre). Fold missing visual questions into the shared interview:

- Do you prefer opaque silhouettes or translucent colored pieces?
- What screen texture, lamp character and visible joints fit?

## Build the look and movement

Read `pixijs` and the relevant Graphics, Text, Container, Assets or Mesh skills. Read `animaguru` before generating assets; discover current models and estimates, respect the user's budget, and reuse completed media. Essential text and exact numerical geometry belong in authored canvas content.

- Separate carved holes from painted color. Translucent overlaps darken; opaque silhouettes occlude.
- Place pivots at puppet joints and design readable profile poses. Derive scale and blur from the authored distance to the lamp, with a coherent light model.
- Keep cloth texture in screen space and puppet texture in piece space. Folktales, cultural settings and particular instruments are optional brief choices.

Use the [production recipe](references/recipe.md) for the bundled original study and port-specific decisions. It is a technique example, not a prescribed film. Keep motions a function of absolute seconds; separate drawing cadence from camera/light cadence when the material calls for it. Prepare assets locally, preserve async seeking and register actual resource/cue times. Keep essential type editable and localized.

## Review and delivery

Inspect small carved openings at output size; readable profiles, lamp consistency and joint continuity. Check representative full-resolution frames, moving playback, desktop/mobile fit and cold seeks. Follow `animaguru-video` for production records, audio mixing and MP4 delivery. Describe the actual 2D/2.5D rendering method accurately. Physically rendered 3D remains deferred.
