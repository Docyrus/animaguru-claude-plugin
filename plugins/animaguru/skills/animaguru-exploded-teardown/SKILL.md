---
name: animaguru-exploded-teardown
description: Build Exploded Teardown visuals and motion in an AnimaGuru PixiJS video workspace. Use when this visual style is chosen for an explainer, advertisement or general video.
disable-model-invocation: true
---

# Exploded Teardown

A product taken apart on one axis under studio light, every part named with the numbers in its own files, then closed and dimensioned. It is an evidence style: real data, imagery or scans carry the film. Subject, audience, emotional tone and story come from the user's brief. This style supports Explainer, Advertisement and General Video.

## Establish direction

Follow sibling `animaguru-video` for purpose → style → compact interview before new production. Reuse explicit choices and completed briefs; honor a requested interview skip. Share [the style gallery](https://animaguru.com/animation-styles#exploded-teardown). Fold missing visual questions into the shared interview:

- Which product and revision, and do you have its CAD, PCB layout, bill of materials and spec sheet?
- Which parts deserve a stop, and which real motion or light should it perform?

## Use real evidence

Ask the user for their own data, scans, files or rights first; otherwise find licence-clean sources (see the [production recipe](references/recipe.md)). Never stand a generated image in for the evidence, and never invent a number. Keep `production/FACTS.md` (each on-screen or spoken claim, its source URL and quoted wording, or the measurement method) and `production/CREDITS.md` (every asset's source, author and licence), and deliver both with the film. CC BY-SA, ODbL, "no known restrictions" or non-commercial terms are not CC0: name them to the user and ask before using them.

## Build the look and movement

Read `pixijs` and the relevant Graphics, Text, Container, Assets, Mesh or Filters skills. Read `animaguru` before generating assets: generation can supply music, narration or a title background, never the evidence itself. Discover current models and estimates, respect the user's budget, and reuse completed media. Essential text and exact numerical geometry belong in authored canvas content.

- Geometry, positions and counts come from the product's own files. Without files, build only from published dimensions, say that it is a model, and show no number you could not source.
- Separate layers on one axis, top first, with even gaps and a long settle; repeated parts lift in a wave. Labels sit in a fixed column (index, name, one spec line); close bottom first and draw dimensions in the object's own perspective.
- Keep the frame dark and neutral so the product is the brightest thing, use one accent for measured lines and indices, and show plain package tops instead of brand marks.

Use the [production recipe](references/recipe.md) for sources, the bundled original study and port-specific decisions. It is a technique example, not a prescribed film. Keep motions a function of absolute seconds; separate drawing cadence from camera/light cadence when the material calls for it. Prepare assets locally, preserve async seeking and register actual resource/cue times. Keep essential type editable and localized.

## Review and delivery

Inspect label reading time at each stop, leader anchors through the orbit, revision consistency between files, dark plastics against the ground and every number against `FACTS.md`. Check representative full-resolution frames, moving playback, desktop/mobile fit and cold seeks. Follow `animaguru-video` for production records, audio mixing and HTML5 delivery; export MP4 when requested. Describe the actual 2D/2.5D rendering method accurately. Physically rendered 3D remains deferred.
