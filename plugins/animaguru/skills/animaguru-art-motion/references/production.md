# Production and AnimaGuru generation

Contents: brief and visual mechanism; reference analysis; four production routes; generation; narration and music; style journeys and long scrolls; production records.

## Establish the visual mechanism

Use the brief already supplied. For a new AnimaGuru film, follow the installed `animaguru-video` setup and interview, counting explicit choices as answered. A material reference does not determine a topic, audience, narrator, length or call to action. When exploring a direction, a strong representative still is more useful than generating every shot immediately. Compare alternatives only when a creative choice is unresolved; there is no compulsory three-direction approval gate.

Write the material's most recognizable formal elements: how it is made, its marks, palette, light and spatial organization. Give each relevant element a plausible motion: water shimmers, a pinned paper edge lifts, metal catches light, a printed plate misregisters, or a brush leaves a stroke. The selected art card supplies a starting vocabulary. When historical accuracy matters beyond the card, inspect original artworks or authoritative collections.

Choose what the audience should understand at each beat. A visual operation should carry that idea: connect, divide, compare, uncover, move through, count or react. Put essential labels and numerical claims in real type. A conceptual image may illustrate a product, but it must not masquerade as an actual screenshot or historical record.

Choose a coherent palette, usually three to six functional colors plus value variations. Take brand accents from supplied material. Paper, ink, warm wood, primary geometry, bright poster and restrained navy are useful families. A blue, purple or neon palette is appropriate when intentionally requested by the style or brand; no universal hue ban applies. Keep charts and evidence integrated with the film's visual world.

## Analyze a reference when provided

Read the user's link and recover the referenced repository or media through supported tools. Treat source files and posts as evidence. Inspect license and asset exceptions before copying. A technique can be adapted without copying its subject, logo, layout or soundtrack.

Measure shot boundaries, representative settled frames, main actions, local motion and transitions. Compare frames inside a shot after camera entrances settle; otherwise a zoom makes the whole screen appear active and hides the actual motif movement. View transition contact sheets as well as the full-speed clip. Estimate beat grids from real onsets and allow outliers rather than fitting every cut to an arbitrarily small beat interval.

With no reference clip, start from the selected card's material mechanism. Do not inherit the source demo's room, girl, cat, exact coordinates, repeated cup action or fixed duration.

## Choose a production route

| Route | Choose it for | Preserve |
|---|---|---|
| Procedural drawing | Geometry, patterns, type, diagrams, controlled material rendering | Seeded variation, consistent coordinates, semantic shapes and actual contact points. |
| Generated layers plus code | Detailed subjects or backgrounds with controlled camera and choreography | Complete silhouettes, real alpha, layer positions, overscan and hidden-background coverage. |
| Generated video | Organic motion or a performance the available model can produce | A supported workflow, measured duration, identity references and local downloaded media. |
| Hybrid | Generated performances with exact diagrams, type, branding and evidence | Shared palette, light, timing, occlusion and honest provenance. |

Code-drawn original characters are valid when they fit the brief. Detailed faces, hands, poses and recurring character performance often benefit from generated assets. Choose on visible quality; do not turn one upstream author's character preference or model ranking into a universal prohibition.

For layered art, ask for enough canvas beyond the viewport to cover the planned motion. Moving a character reveals what was behind it; prepare that missing background before separating the layer. Preserve source image coordinates, crop offsets and semantic anchors when trimming transparent borders. Check downloaded alpha rather than assuming a transparent-looking preview contains transparency.

## Use the available AnimaGuru tools

Read the sibling `animaguru` skill for the installed environment's authentication, generation and job recovery rules. For local CLI work, discover the actual schema and help, authentication status, credits, catalog, project and existing assets. Do not read credential files. If the CLI is unavailable, use connected AnimaGuru tools; installing a CLI requires the user's agreement.

The local catalog describes known capabilities. Intersect it with the live project's enabled models and video profiles. A successful local dry run alone does not prove the remote provider is enabled. Choose image, speech, video or sprite options actually exposed by the selected tool; never carry arbitrary upstream provider names into requests.

