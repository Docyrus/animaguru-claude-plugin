---
name: animaguru-risograph-print
description: Build Risograph Print visuals and motion in an AnimaGuru PixiJS video workspace. Use when this visual style is chosen for an explainer, advertisement or general video.
disable-model-invocation: true
---

# Risograph Print

Porous paper, limited spot inks and colored overprints with deliberate registration and plate reveals. Subject, audience, emotional tone and story come from the user's brief. This style supports Explainer, Advertisement and General Video.

## Establish direction

Follow sibling `animaguru-video` for purpose → style → compact interview before new production. Reuse explicit choices and completed briefs; honor a requested interview skip. Share [the style gallery](https://animaguru.com/animation-styles#risograph-print). Fold missing visual questions into the shared interview:

- How many inks and which brand hues fit the print?
- How rough should the material and registration feel?

## Build the look and movement

Read `pixijs` and the relevant Graphics, Text, Container, Assets or Mesh skills. Read `animaguru` before generating assets; discover current models and estimates, respect the user's budget, and reuse completed media. Essential text and exact numerical geometry belong in authored canvas content.

- Store ink coverage separately from paper knockouts. Overprinted inks combine; opaque paper removes underlying ink.
- Fix registration offsets per shot, with time-based accent kicks that settle; random offsets every frame flicker and bloat exports.
- Keep grain in the plate or paper coordinate system. Halftone spacing must remain readable at the smallest delivery size.

Use the [production recipe](references/recipe.md) for the bundled original study and port-specific decisions. It is a technique example, not a prescribed film. Keep motions a function of absolute seconds; separate drawing cadence from camera/light cadence when the material calls for it. Prepare assets locally, preserve async seeking and register actual resource/cue times. Keep essential type editable and localized.

## Review and delivery

Inspect overprint color and knockout holes; halftone shimmer, registration settling and deterministic grain. Check representative full-resolution frames, moving playback, desktop/mobile fit and cold seeks. Follow `animaguru-video` for production records, audio mixing and HTML5 delivery; export MP4 when requested. Describe the actual 2D/2.5D rendering method accurately. Physically rendered 3D remains deferred.
