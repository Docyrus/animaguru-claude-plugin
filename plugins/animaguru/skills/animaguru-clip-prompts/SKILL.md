---
name: animaguru-clip-prompts
description: Plan, reference and prompt AI video clips made with AnimaGuru so they look directed and real rather than generated, and come right in the first few takes. Covers the shot plan, a setting still, a character sheet, dialogue recorded before the clip, the timed video prompt, sound effects, review and finishing. Use before writing any video generation request (assets generate --type video, or generate_asset with MCP), especially for live-action footage, people, dialogue or a hyper-realistic look, and when a clip looks fake, drifts between shots or keeps needing retakes.
---

# AnimaGuru clip prompts

A generated clip looks fake where the model had to guess. Light left unspecified comes out even and sourceless, an unspecified room comes out tidy and anonymous, an unspecified face comes out symmetrical and retouched, a vague action makes props float and hands pass through things, and sound left to the model rarely suits the character. Take the guesses away before spending credits: decide the details, lock them in cheap stills and a recorded line, then write one timed prompt per shot that says what each reference is for.

This skill is the prompt and reference layer. Sibling `animaguru` covers models, flags, credit authorization, jobs and downloads; `animaguru-video` covers the film workspace. Read the live catalog and the project's `videoProfiles` before choosing a workflow: models, durations and options change without a CLI release.

## Where clips give themselves away

| Tell | What the model guessed | Put in the prompt or the references |
| --- | --- | --- |
| Lighting | Even light from nowhere; shadows and reflections that disagree | The source, its direction, colour and the time of day: "low afternoon sun through half-closed blinds, from frame left". A setting still that shows it. |
| Setting | A clean showroom nobody lives in | Three or four specific, slightly imperfect details that belong to this story: a coffee ring on the desk, a curtain hung a little short, photos this person chose. |
| Character | Symmetrical features, flawless skin, styled hair | Age, build, skin with pores and small marks, asymmetry, hair a little out of place, clothes with creases and wear. A character sheet. |
| Physics | Floating props, hands through objects, effects without causes | One action per shot, step by step, with how each object responds: "she lifts the mug by its handle, the coffee sways, she sets it down and it knocks on the wood". |
| Sound | A voice that doesn't fit, music nobody asked for, mistimed effects | Every sound channel named: the line with its language and delivery, the effects, "No background music", "No subtitles". The dialogue recorded first and passed as a reference. |
| Finish | Raw, flat shots that don't match | A finishing pass: exposure, white balance and saturation, shots matched, then subtle grain or a look. Fix generation errors first; grading can't repair broken physics or a face that changes. |

The same tells apply to animated styles, where "real" means true to the style's own material. See [Animated and stylized clips](#animated-and-stylized-clips).

## The workflow

Spend in order of cost: decisions are free, stills and speech are cheap, and video is the expensive step, so it should be the last place anything is guessed. Dry-run every request (`--dry-run`, or `dry_run: true` with MCP) and add up the estimates, including the retakes you expect, before the first paid submission. A request to make the clip authorizes a proportionate attempt within any stated budget, as sibling `animaguru` describes.

### 1. Plan the details

Write a short shot plan before any request: `production/clips/SHOT.md` in a film workspace, or beside the user's other production notes elsewhere. Take what the brief already says and ask only about gaps that change the result.

- **Beat:** what happens, why, and the frame it ends on.
- **Character:** age range, build, skin, face, hair, wardrobe with colours, fabrics and fit, accessories, what they are *not* wearing, how they move and speak.
- **Setting:** place, time of day, weather, the light source and its direction, the specific props and where they sit.
- **Sound:** the exact line and its delivery, the effects, the ambience, and whether music belongs in the clip at all.
- **Format:** aspect ratio, how long the line runs, and the shot list, one clear action per shot.

### 2. Build the setting

Generate the empty, lit setting as an image at the clip's aspect ratio (`--aspect-ratio 16:9` or `9:16`): the place, its light and the props from the plan, with room for the character. Use [the setting template](references/prompt-templates.md#setting-still). Look at it before going on: a still is the cheapest place to fix the light.

### 3. Cast the character