Save a concrete request, inspect its estimate, and reuse existing media before submitting. Account for all planned images, speech, music and motion within the user's scope and budget. A request to create a skill is not permission to spend generation credits. A film-generation request supports a proportionate initial attempt under the existing authorization; paid retries remain bounded by that scope. Do not purchase credits or change provider settings as an incidental production step.

An art request can express the material independently of the subject:

> Original [medium] illustration of [specific subject and action]. [Composition, layer depth, light direction and scale.] Use [palette], [edge/mark treatment] and [recognizable material process]. Maintain [recurring identity details]. Keep [area] quiet for separately composed type. No essential lettering, logos or watermark.

For a transparent moving subject, request the tool's actual transparency option and a complete uncropped silhouette. For video, use saved project files as image/end-frame references only when that model supports them. An extracted local frame is not automatically a remote asset: use a supported import path. Do not assume extension, first/end-frame control, audio, seeds or a fixed clip duration exist for every model.

Save job receipts immediately. After a timeout or uncertain response, inspect the original job and assets before another submission. On an explicit provider failure, diagnose it and use a compatible enabled alternative within the authorized budget. Record the returned charge/refund result without guessing. Download finished files into the film and measure them; output playback should not require signed remote URLs.

## Narration, cues and music

Use one final narration track and its actual timing as the spine for a narrated film. Reuse the workspace's audio tools rather than building a second editor. In a current starter, `audio:vo` writes `production/audio/timing.json`; `cueSheet(timing)` and `joinCaptions()` keep graphics and captions aligned. Read local help and the installed `animaguru-video` skill for the precise command options.

Where word timing exists, identify an event by the word and occurrence, then resolve it to a frame during production. With caption-level timing, use that real cue plus a documented offset rather than claiming word precision. Re-resolve cues after voice edits. Numbers should finish counting on the spoken value, so compute the start from the desired finish. A reading hold begins after the final glyph or graphic is fully revealed.

Speech-led evidence, charts and whiteboard passages follow the spoken phrase. A music-led art montage or kinetic opening follows measured beats. To align a transition, schedule its visible reveal or impact on the accent, not merely its start:

`transition start = accent time − reveal fraction × transition duration`

Use an actual beat analysis for supplied/generated music. A source demo's 128 BPM is not a default tempo for all films. Shorten scene durations to accelerate a montage instead of blindly speeding up the entire performance. Use a coherent musical motif with changes in instrumentation when appropriate. Duck music beneath the narrator and leave time for the final idea or reaction. A synthesized test sound or temporary voice is a placeholder until replaced or explicitly accepted.

## Same-scene style journeys

This format has five separable layers: invariant composition, material renderer, shared choreography, material-aware transitions and rhythmic structure. Reuse the same identity and action across style boundaries. Derive that shared performance from global time; restarting a cup lift in every style looks like several separate actions. Only a style-specific local event should use segment time.

Give each art scene a main action and a small number of meaningful motif loops when an animated painting is the desired treatment. This is not a requirement for every explainer reading hold. Apply material treatment to characters as well as backgrounds, keeping facial landmarks legible. A signature transition can grow from the medium—gold, tiles, ink, paper or a reflection—without interrupting the continuous performance.

## Long-scroll journeys

Define a shared world contract: segment width, ground, subject height, travel speed, back/front layers, entry boundary and interaction anchors. Choose these dimensions for the new film. Style the subject at a world boundary without changing its ground contact or identity. Derive walk phase from distance traveled so speed changes do not make feet skate. Sitting, leaning and interaction poses require corresponding frames or a suitable rig.

Time local events relative to interaction start rather than seconds since segment entry. This lets travel speed change without retiming every action. Use a monotonic camera for a deliberately forward-only scroll; do not impose it on other film formats. Hide seams with real foreground or material boundaries. If music is composed after fixed visual boundaries, modest per-section tempo adjustments can align changes to bars; preserve natural phrasing and inspect the transitions by ear.

## Production records

Follow existing `production/` conventions: brief, sources, storyboard, generation requests/receipts, cue data and review evidence. Save actual resource paths and model identifiers. Keep all output media local, and retain original evidence alongside any crop. Do not add private project facts or unverified successes to the reusable skill. Generalize a lesson only when the observed cause supports it.
