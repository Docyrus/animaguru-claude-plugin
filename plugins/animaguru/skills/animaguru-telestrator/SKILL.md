---
name: animaguru-telestrator
description: Build Sports Telestrator visuals and motion in an AnimaGuru PixiJS video workspace. Use when this visual style is chosen for an explainer, advertisement or general video.
disable-model-invocation: true
---

# Sports Telestrator

The TV analysis segment: play the clip at full speed, rewind, freeze it, and draw on the broadcast picture — rings under feet, marker arrows for the ball, a flattened pitch board — then play on and switch angles. It is a documentary & broadcast style: real match footage carries the picture; every line is drawn on top of it. Subject, audience, emotional tone and story come from the user's brief. This style supports Explainer, Advertisement and General Video.

## Establish direction

Follow sibling `animaguru-video` for purpose → style → compact interview before new production. Reuse explicit choices and completed briefs; honor a requested interview skip. Share [the style gallery](https://animaguru.com/animation-styles#telestrator). Fold missing visual questions into the shared interview:

- Which match footage (with rights) and which piece of action gets the full rewind-and-freeze breakdown?
- Which roles (the team or ball, opponents, the space) should the three colours carry, and which sport?

## Use real evidence

Ask the user for their own footage, line-ups, event data or photos first; otherwise find licence-clean sources (see the [production recipe](references/recipe.md)). Real footage only: never invent a number the footage can't support (ball speed, distance run); keep `production/FACTS.md` (every counted number, with how it was measured) and `production/CREDITS.md` (every asset's source, author and licence), delivered with the film.

## Build the look and movement

Read `pixijs` and the relevant Mesh, Filters, Graphics or Text skills. Read `animaguru` before generating assets: generation can supply music or narration, never the match footage itself. Discover current models and estimates, respect the user's budget, and reuse completed media. Essential labels, the stopwatch and the data card belong in authored canvas content.

- Everything is drawn on the real picture in the picture's own coordinates: rings under feet, arrows along the ball's path, traced pitch lines; nothing floats in an abstract diagram until the deliberate flatten.
- One freeze, one finding: flash, punch, desaturate, spotlight, then ring → area or link → label, each 0.3–0.6 seconds apart.
- The perspective flatten fits a homography from marked pitch points and redraws the freeze frame as a mesh moving to board coordinates, reusing the same point set for both views.

Use the [production recipe](references/recipe.md) for sources, the bundled original study and port-specific decisions. It is a technique example, not a prescribed film. Keep motions a function of absolute seconds; separate drawing cadence from camera/light cadence when the material calls for it. Prepare assets locally, preserve async seeking and register actual resource/cue times. Keep essential type editable and localized.

## Review and delivery

Inspect tracked-point accuracy against full-resolution crops, overlay alignment through the freeze's punch transform, packaging placement over any real logo or URL, and every counted number against `FACTS.md`. Check representative full-resolution frames, moving playback, desktop/mobile fit and cold seeks. Follow `animaguru-video` for production records, audio mixing and HTML5 delivery; export MP4 when requested. Describe the actual 2D/2.5D rendering method accurately. Physically rendered 3D remains deferred.
