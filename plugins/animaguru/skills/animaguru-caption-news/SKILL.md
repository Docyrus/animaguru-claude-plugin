---
name: animaguru-caption-news
description: Build Caption News visuals and motion in an AnimaGuru PixiJS video workspace. Use when this visual style is chosen for an explainer, advertisement or general video.
disable-model-invocation: true
---

# Caption News

Social-video news that reads with the sound off: huge chunk-slammed captions are the lead actor over real footage, photos and documents, and every number arrives with the source tag that proves it. It is a documentary & broadcast style: real footage, photos, documents or data carry the film. Subject, audience, emotional tone and story come from the user's brief. This style supports Explainer, Advertisement and General Video.

## Establish direction

Follow sibling `animaguru-video` for purpose → style → compact interview before new production. Reuse explicit choices and completed briefs; honor a requested interview skip. Share [the style gallery](https://animaguru.com/animation-styles#caption-news). Fold missing visual questions into the shared interview:

- Which footage, photos or documents do you have, and what is the one turn the hook sets up?
- Which keyword gets the yellow block, and what should the lower third carry (place, date or speaker)?

## Use real evidence

Ask the user for their own footage, photos, documents or data first; otherwise find licence-clean sources (see the [production recipe](references/recipe.md)). Never stand a generated image in for the evidence, and never show a number without its source tag in the same shot. Keep `production/FACTS.md` (each on-screen or spoken claim, its source URL and quoted wording, or the measurement method) and `production/CREDITS.md` (every asset's source, author and licence), and deliver both with the film. CC BY-SA, "no known restrictions" or unclear licences are not CC0: name them to the user and ask before using them.

## Build the look and movement

Read `pixijs` and the relevant Graphics, Text, Container, Assets or Filters skills. Read `animaguru` before generating assets: generation can supply music or narration, never the evidence itself. Discover current models and estimates, respect the user's budget, and reuse completed media. Essential captions, numbers and charts belong in authored canvas content, never baked into footage.

- The caption card is the shot: one Chinese line and one English line, chunk-slammed a piece at a time, one keyword per caption wiped into a honey-yellow block; never wrapped.
- Numbers roll in fixed-width digit cells with their source tag in the same shot; a document highlight sweeps the exact line before its figure is restated as a block.
- Cuts land on a half-beat grid; transitions are a small fixed set (hard cut, a short white flash, a card sliding in, a split, a lit grid, a mask growing out of a map shape) — never dissolves or page turns.

Use the [production recipe](references/recipe.md) for sources, the bundled original study and port-specific decisions. It is a technique example, not a prescribed film. Keep motions a function of absolute seconds; separate drawing cadence from camera/light cadence when the material calls for it. Prepare assets locally, preserve async seeking and register actual resource/cue times. Keep essential type editable and localized.

## Review and delivery

Inspect reading time on every caption and chart title, source-tag presence beside every number, footage credits in the corner, keyword-wipe timing, and every figure against `FACTS.md`. Check representative full-resolution frames, moving playback, desktop/mobile fit and cold seeks. Follow `animaguru-video` for production records, audio mixing and MP4 delivery. Describe the actual 2D/2.5D rendering method accurately. Physically rendered 3D remains deferred.
