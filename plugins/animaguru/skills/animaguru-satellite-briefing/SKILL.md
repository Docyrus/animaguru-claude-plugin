---
name: animaguru-satellite-briefing
description: Build Satellite Briefing visuals and motion in an AnimaGuru PixiJS video workspace. Use when this visual style is chosen for an explainer, advertisement or general video.
disable-model-invocation: true
---

# Satellite Briefing

Satellite imagery graded to an analyst's grey, with thin measured hairlines, dated passes and one reading per screen in one continuous zoom. It is an evidence style: real data, imagery or scans carry the film. Subject, audience, emotional tone and story come from the user's brief. This style supports Explainer, Advertisement and General Video.

## Establish direction

Follow sibling `animaguru-video` for purpose → style → compact interview before new production. Reuse explicit choices and completed briefs; honor a requested interview skip. Share [the style gallery](https://animaguru.com/animation-styles#satellite-briefing). Fold missing visual questions into the shared interview:

- Which place, dates and claim should the imagery test, and do you have your own survey or GIS layers?
- Where should true colour return, and which single reading matters most?

## Use real evidence

Ask the user for their own data, scans, files or rights first; otherwise find licence-clean sources (see the [production recipe](references/recipe.md)). Never stand a generated image in for the evidence, and never invent a number. Keep `production/FACTS.md` (each on-screen or spoken claim, its source URL and quoted wording, or the measurement method) and `production/CREDITS.md` (every asset's source, author and licence), and deliver both with the film. CC BY-SA, ODbL, "no known restrictions" or non-commercial terms are not CC0: name them to the user and ask before using them.

## Build the look and movement

Read `pixijs` and the relevant Graphics, Text, Container, Assets, Mesh or Filters skills. Read `animaguru` before generating assets: generation can supply music, narration or a title background, never the evidence itself. Discover current models and estimates, respect the user's budget, and reuse completed media. Essential text and exact numerical geometry belong in authored canvas content.

- Use licence-clean, georeferenced imagery of the real place or the user's own layers; the ground is a photograph, the hairlines are what the analyst measured.
- Stack plates by resolution in one world frame and zoom in log space; grade the analysis layer to a cool grey with a shoulder so white stays reserved for marks and the accent for the one reading.
- Draw outlines, range lines and reticles through the same ground-to-screen function as the imagery; time changes are scan passes, never dissolves, and readings count up and land.

Use the [production recipe](references/recipe.md) for sources, the bundled original study and port-specific decisions. It is a technique example, not a prescribed film. Keep motions a function of absolute seconds; separate drawing cadence from camera/light cadence when the material calls for it. Prepare assets locally, preserve async seeking and register actual resource/cue times. Keep essential type editable and localized.

## Review and delivery

Inspect plate seams and upsampling at each altitude, grey-grade clipping, mark registration through every camera move, the burned-in imagery credit and every number against `FACTS.md`. Check representative full-resolution frames, moving playback, desktop/mobile fit and cold seeks. Follow `animaguru-video` for production records, audio mixing and HTML5 delivery; export MP4 when requested. Describe the actual 2D/2.5D rendering method accurately. Physically rendered 3D remains deferred.
