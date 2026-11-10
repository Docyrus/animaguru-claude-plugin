---
name: animaguru-variety-captions
description: Build Variety Captions visuals and motion in an AnimaGuru PixiJS video workspace. Use when this visual style is chosen for an explainer, advertisement or general video.
disable-model-invocation: true
---

# Variety Captions

TV variety-show packaging: chunky rounded captions in layered outlines pop onto the footage a beat after every gag, and each feeling gets its own treatment, from bouncing question marks to a burst frame on a freeze. It turns a vlog, a pet clip, an interview or a product demo into an episode. Subject, audience, emotional tone and story come from the user's brief. This style supports Explainer, Advertisement and General Video.

## Establish direction

Follow sibling `animaguru-video` for purpose → style → compact interview before new production. Reuse explicit choices and completed briefs; honor a requested interview skip. Share [the style gallery](https://animaguru.com/animation-styles#variety-captions). Fold missing visual questions into the shared interview:

- Which footage carries the film, and which three to five moments are the gags or turns the captions answer?
- Which language and voice do the captions speak in (the narrator, the subject's inner voice, a commentator), and how cheeky may they be?

## Footage and assets

Ask for the user's own footage first; the captions are written for real moments, so the clip decides the gags. Otherwise use licence-clean stock (CC0 or public domain, or a licence the user confirms) and record each file in `production/CREDITS.md`. A generated clip is allowed only when the user agrees, and it must never pose as a real recorded moment of a real person or animal. Bundle every font locally with its licence: heavy rounded faces such as Nunito Black, Baloo 2, M PLUS Rounded 1c, ZCOOL KuaiLe or Smiley Sans (all OFL), and a hand-lettering face such as Caveat or Patrick Hand for asides.

## Build the look and movement

Read `pixijs` and the relevant Text, Graphics, Container and Filters skills. Read `animaguru` before generating assets: generation can supply music, sound effects or narration; the captions themselves stay authored, editable canvas text.

- Every caption is three layers plus a shadow: a fill with a two-stop gloss (a hard step at about half height), a white outline of about 0.18 em and a coloured outer outline of about 0.34 em, over an offset drop shadow (about 0.04 em right, 0.08 em down, half opacity). Draw each layer across the whole line before the next, so no letter's outline covers its neighbour's fill.
- Entrances overshoot: scale 0 → 1.15 → 1.0 over about eight frames at 24 fps, or letter by letter with a two-frame stagger and a short hop. Exits are a three-to-four-frame pop. Long holds keep a gentle wiggle (±2–3°, ±2–3 px).
- A caption lands two to three frames after its beat (the visual moment or the sound cue), never before, and the edit supports it: a two-frame snap punch-in, a freeze with a slow push, a jump cut to the reaction.
- Match each feeling to one treatment and one palette: curiosity gets bouncing question marks; shock a freeze, a two-frame white flash, a jagged burst frame, converging speed lines redrawn every two frames and a decaying shake; awkwardness a sliding sweat drop, gloom lines and cool lavender; delight twinkling sparkles in pink and magenta; a verdict a worn rubber stamp slammed from about 2.3× to 1× in three frames; a snarky aside small slanted hand lettering in parentheses.
- Keep faces and the gag itself clear, keep a show bug in one corner, and stay inside about 5 % safe margins. Use idiomatic copy and correct punctuation in the captions' language, including CJK punctuation.

Use the [production recipe](references/recipe.md) for the bundled original study and port-specific decisions. It is a technique example, not a prescribed film. Keep motions a function of absolute seconds; separate drawing cadence from camera/light cadence when the material calls for it. Prepare assets locally, preserve async seeking and register actual resource/cue times. Keep essential type editable and localized.

## Review and delivery

Inspect each caption's landing against its beat (two to three frames late, never early), reading time on every caption, overlap with faces and the show bug, outline order between neighbouring letters, fallback fonts and phone-size legibility. Check representative full-resolution frames, moving playback, desktop/mobile fit and cold seeks. Follow `animaguru-video` for production records, audio mixing and MP4 delivery. Describe the actual 2D/2.5D rendering method accurately. Physically rendered 3D remains deferred.
