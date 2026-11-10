---
name: animaguru-kinetic-typography
description: Build type-led animated videos with phrase choreography, editable text, and speech or music synchronization. Use for the Kinetic Typography visual style in an AnimaGuru video workspace.
disable-model-invocation: true
---

# Kinetic Typography

Make typography carry the image, hierarchy and movement. This style works with Explainer, Advertisement and General Video briefs; the user's subject, audience and message determine the story.

## Establish the direction

Follow the sibling `animaguru-video` skill's category → style → quick interview flow before a new production. Reuse explicit choices and completed briefs; honor a request to skip the interview. Share [the style preview](https://animaguru.com/animation-styles#kinetic-typography). Include these unanswered visual questions in the shared interview:

- Should motion follow an existing voice recording, newly generated narration, music, or silent reading?
- Which typeface, brand colors and level of energy should lead the film? Which words deserve emphasis?
- Should the composition feel editorial and restrained, bold and poster-like, or playful and expressive?

## Design and build

- Read the installed `pixijs` router and text skill. Keep words as editable text, with locally bundled licensed fonts and glyph coverage for each language. Wait for fonts before measuring or capturing.
- Group copy into readable phrases. Choose a few distinct emphasis levels through weight, scale, color or placement. Let key words hold long enough to read; do not make every word compete for attention.
- Use a consistent motion vocabulary: masked phrase reveals, aligned slides, tracking changes, scale emphasis, and layout changes that preserve a visual anchor. Select techniques to suit the brief rather than applying every effect.
- Measure final text and wrap by language and output dimensions. Store each phrase's final layout before animating it. Avoid animating font size and rebuilding text textures every frame; transform containers or individual prebuilt glyphs instead. Preserve kerning and joined scripts when splitting text.
- If recorded speech exists, obtain and verify phrase/word timings from the actual recording. A transcript or TTS text alone does not provide alignment. Save cue times with text, language and audio source in `production/`; flag estimated timing until checked by listening.
- If speech does not exist, choose deliberate reading holds or musical beats. Do not imply word-level audio synchronization for silent or unaligned material.
- Use AnimaGuru for authorized speech, music or supporting texture assets when helpful; read its sibling skill and current catalog first. Typography and geometric accents can be authored directly.
- Evaluate animation from absolute film time. A backwards seek must restore the same word visibility, emphasis and layout as linear playback. Track phrases and accents in `src/film-resources.ts`.

## Review and completion

Follow `animaguru-video` for the player, records, audio mix and exports. Check longest phrases, transitions, multilingual glyphs, contrast and phone-size legibility. For speech-led word highlighting, target alignment within two output frames and verify against the recording; report any remaining timing uncertainty. Inspect phrase entrances, reading holds and exits, not only attractive stills. Deliver the agreed film with editable localized copy, verified cues and the working HTML5 player; export MP4 when requested.

## Additional visual treatments

Read [the material and motion variants](references/variants.md) when the brief calls for a specialized treatment. Choose the relevant recipe without imposing its example story.
