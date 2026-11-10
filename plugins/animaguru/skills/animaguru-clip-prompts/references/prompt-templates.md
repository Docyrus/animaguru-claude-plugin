# Clip prompt templates

Fill every bracket from the shot plan and delete what doesn't apply. Each sentence should describe something the viewer will see or hear; cut adjectives that don't. Keep a recurring character's wording identical in every request of the film.

## Setting still

An image request (`--type image --aspect-ratio 16:9` or `9:16`), generated empty so the character can be placed later.

```text
Photograph of [place] at [time of day], [weather], with no people in it. [Main light source] from [direction], [hard or soft], [colour temperature], casting shadows [where they fall]; [secondary light, such as a warm desk lamp or a screen glow]. [Layout: what is in the foreground, middle and back, and where the character will stand or sit, left clear.] Lived-in, specific details: [three or four props with their materials and wear, such as a chipped enamel mug beside a coffee ring, a curtain hung slightly short, a fridge door crowded with takeaway menus]. [Palette.] Shot at eye level on a full-frame camera with a [24–35] mm lens, true-to-life colour, natural exposure with shadows that fall off into darkness. Slightly untidy and unstaged, not a showroom. No people, no text, no logos, no watermark.
```

## Character sheet

An image request at `--aspect-ratio 16:9`. It becomes the reference for every keyframe and shot of this character.

```text
A true-to-life photographic character sheet of ONE completely original [woman / man / person], not resembling any real or famous person, in their [age range], with a [height and build]. [Skin tone] skin with unretouched texture: visible pores, fine vellus hair, slight unevenness in tone and [small natural marks, such as freckles, a faint scar, under-eye shadows]. [Face shape], [cheekbones], [nose], [lips and natural lip colour], [brows], with subtle natural asymmetry. Their expression is [expression and mood], looking straight into the camera with [attitude].

Their most recognizable feature is [usually the hair: length, colour, texture, style, parting, and how neat or untidy it is]. They wear [accessory 1 with its material and details], [accessory 2] and [accessory 3].

They wear [top: fit, colour or pattern, fabric, neckline, sleeves, length, construction details], with [bottoms: rise, cut, colour, fabric or wash, closures, pockets, how they fall at the hem] and [shoes: style, colour, material], with no visible branding. The clothes show natural creases and light wear.

They look [three or four words for the vibe], and unmistakably human.

LAYOUT: ONE 16:9 landscape image showing TWO views of the EXACT SAME person.
LEFT: a large frontal close-up of the whole face, showing the skin texture, [the signature feature], [each accessory visible at this framing] and [the neckline or upper details of the top].
RIGHT: a complete head-to-toe photograph of the same person with the identical face, [signature feature], [every accessory], [top], [bottoms] and [shoes], standing naturally upright with arms relaxed at their sides and both feet fully in frame.

Both views on a seamless pure white (#FFFFFF) studio background. Documentary-style studio photography on a full-frame camera with an 85 mm lens, soft daylight-balanced softbox light with gentle shadows, true-to-life colour. No retouching, no airbrushing, no beauty filter, no skin smoothing. Accurate fabric detail on [the main fabrics, such as cotton jersey with a visible knit, denim with twill weave and topstitching], realistic highlights on [any metal or jewellery], natural anatomy, accurate adult proportions, realistic hands. No [everything they are not wearing, such as a bag, hat, rings, bracelets, watch], no text, no logos, no other people, no watermark, no CGI or illustrated look.
```

## Keyframe

An image request with `--references SETTING_SHA,SHEET_SHA` at the clip's aspect ratio, when a shot must open on an exact composition.

```text
The [person] from Image 2, with the same face, hair, clothing and accessories, [pose and action at the first moment of the shot] in the [place] from Image 1, keeping its furniture, props and light. [Shot size and camera height.] [Where they are in the frame and what they hold.] Light falls on them exactly as in Image 1: [source and direction]. Not the white background or the two-view layout of Image 2. Hyper-realistic photograph, true-to-life skin and fabric, no retouching. No text, no logos, no other people.
```

## Video prompt

The prompt text, then the request settings and the CHECK list, which stay out of the prompt. Dialogue goes in `{ }`, sound effects in `< >` and music in `( )`, so each channel is unmistakable.

```text
Duration: [X] seconds.

Audio: [Every sound channel. Dialogue in { } with its language and delivery; sound effects in < >; music in ( ), or "No background music". "No subtitles" unless subtitles are wanted.]

Context: [Reference roles first, if the request has references: "Image 1 is the setting: keep … . Image 2 is the character sheet: take … , not its white background or two-view layout. Audio 1 is [her / his / their] line, spoken in sync."] [The subject: an original adult, age range, build, skin, face, hair, clothing with exact colours, fabrics and fit, worded as in every other shot.] [What they are doing and where: the place, time of day, weather, the light source and its direction, the key props and where they are.] [The look: hyper-realistic live-action footage shot on a cinema camera with natural lens character, true-to-life colour, natural skin texture with visible pores and small imperfections, realistic fabric movement, accurate physics and anatomy, realistic hands, subtle natural film grain, no beauty filter, no CGI, no illustrated or plastic look.]

Movement & Editing:
0–[X]s: [Shot size and camera position or move (static, slow push-in, handheld follow, pan, tilt, orbit), what the subject does step by step and how objects respond, visible changes of expression, and what the frame looks like at the end of the segment.]
[X]–[Y]s: [A cut or the same continuous take, stated; the next action; its end state.]
[Y]–[Z]s: [The final beat, ending on a clear, settled frame.]
Keep [identity, headcount, clothing, props and lighting] consistent throughout. No text, no logos, no watermarks, no additional people.
```

