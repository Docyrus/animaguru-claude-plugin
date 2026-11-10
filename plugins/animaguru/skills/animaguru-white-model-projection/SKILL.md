---
name: animaguru-white-model-projection
description: Build White Model Projection visuals and motion in an AnimaGuru PixiJS video workspace. Use when this visual style is chosen for an explainer, advertisement or general video.
disable-model-invocation: true
---

# White Model Projection

A white massing model in a dark room, where projected light paints data onto the buildings one layer at a time. It is an evidence style: real data, imagery or scans carry the film. Subject, audience, emotional tone and story come from the user's brief. This style supports Explainer, Advertisement and General Video.

## Establish direction

Follow sibling `animaguru-video` for purpose → style → compact interview before new production. Reuse explicit choices and completed briefs; honor a requested interview skip. Share [the style gallery](https://animaguru.com/animation-styles#white-model-projection). Fold missing visual questions into the shared interview:

- Which place, scale and layers (age, height, zoning, sun), and do you have the place's own building data?
- Which building or set should be picked out at the end?

## Use real evidence

Ask the user for their own data, scans, files or rights first; otherwise find licence-clean sources (see the [production recipe](references/recipe.md)). Never stand a generated image in for the evidence, and never invent a number. Keep `production/FACTS.md` (each on-screen or spoken claim, its source URL and quoted wording, or the measurement method) and `production/CREDITS.md` (every asset's source, author and licence), and deliver both with the film. CC BY-SA, ODbL, "no known restrictions" or non-commercial terms are not CC0: name them to the user and ask before using them.

## Build the look and movement

Read `pixijs` and the relevant Graphics, Text, Container, Assets, Mesh or Filters skills. Read `animaguru` before generating assets: generation can supply music, narration or a title background, never the evidence itself. Discover current models and estimates, respect the user's budget, and reuse completed media. Essential text and exact numerical geometry belong in authored canvas content.

- The model is real geometry from open data or the user's plans, extruded at a stated scale. It is never coloured in the material: data arrives as projected light that brightens surfaces facing the projector and stops at the edge of the throw.
- Bring one layer at a time, each with its own gesture of light: buildings switching on by decade, a level climbing every facade, a real sun's shadows. House lights cut fast and return slowly.
- Every number comes from the same buildings that are on the table. Readouts sit in the left third, pins rise from roofs, and each layer uses one hue family.

Use the [production recipe](references/recipe.md) for sources, the bundled original study and port-specific decisions. It is a technique example, not a prescribed film. Keep motions a function of absolute seconds; separate drawing cadence from camera/light cadence when the material calls for it. Prepare assets locally, preserve async seeking and register actual resource/cue times. Keep essential type editable and localized.

## Review and delivery

Inspect that colour lands only on lit white surfaces, readout legibility over the model, pin anchors through the camera move, and every number against the data file. Check representative full-resolution frames, moving playback, desktop/mobile fit and cold seeks. Follow `animaguru-video` for production records, audio mixing and MP4 delivery. Describe the actual 2D/2.5D rendering method accurately. Physically rendered 3D remains deferred.
