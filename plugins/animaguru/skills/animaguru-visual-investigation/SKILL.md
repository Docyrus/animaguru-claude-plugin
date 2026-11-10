---
name: animaguru-visual-investigation
description: Build Visual Investigation visuals and motion in an AnimaGuru PixiJS video workspace. Use when this visual style is chosen for an explainer, advertisement or general video.
disable-model-invocation: true
---

# Visual Investigation

A cold investigation desk: footage, photographs, documents, sound and maps from one real event laid on one shared clock so they check each other; frozen frames are circled and magnified, quotes are highlighted on the page, and every piece of evidence is pulled into one map at the end. It is a documentary & broadcast style: real footage, documents, photographs and sound carry the film. Subject, audience, emotional tone and story come from the user's brief. This style supports Explainer, Advertisement and General Video.

## Establish direction

Follow sibling `animaguru-video` for purpose → style → compact interview before new production. Reuse explicit choices and completed briefs; honor a requested interview skip. Share [the style gallery](https://animaguru.com/animation-styles#visual-investigation). Fold missing visual questions into the shared interview:

- Which event's footage, documents, photographs, sound and maps do you have, and what is the one sync point every source should converge on?
- Which time scales should the clock pass through (hours → minutes → seconds → days)?

## Use real evidence

Ask the user for their own footage, documents, photographs, recordings or data first; otherwise find licence-clean sources (see the [production recipe](references/recipe.md)). Mark every inference `≈ / inferred / unlocated / schematic` on screen and in `production/FACTS.md`; never fake a multi-camera event from a single source. Keep `production/CREDITS.md` (every asset's source, author and licence), delivered with the film. CC BY-SA, "no known restrictions" or unclear origin are not usable without the user's explicit agreement.

## Build the look and movement

Read `pixijs` and the relevant Graphics, Mesh, Text or Filters skills. Read `animaguru` before generating assets: generation can supply music or narration, never the evidence itself. Discover current models and estimates, respect the user's budget, and reuse completed media. Essential readouts, tags and findings belong in authored canvas content.

- Cut points are sync points: pick one instant every source can recognise (an impact, a flash, a public clock) and align each source to it; a source that starts late simply appears late.
- One clock lives inside the layout itself (a card timestamp, a chart playhead, a `T+` stopwatch), never a separate reserved timeline band by default.
- Red is the only colour and it only ever points (circles, links, the playhead, the verdict); everything else is grey panels on a near-black ground, and each section says one finding.

Use the [production recipe](references/recipe.md) for sources, the bundled original study and port-specific decisions. It is a technique example, not a prescribed film. Keep motions a function of absolute seconds; separate drawing cadence from camera/light cadence when the material calls for it. Prepare assets locally, preserve async seeking and register actual resource/cue times. Keep essential type editable and localized.

## Review and delivery

Inspect sync-point alignment across sources, inference labelling, source-tag presence on every panel, reading time on verdict boards, and every claim against `FACTS.md`. Check representative full-resolution frames, moving playback, desktop/mobile fit and cold seeks. Follow `animaguru-video` for production records, audio mixing and MP4 delivery. Describe the actual 2D/2.5D rendering method accurately. Physically rendered 3D remains deferred.
