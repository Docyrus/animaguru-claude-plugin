---
name: animaguru-interface-motion
description: Animate supplied screens or conceptual interfaces with accurate cursor targets, focus treatments and state transitions. Use for the Interface Motion visual style in an AnimaGuru video workspace.
disable-model-invocation: true
---

# Interface Motion

Turn interface surfaces into clear animated compositions. The Explainer, Advertisement or General Video brief supplies the story and product claims; this style defines screen treatment, focus and motion.

## Establish the direction

Follow the sibling `animaguru-video` category → style → quick interview flow for new films. Reuse supplied choices and briefs; honor an explicit request to skip the interview. Share [the style preview](https://animaguru.com/animation-styles#interface-motion). Include missing visual questions in the shared interview:

- Are the screens actual product screenshots/recordings, or should the film use a conceptual interface?
- Which states, controls and interactions matter, and what approved copy describes them?
- Should screens fill the composition or sit in a restrained frame? What cursor, zoom and callout treatment suits the brand?

## Design and build

- Read `pixijs`, assets, container and text guidance. Inspect supplied screenshots at their native dimensions. Record each state's source and intended action before building transitions. A screenshot proves its visible state, not an unseen interaction or product capability.
- Read [screen mapping](references/screen-mapping.md) for coordinate and capture rules. Store verified control bounds, cursor targets, crops and callout anchors in `production/` so they can be reviewed.
- Move the cursor toward the actual target, pause for recognition, show the interaction, then reveal its resulting state. Use a next screenshot or an authored state transition only when the outcome is supported. Identify invented interfaces as conceptual in the film or surrounding context as appropriate.
- Parent the screen, target markers and interaction effects to the same transformed container. If callouts stay in screen space, derive their anchors through the same transform. Limit zoom by source resolution and legibility; obtain better source images when enlargement becomes soft.
- Place callouts beside the relevant control, keeping the control, pointer and important UI copy unobstructed. Recalculate placement for aspect-ratio or language changes.
- Use focus masks, cropped detail views, restrained pans and state-to-state matches. Device frames and cursor effects are optional treatments selected through the brief.
- Recreate simple conceptual components in PixiJS for editable labels and state transitions. AnimaGuru can provide supporting assets or narration; do not generate fake screenshots of a real product and present them as actual UI.
- Ensure screenshots and recordings are approved for inclusion. Redact private information before placing media in `public/assets/`, which `animaguru submit` uploads with the film.
- Register real screens, cursor intervals and callouts in the resource timeline. Keep interactions deterministic; playback demonstrates the recorded sequence rather than calling a live application.

## Review and completion

Follow `animaguru-video` for audio and export. Inspect the frame immediately before and after every click; verify the target, focus mask and resulting state. Check callouts at mobile size and replay/backward seeking. Deliver the source-to-canvas coordinate map, readable screen assets and the finished film as an MP4.

## Additional visual treatments

Read [the material and motion variants](references/variants.md) when the brief calls for a specialized treatment. Choose the relevant recipe without imposing its example story.