```text
REQUEST (outside the prompt)
workflow: [reference-to-video / image-to-video / text-to-video / lip-sync] | model: [studio default, or one from the live catalog]
references: [Image 1 = setting SHA, Image 2 = sheet SHA] | audioReferences: [Audio 1 = line SHA] | reference: [keyframe SHA, or none]
seconds: [X] | aspectRatio: [16:9 / 9:16, where the workflow takes one] | resolution: [the highest the profile and budget allow]

CHECK
[Two to four things to watch in this take, each with its first fix: identity between cuts, headcount, hands and contact, the mouth on a named word, music or subtitles creeping in, the timing of the key action.]
```

### Worked example

A single 8-second take for a reference-to-video request with a setting still, a character sheet and a recorded line.

```text
Duration: 8 seconds.

Audio: {English, tired but warm, a small laugh at the end: "You said it wouldn't rain."} <steady rain on the window, a fridge hum, a ceramic mug set down on a wooden counter at 5 s>. No background music. No subtitles.

Context: Image 1 is the setting: keep the narrow kitchen, the rain-streaked window, the warm under-cabinet light and the cold blue streetlight. Image 2 is the character sheet: take her face, hair, clothing and the silver ear cuff, not its white background or two-view layout. Audio 1 is her line, spoken in sync from 1 s. She is an original woman in her early 30s, average height, light olive skin with visible pores and faint under-eye shadows, a slightly crooked nose, shoulder-length dark brown hair slipping out of a low clip, in an oversized faded charcoal cotton sweatshirt with the cuffs pushed up and grey cotton joggers. Late at night she leans on the counter by the window, holding a white enamel mug with a chipped rim in both hands. The under-cabinet light lights her face warmly from below left; blue streetlight through the rain falls across her shoulder from the window at frame right. Hyper-realistic live-action footage shot on a cinema camera with natural lens character, true-to-life colour, natural skin texture with visible pores and small imperfections, realistic fabric movement, accurate physics and anatomy, realistic hands, subtle natural film grain, no beauty filter, no CGI, no illustrated or plastic look.

Movement & Editing:
0–1s: Static medium close-up from across the counter at chest height. She looks out of the window, the mug at chin height, a thin wisp of steam rising.
1–4s: The same take, with a very slow push-in. She turns her head to the camera and says the line; her eyebrows lift on "rain" and one corner of her mouth goes up.
4–6s: The same take. She lowers the mug by its handle and sets it on the counter; it lands with a small knock and the coffee inside sways, then settles.
6–8s: The same take. She laughs once through her nose and holds a tired smile at the camera, the frame settled on her face and the mug.
Keep her face, hair, clothes, the single mug and the two-colour lighting consistent throughout. No text, no logos, no watermarks, no additional people.
```

```text
REQUEST (outside the prompt)
workflow: reference-to-video | model: studio default
references: Image 1 = kitchen setting SHA, Image 2 = character sheet SHA | audioReferences: Audio 1 = line SHA
seconds: 8 | resolution: 720p

CHECK
- Her face at the head turn (1–2 s); if it drifts, shorten the turn or open on a keyframe.
- Her fingers on the handle as the mug goes down (4–6 s); if they pass through it, describe the grip.
- The mouth on "rain"; if it misses, lip-sync from a keyframe with the recorded line.
- Music under the rain; if it appears, mute the clip and lay the line, rain and knock in the edit.
```

## Stylized look

For an animated clip, replace the look sentence in Context with the selected style's material, taken from its style skill:

```text
[Style] animation: [the style's material, such as matte cardstock cutouts with visible fibres and slightly irregular scissor edges], one light from [direction] casting [shadow quality], [palette]. Motion follows the material: [such as paper turning only at pinned joints, sliding and stacking, never stretching]. Consistent with Image 2's character design. No photoreal textures, no 3D render look, no lettering, no logos.
```

## Sound effects

Sound effect requests (`--type sfx`) in plain physical language: one sound, its material, distance, room and length.

- "A white enamel mug set down on a wooden counter, one soft knock, close, in a small dry kitchen" with `--seconds 1`.
- "Steady rain against a kitchen window at night, distant traffic, a low fridge hum" with `--seconds 30 --loop` for a bed under the scene.
- "Footsteps in leather shoes on wet pavement, unhurried, passing from left to right" with `--seconds` matched to the walk.

Raise `--prompt-influence` (0–1, default 0.3) when the result drifts from the description; lower it for a looser, more natural variation.
