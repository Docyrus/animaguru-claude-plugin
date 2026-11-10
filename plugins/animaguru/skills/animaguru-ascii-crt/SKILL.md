---
name: animaguru-ascii-crt
description: Build ASCII & CRT visuals and motion in an AnimaGuru PixiJS video workspace. Use when this visual style is chosen for an explainer, advertisement or general video.
disable-model-invocation: true
---

# ASCII & CRT

Real glyph-grid imagery, terminal text and restrained phosphor glow with deliberate typing and screen behavior. Subject, audience, emotional tone and story come from the user's brief. This style supports Explainer, Advertisement and General Video.

## Establish direction

Follow sibling `animaguru-video` for purpose → style → compact interview before new production. Reuse explicit choices and completed briefs; honor a requested interview skip. Share [the style gallery](https://animaguru.com/animation-styles#ascii-crt). Fold missing visual questions into the shared interview:

- Which phosphor hue and balance of text versus imagery fits?
- How much screen aging should be visible?

## Build the look and movement

Read `pixijs` and the relevant Graphics, Text, Container, Assets or Mesh skills. Read `animaguru` before generating assets; discover current models and estimates, respect the user's budget, and reuse completed media. Essential text and exact numerical geometry belong in authored canvas content.

- Build a glyph atlas and choose characters by measured coverage, with blank cells below a threshold. Negative space makes images recognizable.
- Derive afterglow from known earlier cue samples, never a history buffer that changes with playback order. Snap grid content while camera scaling may be smooth.
- Match artifacts to the medium: monochrome phosphor has no RGB grille, and CRT is not VHS tape. Keep required copy readable through the treatment.

Use the [production recipe](references/recipe.md) for the bundled original study and port-specific decisions. It is a technique example, not a prescribed film. Keep motions a function of absolute seconds; separate drawing cadence from camera/light cadence when the material calls for it. Prepare assets locally, preserve async seeking and register actual resource/cue times. Keep essential type editable and localized.

## Review and delivery

Inspect glyph legibility and stable cell placement; cold seeks, afterglow and loop boundary continuity. Check representative full-resolution frames, moving playback, desktop/mobile fit and cold seeks. Follow `animaguru-video` for production records, audio mixing and HTML5 delivery; export MP4 when requested. Describe the actual 2D/2.5D rendering method accurately. Physically rendered 3D remains deferred.
