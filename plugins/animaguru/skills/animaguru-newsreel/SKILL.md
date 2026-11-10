---
name: animaguru-newsreel
description: Build 1920s Newsreel visuals and motion in an AnimaGuru PixiJS video workspace. Use when this visual style is chosen for an explainer, advertisement or general video.
disable-model-invocation: true
---

# 1920s Newsreel

A sound newsreel of the late 1920s cut from real archive material: a searchlight-and-globe ident with a brass fanfare, a newspaper spinning into the lens, a fast announcer and a hot band, all inside one silver-graded projector gate. It is a documentary & broadcast style: real archive film, photographs, print or recordings carry the picture; only the packaging is drawn. Subject, audience, emotional tone and story come from the user's brief. This style supports Explainer, Advertisement and General Video.

## Establish direction

Follow sibling `animaguru-video` for purpose → style → compact interview before new production. Reuse explicit choices and completed briefs; honor a requested interview skip. Share [the style gallery](https://animaguru.com/animation-styles#newsreel). Fold missing visual questions into the shared interview:

- Which archive film, photographs, print or recordings do you have, or should be found, and what is the one place-and-story arc?
- What is the ident's fictional name, and which native transitions (iris, wipe, flip) fit the story's turns?

## Use real evidence

Ask the user for their own archive film, photographs, print or recordings first; otherwise find licence-clean sources (see the [production recipe](references/recipe.md)). Never generate "archive" pictures: only the ident, cards, maps and end card are drawn, and the footage and print must be real. Keep `production/FACTS.md` (each on-screen or spoken claim, its source URL and quoted wording) and `production/CREDITS.md` (every asset's source, author and licence), and deliver both with the film. CC BY-SA or "no known restrictions" are not a clear licence: name them to the user and ask before using them.

## Build the look and movement

Read `pixijs` and the relevant Filters, Mesh, Graphics, Text or Assets skills. Read `animaguru` before generating assets: generation can supply music or narration, never the archive footage itself. Discover current models and estimates, respect the user's budget, and reuse completed media. Essential place cards and subtitles belong in authored canvas content, never baked into the picture.

- One silver grade and projected gate (1.37:1, rounded corners, black outside) sits over every real shot; flicker, gate weave and scratches belong to the picture layer only, never to type.
- The ident, spinning paper, map spread, place cards and end card are the only generated elements; draw them with Graphics and Text, never as a stand-in for archive imagery.
- Cuts and landings ride a hot-band beat grid; use the style's own fixed transitions (iris, diagonal wipe, flip, venetian blinds, clock wipe) once each, never a cross-dissolve between stories.

Use the [production recipe](references/recipe.md) for sources, the bundled original study and port-specific decisions. It is a technique example, not a prescribed film. Keep motions a function of absolute seconds; separate drawing cadence from camera/light cadence when the material calls for it. Prepare assets locally, preserve async seeking and register actual resource/cue times. Keep essential type editable and localized.

## Review and delivery

Inspect the gate mask at every corner, grade consistency across clips (one level set per clip, never per frame), place-card reading time, subtitle one-line limits, and every date or claim against `FACTS.md`. Check representative full-resolution frames, moving playback, desktop/mobile fit and cold seeks. Follow `animaguru-video` for production records, audio mixing and MP4 delivery. Describe the actual 2D/2.5D rendering method accurately. Physically rendered 3D remains deferred.
