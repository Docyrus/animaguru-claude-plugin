---
name: animaguru-sticker-explainer
description: Build Sticker Explainer visuals and motion in an AnimaGuru PixiJS video workspace. Use when this visual style is chosen for an explainer, advertisement or general video.
disable-model-invocation: true
---

# Sticker Explainer

The knowledge-video board: cut-out photos with thick white borders, flat icons and exact charts laid across one huge calm canvas, and a single camera that travels from fact to fact while every narration line brings a new element. It reads serious and dense: restrained colour, one monoline sans, numbers that are always to scale. Subject, audience, emotional tone and story come from the user's brief. This style supports Explainer, Advertisement and General Video.

## Establish direction

Follow sibling `animaguru-video` for purpose → style → compact interview before new production. Reuse explicit choices and completed briefs; honor a requested interview skip. Share [the style gallery](https://animaguru.com/animation-styles#sticker-explainer). Fold missing visual questions into the shared interview:

- Which photos, product shots or data do you have, and which facts should the camera visit, in what order?
- What is the one number or conclusion the board pulls back to at the end?

## Keep the facts traceable

Ask the user for their own photos and data first; otherwise use licence-clean sources (see the [production recipe](references/recipe.md)). Every number on the board comes from a source or a stated calculation: keep `production/FACTS.md` (each figure, its source URL or the arithmetic behind it) and `production/CREDITS.md` (every photo's source, author and licence), and deliver both with the film. Generated cut-outs may stand in for generic objects (a cup, a sack, a phone), never for a specific real person, place, product or event, and a generated image never carries a figure. Rounded or illustrative values say so on screen.

## Build the look and movement

Read `pixijs` and the relevant Container, Sprite, Graphics, Text and Filters skills. Read `animaguru` before generating assets; discover current models and estimates, respect the user's budget, and reuse completed media. Essential numbers, labels and charts stay authored canvas content, never baked into a picture.

- One board, several frames wide and tall, on a cool neutral ground (blue-grey or off-white) with a faint dot grid and fibre; facts sit in regions on it, linked by thin dashed threads. Only the camera moves between regions.
- Every photo becomes a sticker: subject cut out, then one uniform white margin of 8–12 px at delivery size, a soft shadow with a tight contact core and the same light direction on every sticker. Bake the margin into the texture so it never thickens or thins with the camera zoom.
- Stickers slap on: they drop from about 1.3× scale with a few degrees of turn while their shadow tightens, land in 0.2–0.3 s and settle with a small spring; the board can thump by under 1% on impact.
- The camera holds with a slow 2–3% push, then travels in 0.7–1 s with a long ease, easing back mid-move so the departing and arriving facts share the frame; it ends pulled back on the whole board with the conclusion set large in the middle.
- One narration line, one new element: a sticker, a counter, a chart or a labelled leader line lands within about 0.2 s of its line. Keep the subtitle in a fixed pill, a chapter tag in a corner, and two or three colours plus one accent.
- Charts are exact: zero-based bars to scale from one data model, counters rolling in fixed-width digit cells to the exact final value, and a source or approximation note under each chart.

Use the [production recipe](references/recipe.md) for sources, the bundled original study and port-specific decisions. It is a technique example, not a prescribed film. Keep motions a function of absolute seconds. Prepare assets locally, preserve async seeking and register actual resource/cue times. Keep essential type editable and localized.

## Review and delivery

Check every figure against `FACTS.md`, bar lengths against their values, sticker margins and shadows for consistency at every zoom, that no frame mid-move is an empty stretch of board, that labels clear the subtitle pill, and that the final pull-back frame reads as a finished poster. Check representative full-resolution frames, moving playback, desktop/mobile fit and cold seeks. Follow `animaguru-video` for production records, audio mixing and MP4 delivery. Describe the actual 2D/2.5D rendering method accurately. Physically rendered 3D remains deferred.
