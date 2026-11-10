---
name: animaguru-analog-film-tape
description: Build Analog Film & Tape visuals and motion in an AnimaGuru PixiJS video workspace. Use when this visual style is chosen for an explainer, advertisement or general video.
disable-model-invocation: true
---

# Analog Film & Tape

Projected-film cadence or camcorder texture over original scenes, with controlled weave, exposure and medium-specific transitions. Subject, audience, emotional tone and story come from the user's brief. This style supports Explainer, Advertisement and General Video.

## Establish direction

Follow sibling `animaguru-video` for purpose → style → compact interview before new production. Reuse explicit choices and completed briefs; honor a requested interview skip. Share [the style gallery](https://animaguru.com/animation-styles#analog-film-tape). Fold missing visual questions into the shared interview:

- Do you want projected film or camcorder tape, and which intensity?
- What frame shape, overlays or intertitles should be used?

## Build the look and movement

Read `pixijs` and the relevant Graphics, Text, Container, Assets or Mesh skills. Read `animaguru` before generating assets; discover current models and estimates, respect the user's budget, and reuse completed media. Essential text and exact numerical geometry belong in authored canvas content.

- Select film or tape, then keep its artifacts coherent. Film can use gate weave, shutter/flicker and scratches; tape uses luma/chroma distortion, tracking and optional OSD.
- Compute every artifact from absolute time and fixed seeds. Sampling subject motion and adding output-frame damage are separate clocks.
- Moderate effects over essential text. The source examples do not require horror, empty corridors, slapstick, a pianist or a particular period story.

Use the [production recipe](references/recipe.md) for the bundled original study and port-specific decisions. It is a technique example, not a prescribed film. Keep motions a function of absolute seconds; separate drawing cadence from camera/light cadence when the material calls for it. Prepare assets locally, preserve async seeking and register actual resource/cue times. Keep essential type editable and localized.

## Review and delivery

Inspect text readability and accidental blank frames; replay stability and correct medium-specific artifacts. Check representative full-resolution frames, moving playback, desktop/mobile fit and cold seeks. Follow `animaguru-video` for production records, audio mixing and HTML5 delivery; export MP4 when requested. Describe the actual 2D/2.5D rendering method accurately. Physically rendered 3D remains deferred.
