---
name: animaguru-aurora-glass
description: Build Aurora & Glass visuals and motion in an AnimaGuru PixiJS video workspace. Use when this visual style is chosen for an explainer, advertisement or general video.
disable-model-invocation: true
---

# Aurora & Glass

Slow drifting fields of blurred colour under frosted glass cards with hairline highlights: the calm, translucent look of current product and AI launches, where everything breathes and nothing hurries. Subject, audience, emotional tone and story come from the user's brief. This style supports Explainer, Advertisement and General Video.

## Establish direction

Follow sibling `animaguru-video` for purpose → style → compact interview before new production. Reuse explicit choices and completed briefs; honor a requested interview skip. Share [the style gallery](https://animaguru.com/animation-styles#aurora-glass). Fold missing visual questions into the shared interview:

- Which neighbouring hues fit the brand (violet, blue and teal; or orange, pink and red), on a dark or a light ground?
- What do the cards hold (real product screens, a conversation, settings, a few numbers), and which single moment deserves the clear lens?

## Build the look and movement

Read `pixijs` and the relevant Graphics, Text, Container, Filters or Mesh skills. Read `animaguru` before generating assets; discover current models and estimates, respect the user's budget, and reuse completed media. Essential text, interface states and numbers belong in authored canvas content.

- Aurora ground: three to five large solid shapes blurred 80–150 px, each drifting on its own slow closed path (a 20–40 s loop) and breathing a few percent in size over a deep base. Keep to two or three neighbouring hues; complementary colours turn muddy where they blend. Add a few thin light threads or specks so the glass has detail to soften.
- Glass cards: the backdrop blurred 20–40 px inside a large-radius rounded shape, a 5–10 % white fill, a one-pixel inner edge at about 30 % white, a faint top sheen and a soft lifted shadow. Stack two or three cards at different depths: nearer cards drift further and blur whatever lies behind them, farther cards included.
- Light: one key light travels slowly; each glass edge brightens where its normal faces it, so light slides along the edges as cards and light move.
- Hero lens, at most one per film: a clear liquid-glass shape that magnifies its centre, bends hard at a bevelled rim with a slight colour split, and carries a specular edge toward the light. Let it glide over the content, then settle into a capsule or button that holds the title.
- Pace: sine or near-linear easing, no overshoot and no bounce. Text and interface content enter only with opacity and about 8 px of rise, staggered; state changes crossfade. Receding layers lose opacity and fall out of focus rather than flying away.
- Add 3–5 % noise or dither over the frame against gradient banding, and judge banding in the exported file at its delivery bitrate.

Use the [production recipe](references/recipe.md) for the bundled original study and port-specific decisions. It is a technique example, not a prescribed film. Keep motions a function of absolute seconds; separate drawing cadence from camera/light cadence when the material calls for it. Prepare assets locally, preserve async seeking and register actual resource/cue times. Keep essential type editable and localized.

## Review and delivery

Inspect banding in the colour fields, edge highlights that stay one pixel and follow the light, card text that stays legible over the brightest field, blur that visibly softens what sits behind each card, and that nothing moves fast. Check representative full-resolution frames, moving playback, desktop/mobile fit and cold seeks. Follow `animaguru-video` for production records, audio mixing and MP4 delivery. Describe the actual 2D/2.5D rendering method accurately. Physically rendered 3D remains deferred.
