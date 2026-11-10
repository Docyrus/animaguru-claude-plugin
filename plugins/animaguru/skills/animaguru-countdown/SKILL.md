---
name: animaguru-countdown
description: Build Live Countdown Split-screen visuals and motion in an AnimaGuru PixiJS video workspace. Use when this visual style is chosen for an explainer, advertisement or general video.
disable-model-invocation: true
---

# Live Countdown Split-screen

Real-time footage of one event with a known zero: screen time equals event time, a clock ticks every second, and the screen splits into more cells as the moment nears, merging into one picture at zero. It is a documentary & broadcast style: real synced footage, documents and data carry the film. Subject, audience, emotional tone and story come from the user's brief. This style supports Explainer, Advertisement and General Video.

## Establish direction

Follow sibling `animaguru-video` for purpose → style → compact interview before new production. Reuse explicit choices and completed briefs; honor a requested interview skip. Share [the style gallery](https://animaguru.com/animation-styles#countdown). Fold missing visual questions into the shared interview:

- Which event with a known zero, and how many synced camera angles, documents or data do you have?
- Which milestones should the control strip carry, and what should the clock count to after zero?

## Use real evidence

Ask the user for their own footage, recordings, photos or data of the event first; otherwise find licence-clean sources (see the [production recipe](references/recipe.md)). Screen time equals event time: never cut, reorder or speed up the real stretch. Label footage honestly rather than faking sync ("same window · not frame-synced" instead of a forced alignment), and keep `production/FACTS.md` (every number, time, name and call, with source) and `production/CREDITS.md` (every asset's source, author and licence), delivered with the film.

## Build the look and movement

Read `pixijs` and the relevant Container, Graphics, Text or Filters skills. Read `animaguru` before generating assets: generation can supply music or narration, never the event footage itself. Discover current models and estimates, respect the user's budget, and reuse completed media. Essential clock digits, checklists and labels belong in authored canvas content.

- The layout is the edit: cells open, close and resize on a real spoken call or event in the native audio, never on the music; cell count rises toward zero, then drops to one at the merge.
- Draw the clock in fixed-width digit slots so it never jitters; sync badges (synced, same-window, real-time) are part of the look's honesty, not an afterthought.
- At zero, every cell animates to its tile of the merged full-screen frame while chrome fades, then the clock inverts from counting down to counting up.

Use the [production recipe](references/recipe.md) for sources, the bundled original study and port-specific decisions. It is a technique example, not a prescribed film. Keep motions a function of absolute seconds; separate drawing cadence from camera/light cadence when the material calls for it. Prepare assets locally, preserve async seeking and register actual resource/cue times. Keep essential type editable and localized.

## Review and delivery

Inspect sync accuracy at zero, clock digit stability under re-layout, sync-badge honesty on every unsynced cell, and every milestone and number against `FACTS.md`. Check representative full-resolution frames, moving playback, desktop/mobile fit and cold seeks. Follow `animaguru-video` for production records, audio mixing and MP4 delivery. Describe the actual 2D/2.5D rendering method accurately. Physically rendered 3D remains deferred.
