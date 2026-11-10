---
name: animaguru-news-package
description: Build Broadcast News Package visuals and motion in an AnimaGuru PixiJS video workspace. Use when this visual style is chosen for an explainer, advertisement or general video.
disable-model-invocation: true
---

# Broadcast News Package

A television newsroom's on-air package built entirely in code: a sting that becomes the channel bug, a rundown that opens and closes the bulletin, a lower-third strap that never leaves the frame, and full-frame graphics that carry the facts. It is a documentary & broadcast style; it can run as pure graphics over real data, with footage optional. Subject, audience, emotional tone and story come from the user's brief. This style supports Explainer, Advertisement and General Video.

## Establish direction

Follow sibling `animaguru-video` for purpose → style → compact interview before new production. Reuse explicit choices and completed briefs; honor a requested interview skip. Share [the style gallery](https://animaguru.com/animation-styles#news-package). Fold missing visual questions into the shared interview:

- How many stories, and which graphics does each need (a split-flap board, a threshold chart, an explainer map, a spec card, a quote card)?
- Does the user have their own brand (name, plate colour, voice), or should one be invented for this film?

## Use real evidence

Every on-screen number and sentence comes from an official source first; ask the user for their own data, pictures or a recorded voice before anything else (see the [production recipe](references/recipe.md)). Draw charts from real series only; tag a line `SCHEMATIC` when only a few numbers are known. A generated illustrative plate is a last resort, always tagged `ILLUSTRATION` while visible, and never stands in for the event, a place or a person. Keep `production/FACTS.md` (claim, URL, quoted wording) and `production/CREDITS.md`, delivered with the film.

## Build the look and movement

Read `pixijs` and the relevant Graphics, Text, Container or Filters skills. Read `animaguru` before generating assets: generation can supply an anchor voice, music or an illustrative plate, never the facts themselves. Discover current models and estimates, respect the user's budget, and reuse completed media. Essential straps, datelines and numbers belong in authored canvas content.

- One package system throughout: a brand plate, a tab, a paper strap, ink cards, mono datelines, stamps — viewers read the system before the words.
- The strap never leaves the frame from the first story to the recap; its tab changes category with a flash; the sting becomes the bug by flying into the corner.
- The package travels with its picture: under a wipe, draw the strap, tab, source line and corner tag per side of the wipe, never once on top of everything, so the chrome never lags the cut.

Use the [production recipe](references/recipe.md) for sources, the bundled original study and port-specific decisions. It is a technique example, not a prescribed film. Keep motions a function of absolute seconds; separate drawing cadence from camera/light cadence when the material calls for it. Prepare assets locally, preserve async seeking and register actual resource/cue times. Keep essential type editable and localized.

## Review and delivery

Inspect strap/tab/source-line sync under every wipe, schematic-vs-data labelling, source-line length limits, every claim against `FACTS.md`, and illustration tagging on any generated plate. Check representative full-resolution frames, moving playback, desktop/mobile fit and cold seeks. Follow `animaguru-video` for production records, audio mixing and MP4 delivery. Describe the actual 2D/2.5D rendering method accurately. Physically rendered 3D remains deferred.
