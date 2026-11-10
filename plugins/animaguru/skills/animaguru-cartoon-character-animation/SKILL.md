---
name: animaguru-cartoon-character-animation
description: Create animated films with expressive illustrated characters, readable poses and coordinated props. Use for the Cartoon Character Animation visual style in an AnimaGuru video workspace.
disable-model-invocation: true
---

# Cartoon Character Animation

Use illustrated characters and clear acting to express the user's message. Casting, relationships, mood and narrative come from the Explainer, Advertisement or General Video brief; a cartoon treatment does not imply a child audience or comedy.

## Establish the direction

Follow the sibling `animaguru-video` category → style → quick interview flow for new films. Reuse supplied choices and briefs; honor an explicit request to skip the interview. Share [the style preview](https://animaguru.com/animation-styles#cartoon-character-animation). Add missing visual choices to the shared interview:

- Which characters, objects or mascots are needed, and are approved designs available?
- What line weight, palette, shading and illustration references should guide the cast?
- Should acting be subtle, broad or stylized? Is speech shown on camera, off screen, or absent?

## Design and build

- Read `animaguru` for generation, reference imports, current model discovery and custom motion jobs. Use `hd-cartoon` where appropriate. Record a concise model sheet: silhouette, proportions, clothing, palette, facial features and view. Reuse approved assets to preserve identity.
- Plan performances as readable poses with anticipation, action and a resolved hold. Choose the necessary motion from the actual story. AnimaGuru's built-in game actions are not a complete acting vocabulary; use supported custom motions for pointing, considering, presenting and other brief-specific actions.
- Read `pixijs`, sprite and container guidance. Choose spritesheets, separate articulated parts or generated video based on the performance. Simple limb transforms are precise; nuanced facial acting may need generated frames or video. Do not apply rubbery stretching to every design.
- Keep character anchors, apparent height, facing and prop ownership consistent. Separate rear limbs, torso, front limbs and held props where needed. Track contact points to prevent floating feet and sliding hands.
- Derive spritesheet frame indices from absolute time, respecting per-animation frame counts, holds and loop behavior. Match the performance cadence to the selected design while keeping the film export fps explicit.
- Give acting priority over background motion. Aim eye lines and gestures toward the intended focus. Use reaction holds rather than constant idle movement for every character.
- For dialogue, use verified phoneme/viseme or performance timing when lip sync is required. A talking loop is not accurate lip sync. If only off-screen narration is needed, keep mouth movement appropriate to the scene.
- Keep typography and captions editable, and register characters, props and scene layers in the resource timeline. Generated video must obey the shared asynchronous frame-decoding contract.

## Review and completion

Follow `animaguru-video` for production records, audio and exports. Inspect character identity, hands, eye lines, contact points, occlusion, pose readability and loop seams. Check movements at full speed and selected extremes. Deliver approved cast assets, coherent performances and the working HTML5 film; export MP4 when requested.

## Additional visual treatments

Read [the material and motion variants](references/variants.md) when the brief calls for a specialized treatment. Choose the relevant recipe without imposing its example story.
