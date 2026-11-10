---
name: animaguru-whiteboard-line-drawing
description: Build stroke-by-stroke animated illustrations and annotations in marker, ink or chalk treatments. Use for the Whiteboard and Line Drawing visual style in an AnimaGuru video workspace.
disable-model-invocation: true
---

# Whiteboard & Line Drawing

Reveal an illustration through deliberate drawing order, readable marks and connecting annotations. The style does not prescribe a lesson, scene count or audience; apply the selected Explainer, Advertisement or General Video brief.

## Establish the direction

Follow the sibling `animaguru-video` category → style → quick interview flow for a new film. Reuse explicit choices and existing briefs; honor an explicit request to skip the interview. Share [the style preview](https://animaguru.com/animation-styles#whiteboard-line-drawing). Include missing visual choices in the shared interview:

- Whiteboard marker, paper-and-ink, chalkboard, or another reference surface?
- Precise diagram lines or handmade illustration? Which accent colors and annotations are appropriate?
- Should drawings accumulate on one surface or clear between compositions?

## Design and build

- Read `pixijs` and its graphics guidance. Author ordered centerline paths with consistent joins and caps. A flattened raster illustration cannot reveal meaningful pen strokes automatically; use it as a reference, separate reveal layers, or trace the necessary paths.
- Break drawings into logical strokes. Reveal the outline or structural marks before small details, then add labels and annotations when their referent is visible. Keep existing information readable while additions draw.
- Allocate drawing time by approximate path length and importance. Sample curves by distance so a long curve does not race while a short line crawls. Store sampled path points or stroke masks once; expose progress from absolute film time.
- Implement partial strokes in PixiJS with sampled geometry or prebuilt masks. SVG dash animation in a DOM overlay will not appear in a canvas-only MP4 capture; ensure the final drawing is inside the Pixi canvas.
- Decide the surface, ink width and texture at output resolution. Seed handmade irregularity once and keep it attached to the line; per-frame randomness causes shimmer. A hand prop is optional and should be used only if the brief calls for it.
- Keep labels as editable, localized text. Generated artwork can guide drawings or supply a paper texture; use AnimaGuru only when these assets help. Do not rely on generated text for critical wording.
- Give each completed drawing a reading hold. Use erasure, wipes, repositioning or a continuing surface according to the chosen treatment. Track drawing and annotation intervals in the resource timeline.

## Review and completion

Follow `animaguru-video` for audio, records and delivery. Scrub through each stroke to check order, speed, joins and reveal masks. Verify all required marks finish before their composition is removed and labels remain readable on a small screen. Deliver authored stroke data, editable labels and a deterministic HTML5 film; export MP4 when requested.

## Additional visual treatments

Read [the material and motion variants](references/variants.md) when the brief calls for a specialized treatment. Choose the relevant recipe without imposing its example story.
