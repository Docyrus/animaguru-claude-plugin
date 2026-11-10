---
name: animaguru-microscope-story
description: Build Microscope Story visuals and motion in an AnimaGuru PixiJS video workspace. Use when this visual style is chosen for an explainer, advertisement or general video.
disable-model-invocation: true
---

# Microscope Story

One continuous dive from a slide on the bench to a single cell, with focus breaths, true scale bars and readings counted from the image. It is an evidence style: real data, imagery or scans carry the film. Subject, audience, emotional tone and story come from the user's brief. This style supports Explainer, Advertisement and General Video.

## Establish direction

Follow sibling `animaguru-video` for purpose → style → compact interview before new production. Reuse explicit choices and completed briefs; honor a requested interview skip. Share [the style gallery](https://animaguru.com/animation-styles#microscope-story). Fold missing visual questions into the shared interview:

- Which specimen, stain or modality, and do you have your own scans (SVS, NDPI, MRXS, or SEM TIFFs with a scale)?
- What should be measured or counted, and should the film end on a cell or climb back out?

## Use real evidence

Ask the user for their own data, scans, files or rights first; otherwise find licence-clean sources (see the [production recipe](references/recipe.md)). Never stand a generated image in for the evidence, and never invent a number. Keep `production/FACTS.md` (each on-screen or spoken claim, its source URL and quoted wording, or the measurement method) and `production/CREDITS.md` (every asset's source, author and licence), and deliver both with the film. CC BY-SA, ODbL, "no known restrictions" or non-commercial terms are not CC0: name them to the user and ask before using them.

## Build the look and movement

Read `pixijs` and the relevant Graphics, Text, Container, Assets, Mesh or Filters skills. Read `animaguru` before generating assets: generation can supply music, narration or a title background, never the evidence itself. Discover current models and estimates, respect the user's budget, and reuse completed media. Essential text and exact numerical geometry belong in authored canvas content.

- The specimen is a real, licence-clean micrograph or whole-slide scan; nothing on it is drawn, retouched or generated, and two different samples never zoom into each other.
- Scale is the camera: one log-space dive through registered pyramid levels, a focus breath at every real objective change and a focal-plane sweep on landing. The scale bar, field of view and magnification come from the file's pixel size.
- Readings are measured: describe what was measured, never diagnose. One accent, away from the stain's hues, marks the counted pixels and the reading.

Use the [production recipe](references/recipe.md) for sources, the bundled original study and port-specific decisions. It is a technique example, not a prescribed film. Keep motions a function of absolute seconds; separate drawing cadence from camera/light cadence when the material calls for it. Prepare assets locally, preserve async seeking and register actual resource/cue times. Keep essential type editable and localized.

## Review and delivery

Inspect upsampling at the deepest level, seams between levels, scale-bar values against the pixel size, counted shares against the mask and raw counts, and frosted panels over stain and glass. Check representative full-resolution frames, moving playback, desktop/mobile fit and cold seeks. Follow `animaguru-video` for production records, audio mixing and MP4 delivery. Describe the actual 2D/2.5D rendering method accurately. Physically rendered 3D remains deferred.
