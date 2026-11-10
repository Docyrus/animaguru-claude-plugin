---
name: animaguru-synthwave-y2k
description: Build Synthwave & Y2K visuals and motion in an AnimaGuru PixiJS video workspace. Use when this visual style is chosen for an explainer, advertisement or general video.
disable-model-invocation: true
---

# Synthwave & Y2K

A whole-film quote of a media era: a neon perspective grid running at a slatted sunset, chrome lettering with a flare and a glint, and Y2K desktop pop-ups driven by a cursor, all played back through one VHS deck. Subject, audience, emotional tone and story come from the user's brief. This style supports Explainer, Advertisement and General Video.

## Establish direction

Follow sibling `animaguru-video` for purpose → style → compact interview before new production. Reuse explicit choices and completed briefs; honor a requested interview skip. Share [the style gallery](https://animaguru.com/animation-styles#synthwave-y2k). Fold missing visual questions into the shared interview:

- Pure 80s synthwave (grid, sun, chrome), Y2K desktop (pop-ups, acid chrome, cursor), or both in one film?
- How worn should the tape be: a light vintage finish, or a tired cassette with tracking errors and stutters?
- Which words get chrome and which get neon, and is there an on-screen action the cursor should perform?

## Build the look and movement

Read `pixijs` and the relevant Graphics, Text, Mesh, Filters and Blend Modes skills. Read `animaguru` before generating assets: generation can supply a soundtrack or a backdrop plate, but the grid, sun, type and windows are drawn in code. Discover current models and estimates, respect the user's budget, and reuse completed media. Essential text belongs in authored canvas content, never baked into an image.

- The grid is a one-point perspective floor computed in world space (lines at fixed world spacing, scrolled by camera travel), so lines thicken toward the lens and stay locked to the horizon. Fade lines into their average glow where a cell shrinks below about 4 px; never let them shimmer into moiré at the horizon.
- The sun is a multi-stop vertical gradient (pale yellow → orange → magenta) with slats cut from its lower half, widening toward the bottom and drifting downward; mountains, palms and cloud strips may cross it, its reflection ripples on the floor.
- Glow is double: a tight bloom of about 3–4 px and a wide one of about 30 px, both from an emission layer that holds only the neon (grid, rims, sun, script tubes), added on top. Glow never lifts the whole frame; keep the sky top near navy-black.
- Chrome lettering is a heavy italic sans with a high-contrast metal gradient that breaks at a hard horizon band near its middle (sky blue → white → dark band → warm tones), a stepped extrusion, a thin bevel highlight, one shine sweep and one star glint. A title slam lands with a flare and, if wanted, a short flash; neon script strikes on left to right with a hot leading edge and a brief sputter.
- Y2K desktop language: glossy pop-ups with gradient title bars, bevelled buttons and candy icons; they pop with overshoot, a cursor moves, presses, drags (an outline may stand in for the window while dragging), cascades more pop-ups and clicks; windows close by collapsing to a line like a switched-off tube. Invent the operating system: no real OS logos, chrome or sounds.
- The VHS chain runs in a fixed order: row wobble and tears, chroma bleed (luma sharp; colour blurred over about 9 px and delayed 1–2 px, or red and blue split 1–2 px), luma noise and dropouts, tracking bars and bottom head-switching noise, then scanlines (every other row 10–15% darker) and rounded tube corners. An on-screen display (PLAY ▶, tape counter, SP) sits above the tape damage and below the scanlines. An optional 4:3 rounded mask is a framing choice, not a requirement.
- Cadence is part of the medium: one or two glitches a second at most, a few passages stepped to 15 fps, and a two-frame reverse stutter on a hit. Keep essential reading moments clean.

Use the [production recipe](references/recipe.md) for the bundled original study and port-specific decisions. It is a technique example, not a prescribed film. Keep motions a function of absolute seconds; separate the scene clock (stepped, stuttered) from the tape clock (noise and glitches always moving). Prepare assets locally, preserve async seeking and register actual resource/cue times. Keep essential type editable and localized.

## Review and delivery

Inspect grid stability near the horizon, chrome legibility under glow, the slam and stutter frames one by one, cursor targets (it must actually reach the buttons it clicks), and that glitches avoid essential text. Check representative full-resolution frames, moving playback, desktop/mobile fit and cold seeks. Fonts must be licensed for embedding (OFL or system-bundled for local rendering); music and sound must be licence-clean or generated. Follow `animaguru-video` for production records, audio mixing and MP4 delivery. Describe the actual 2D/2.5D rendering method accurately. Physically rendered 3D remains deferred.
