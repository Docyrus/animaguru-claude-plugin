---
name: animaguru-photo-footage-editorial
description: Build Photo & Footage Editorial visuals and motion in an AnimaGuru PixiJS video workspace. Use when this visual style is chosen for an explainer, advertisement or general video.
disable-model-invocation: true
---

# Photo & Footage Editorial

Purposeful media frames, filmstrips and contact-sheet layouts with selective focus and continuous framing relationships. Subject, audience, emotional tone and story come from the user's brief. This style supports Explainer, Advertisement and General Video.

## Establish direction

Follow sibling `animaguru-video` for purpose → style → compact interview before new production. Reuse explicit choices and completed briefs; honor a requested interview skip. Share [the style gallery](https://animaguru.com/animation-styles#photo-footage-editorial). Fold missing visual questions into the shared interview:

- Which real media is available and what must stay inside each crop?
- Should the edit feel calm, rhythmic or tightly cut?

## Build the look and movement

Read `pixijs` and the relevant Graphics, Text, Container, Assets or Mesh skills. Read `animaguru` before generating assets; discover current models and estimates, respect the user's budget, and reuse completed media. Essential text and exact numerical geometry belong in authored canvas content.

- Use local supplied or generated media and one crop model for thumbnail-to-hero transitions. Important faces, product labels and controls guide crop choices.
- Await decoded video frames before resolving renderFrame. Large image sequences are optional and can make the hosted film slow to load and the submission large.
- Use a timeline trim/source-time contract for footage, not an independent live video clock. The bundled study uses original illustrated cards as stand-ins; replace them with real media for a real-product film.

Use the [production recipe](references/recipe.md) for the bundled original study and port-specific decisions. It is a technique example, not a prescribed film. Keep motions a function of absolute seconds; separate drawing cadence from camera/light cadence when the material calls for it. Prepare assets locally, preserve async seeking and register actual resource/cue times. Keep essential type editable and localized.

## Review and delivery

Inspect crop safety, decoded frame correctness and audio choice; nested-path/iframe playback and total export size. Check representative full-resolution frames, moving playback, desktop/mobile fit and cold seeks. Follow `animaguru-video` for production records, audio mixing and MP4 delivery. Describe the actual 2D/2.5D rendering method accurately. Physically rendered 3D remains deferred.
