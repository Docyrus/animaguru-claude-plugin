---
name: animaguru-one-line-art
description: Build One-Line Art visuals and motion in an AnimaGuru PixiJS video workspace, where one constant-width line draws every figure without lifting. Use when this visual style is chosen for an explainer, advertisement or general video.
disable-model-invocation: true
---

# One-Line Art

A single thin line draws one figure, keeps going and becomes the next, so the whole film is one unbroken stroke across open space. It is the monoline language of fashion, finance, architecture and jewellery brands: one or two colours, a constant hairline, generous negative space and a line that turns into a filled form for the brand moment. Subject, audience, emotional tone and story come from the user's brief. This style supports Explainer, Advertisement and General Video.

## Establish direction

Follow sibling `animaguru-video` for purpose → style → compact interview before new production. Reuse explicit choices and completed briefs; honor a requested interview skip. Share [the style gallery](https://animaguru.com/animation-styles#one-line-art). Fold missing visual questions into the shared interview:

- Which figures should the one line pass through, in what order, and what does it end on (a logo, a product silhouette, a word)?
- Light ground with ink, or a deep ground with a metallic line? Which one or two colours, and which typeface for the closing wordmark?
- Is a logo or product outline supplied as vector art that the line can trace?

## Build the look and movement

Read `pixijs` and the relevant Graphics, Text, Container and Filters skills. Read `animaguru` before generating assets: generation can supply music or a paper texture, never the line itself. Discover current models and estimates, respect the user's budget, and reuse completed media. The line, the figures it draws and every word belong in authored canvas content.

- Author the whole film as one ordered path. The tail of each figure is the start of the next; plan the joins in the vector file (or in code) before animating, so no figure needs a lift. The pen lifts once, at the end.
- Keep the line width constant for the whole film, 2–4 px at 1080p, measured on screen: when the camera zooms, redraw the stroke at the same screen width rather than scaling it. Use round caps and joins.
- Split the path into strokes at real corners. Inside each stroke, drive arc length with an ease-in-out (`cubic-bezier(0.65, 0, 0.35, 1)`), so the nib slows into every corner and sets off again; give strokes time in proportion to length so the pace stays even.
- Line to fill: once a closed figure (the logo, a product) is complete, expand a fill from the anchor where the line closed it, clipped to the figure, then let any line that falls inside switch to the ground colour so it reads as engraved.
- A virtual camera rides just ahead of the nib with a gentle drift, lets older line settle to a dimmer tone as it moves on, then pulls back so the whole drawing reads as one composed poster above the wordmark.
- Keep texture quiet: an optional faint tremor attached to the path (seeded once, never per frame), a soft glow on the line, a small hot point at the nib, paper tooth on the ground. No gradients inside the line, no second line weight.

Use the [production recipe](references/recipe.md) for the bundled original study and port-specific decisions. It is a technique example, not a prescribed film. Keep motion a function of absolute seconds so cold seeks reproduce the same frame. Prepare assets locally, preserve async seeking and register actual resource/cue times. Keep essential type editable and localized.

## Review and delivery

Scrub every join: no gaps, no doubled caps, no figure that needs a lift. Check that the line keeps one width through zooms, that the nib visibly slows at corners, that each figure reads at the moment it completes and again in the final pull-back, and that the fill stays inside its figure. Check representative full-resolution frames, moving playback, desktop/mobile fit and cold seeks. Follow `animaguru-video` for production records, audio mixing and HTML5 delivery; export MP4 when requested. Describe the actual 2D rendering method accurately.
