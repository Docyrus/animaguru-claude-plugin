---
name: animaguru-lidar-survey
description: Build LiDAR Survey visuals and motion in an AnimaGuru PixiJS video workspace. Use when this visual style is chosen for an explainer, advertisement or general video.
disable-model-invocation: true
---

# LiDAR Survey

Measured point clouds flown through in the dark, peeled by a cutting plane and condensed into a raking-lit surface with traced features. It is an evidence style: real data, imagery or scans carry the film. Subject, audience, emotional tone and story come from the user's brief. This style supports Explainer, Advertisement and General Video.

## Establish direction

Follow sibling `animaguru-video` for purpose → style → compact interview before new production. Reuse explicit choices and completed briefs; honor a requested interview skip. Share [the style gallery](https://animaguru.com/animation-styles#lidar-survey). Fold missing visual questions into the shared interview:

- Which place and dataset (or the user's own scan), and which feature should the survey reveal?
- Which classes should be peeled or kept, and which one reading should land?

## Use real evidence

Ask the user for their own data, scans, files or rights first; otherwise find licence-clean sources (see the [production recipe](references/recipe.md)). Never stand a generated image in for the evidence, and never invent a number. Keep `production/FACTS.md` (each on-screen or spoken claim, its source URL and quoted wording, or the measurement method) and `production/CREDITS.md` (every asset's source, author and licence), and deliver both with the film. CC BY-SA, ODbL, "no known restrictions" or non-commercial terms are not CC0: name them to the user and ask before using them.

## Build the look and movement

Read `pixijs` and the relevant Graphics, Text, Container, Assets, Mesh or Filters skills. Read `animaguru` before generating assets: generation can supply music, narration or a title background, never the evidence itself. Discover current models and estimates, respect the user's budget, and reuse completed media. Essential text and exact numerical geometry belong in authored canvas content.

- Every point is a real return at its measured position: colour by height above ground or by class, value by intensity, never moved into a shape. Points appear behind a front or by height, never by a random fade.
- Peel with a cutting plane by height above ground, then condense the remaining ground into a raking-lit surface. Exaggerate micro relief only with an on-screen note, and measure on undistorted data.
- Keep the background near black, fronts a cool near-white and one amber accent for traced features and the reading. Traced features are interpretation: say "traced".

Use the [production recipe](references/recipe.md) for sources, the bundled original study and port-specific decisions. It is a technique example, not a prescribed film. Keep motions a function of absolute seconds; separate drawing cadence from camera/light cadence when the material calls for it. Prepare assets locally, preserve async seeking and register actual resource/cue times. Keep essential type editable and localized.

## Review and delivery

Inspect point sizes and fog at distance, registration between points and surface at the front, the exaggeration note, privacy cropping and the reading against `FACTS.md`. Check representative full-resolution frames, moving playback, desktop/mobile fit and cold seeks. Follow `animaguru-video` for production records, audio mixing and HTML5 delivery; export MP4 when requested. Describe the actual 2D/2.5D rendering method accurately. Physically rendered 3D remains deferred.