Generate a character sheet once: one 16:9 image with a frontal close-up and a full-body view of the same original person on pure white, shot as unretouched studio photography. Use [the character sheet template](references/prompt-templates.md#character-sheet), fill every bracket from the plan, and list what the character does not wear so the model doesn't add it. Check the face, hands, accessories and fabric before using the sheet anywhere.

For an exact first frame, put the character in the setting with an image keyframe: `--references SETTING_SHA,SHEET_SHA`, saying what to take from Image 1 and from Image 2. Generate it at the clip's final aspect ratio, since image-to-video keeps the image's shape.

Cast only original people. Never use a photo of a real person, a celebrity lookalike or a named public figure as a generated character. A real person who agreed to appear belongs in the HeyGen avatar workflow, which sibling `animaguru` covers, with their recorded consent. Seedance refuses images of real people's faces; if it refuses a photoreal sheet, use MiniMax H3 Max or HeyGen Video 1 with the same references.

### 4. Record the lines first

Generate each line of dialogue as speech before its clip (`--type speech`, on the studio's default speech model unless the user names one) in a voice that fits the character. For ElevenLabs, pass a voice ID with `--voice` and put audio tags in the transcript, such as `[tired] You said it wouldn't rain. [laughs softly]`; `catalog --type speech` lists voices. Download the line and measure it with `ffprobe`: its length sets the clip's `--seconds` and the timings in the prompt. One line per shot keeps the mouth and the timing manageable.

### 5. Choose the route

Choose from the selected model's `videoProfiles`, among the models both the catalog and the project's `availableModels` list:

| The shot needs | Route |
| --- | --- |
| The same character across several shots, framing left to the model | `--workflow reference-to-video` with `--references SETTING_SHA,SHEET_SHA`, plus `--audio-references LINE_SHA` for dialogue. Seedance 2.5, MiniMax H3 Max and HeyGen Video 1 take images and audio this way. |
| An exact opening composition, or continuity with the previous shot | The keyframe from step 3, then `image-to-video` with `--reference KEYFRAME_SHA`; or H3 Max `reference-to-video`, which can open on `--reference` and keep the sheet in `--references`. |
| A talking close-up where the mouth must match the line | H3 Max `lip-sync`: the face in a keyframe (`--reference`) speaks the recorded line (`--soundtrack`, 5 seconds or longer, `--transcribe` helps). It takes no prompt, so the still sets the framing. Or a reference-to-video shot with Audio 1, then check the mouth. |
| No people and no exact frame | `text-to-video`, with the same Context and Movement detail. |

Keep `--seconds` to the line plus a beat either side; one action per shot comes out right more often than a long take with three. A fully written prompt needs no rewriting: on H3, `--prompt-expansion disabled` sends your words as they are. FLUX always reasons about the prompt, and HeyGen Video needs expansion past 15 seconds; read the asset's expanded prompt to see what changed. Seedance takes no expansion setting.

### 6. Write the video prompt

Use [the video prompt template](references/prompt-templates.md#video-prompt): Duration, Audio, Context, then timed Movement & Editing ending on a settled frame, then the consistency line. Name each reference by its role at the start of Context: "Image 1 is the setting: keep the room, its furniture and the light from the window. Image 2 is the character sheet: take her face, hair, clothing and accessories, not its white background or its two-view layout. Audio 1 is her line." Repeat the character's description word for word in every shot of the film.

Settings belong in the request, not the prompt: model, workflow, the order of the references (which fixes Image 1, Image 2, Audio 1), `seconds`, `aspectRatio` where the workflow takes one, and `resolution`, the highest the profile and budget allow for the final take. Save each shot as a one-item batch file, so the long prompt lives in JSON rather than in a shell argument:

```sh
# production/generation/kitchen-line.json:
# {"assets": [{"name": "kitchen-line", "type": "video", "workflow": "reference-to-video",
#   "references": ["SETTING_SHA", "SHEET_SHA"], "audioReferences": ["LINE_SHA"],
#   "seconds": 8, "resolution": "720p", "prompt": "Duration: 8 seconds. …"}]}
animaguru assets batch PROJECT_ID --file production/generation/kitchen-line.json --dry-run
```

Add `model` only when the user asks for one or the route needs a model the studio default isn't. With MCP, pass the same fields to `generate_asset`. Write the CHECK list from the template into the shot plan before submitting.

### 7. Add the sound

Search the asset library before generating common effects (`animaguru library search DESCRIPTION --type sfx`; importing is free). Generate the rest with `--type sfx`: one sound per asset, described physically, with `--seconds` sized to the action and `--loop` for an ambience bed ([examples](references/prompt-templates.md#sound-effects)). Place each effect at its frame in the edit rather than asking the video model for it, and keep the clip's own sound only where it is right.

### 8. Finish

Treat the take as footage that still needs a final pass: see [Finishing](#finishing).

## Review the take

Watch the clip with sound first, then look at the opening, the key action, every cut and the last frame at full size. Go through the shot plan's CHECK list, then:

| Symptom | First fix |
| --- | --- |
| The face or clothes change between cuts | Reference-to-video with the sheet; fewer cuts per clip; the same character wording in every shot. |
| An extra person, or the headcount changes | State the headcount in Context and "no additional people"; shorten the shot. |
| Hands, props or contact go wrong | Describe the grip and how the object responds, step by step; one action per shot; keep hands out of fast moves. |
| The mouth misses the line | H3 Max lip-sync from a keyframe of the face with the recorded line, or a shorter line with Audio 1. |
| Music, subtitles or lettering appear | "No background music", "No subtitles", "No text" in the prompt; mute the clip and use your own tracks. |
| The key action lands at the wrong moment | Give it its own timed segment; trim in the edit before regenerating. |
| Plastic skin, perfect hair, a showroom set | Add the imperfections to the sheet, the setting and Context, and check the sheet itself isn't retouched. |
| Flat or mismatched colour | Fix it in the finishing pass, not with another take. |

Change one thing per retake and write down what changed. Before paying for another take, see whether the edit can fix it: trim, crop, reorder, replace the audio, grade. When a clip is mostly right, change only the broken part with the targeted workflows its model's profile offers (`extend-video`, `insert-video`, `relight`, `lip-sync`) rather than regenerating the whole shot. After an uncertain response, check jobs and saved assets before submitting again.

## Finishing

In a film workspace the clip is one layer of the Pixi film (sibling `animaguru-video`). Map film time to the clip's own time with `mediaTime()` and `seekVideo()` from `src/studies/media.ts`, never with the video's own clock.

- **Correct first:** exposure, white balance and saturation with a `ColorMatrixFilter` on the clip's sprite (`pixijs-filters`), then match neighbouring shots to each other.
- **Then the look, if it suits the brief:** subtle grain from a `NoiseFilter` whose `seed` is set from film time, so review and export see the same frame, and a soft vignette from the kit's `vignetteTexture()`.
- **Sound:** register the dialogue, effects and ambience in `src/film-resources.ts` at their times and mix with `npm run audio:mix`.

For a standalone clip, ffmpeg does the same pass: `eq` and `colorbalance` to correct, `lut3d=FILE.cube` for a LUT the user owns or supplied, `noise` for grain, `vignette`, then the audio mix. Keep the untouched download and the exact commands.

Describe the result as generated footage, finished in the edit. Don't present it as a recording of a real event, place or person.

## Animated and stylized clips

Most AnimaGuru films are animated. Keep the same plan, references and prompt structure, and swap the look:

- Replace the live-action look in Context with the selected style's material from its style skill (paper, ink, clay, pixel art, toy 3D), and leave out camera bodies, pores and film grain. The template has [a stylized look line](references/prompt-templates.md#stylized-look).
- Draw the character sheet in the style, still on plain white, still face and full body, still listing what they don't wear.
- Keep the rules on light, set, physics and sound: one light direction, a set made for this story rather than a stock background, motion the material allows (paper bends at its joints, clay squashes), sound placed in the edit.
- Exact text, logos and numbers stay out of generated pixels and go in the composition.

## Records

Keep each shot's plan, prompt, request file, estimate, job ID, asset IDs, file SHAs, CHECK list and what changed between takes in `production/clips/` and `production/generation/` (or beside the clip outside a workspace), so a retake changes one thing and never repeats paid work by accident.
