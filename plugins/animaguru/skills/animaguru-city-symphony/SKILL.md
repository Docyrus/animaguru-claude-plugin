---
name: animaguru-city-symphony
description: Build Time-lapse Symphony visuals and motion in an AnimaGuru PixiJS video workspace. Use when this visual style is chosen for an explainer, advertisement or general video.
disable-model-invocation: true
---

# Time-lapse Symphony

A city film cut like a piece of minimalist music: time-lapse turns traffic, crowds and clouds into rivers of light, the cuts get denser with the score's subdivisions, one thing slows almost to a stop, and the film ends on a hard cut to black on a downbeat. It is a documentary & broadcast style: real time-lapse, aerial, archive or photographic footage carries the film. Subject, audience, emotional tone and story come from the user's brief. This style supports Explainer, Advertisement and General Video.

## Establish direction

Follow sibling `animaguru-video` for purpose → style → compact interview before new production. Reuse explicit choices and completed briefs; honor a requested interview skip. Share [the style gallery](https://animaguru.com/animation-styles#city-symphony). Fold missing visual questions into the shared interview:

- Which place, and which licence-clean time-lapse, aerial or archive footage should carry the film, and what is its one slowed, fragile moment?
- What is the score's tempo and arc (minimal repetition → acceleration → climax → hard stop → coda)?

## Use real evidence

Ask the user for their own time-lapses, photographs, documents or data of the place first; otherwise find licence-clean sources (see the [production recipe](references/recipe.md)). Footage only: never generate images, never use colourised or "restored" archive copies, never a YouTube mirror without a passed review. Keep `production/FACTS.md` (every number from an official source, with its URL and quoted wording) and `production/CREDITS.md` (every asset's source, author and licence), delivered with the film.

## Build the look and movement

Read `pixijs` and the relevant Filters, Container, Graphics or Text skills. Read `animaguru` before generating assets: generation can supply music or narration, never the city's own footage. Discover current models and estimates, respect the user's budget, and reuse completed media. Essential number cards and the closing quote belong in authored canvas content.

- Density follows the score: the cut grid (bars, beats, subdivisions) comes from one tempo function, never a hand-typed duration; the grid split (1×2 up to 4×4) is this style's split screen.
- Speed is the instrument: every sped-up shot reads as motion-blurred light, not stepped frames; one moment brakes into slow motion exactly where the music's arpeggios stop.
- One 35mm release-print grade and matte unify every source, archive included; number cards and the closing quote stay left-aligned, never centred or boxed.

Use the [production recipe](references/recipe.md) for sources, the bundled original study and port-specific decisions. It is a technique example, not a prescribed film. Keep motions a function of absolute seconds; separate drawing cadence from camera/light cadence when the material calls for it. Prepare assets locally, preserve async seeking and register actual resource/cue times. Keep essential type editable and localized.

## Review and delivery

Inspect cut-to-beat alignment, grade consistency across day and night shots, text reading time against `readcheck`-style limits, and every number against `FACTS.md`. Check representative full-resolution frames, moving playback, desktop/mobile fit and cold seeks. Follow `animaguru-video` for production records, audio mixing and MP4 delivery. Describe the actual 2D/2.5D rendering method accurately. Physically rendered 3D remains deferred.
