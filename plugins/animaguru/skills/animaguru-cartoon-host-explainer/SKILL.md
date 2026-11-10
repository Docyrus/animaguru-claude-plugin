---
name: animaguru-cartoon-host-explainer
description: Build Cartoon Host Explainer visuals and motion in an AnimaGuru PixiJS video workspace. Use when this visual style is chosen for an explainer, advertisement or general video.
disable-model-invocation: true
---

# Cartoon Host Explainer

The talking-host explainer reel: a drawn presenter, cropped at the chest in the lower right, talks the whole time while the screen spells out what they say. Captions appear word by word as they are spoken, a condensed two-word title slams in on its word with a red swash underline, and white cards with halftone shadows show each point and then act out its explanation. It is a 30–60 second vertical reel by default and reads like a curious friend explaining something, not like an ad. Subject, audience, emotional tone and story come from the user's brief. This style supports Explainer, Advertisement and General Video.

## Establish direction

Follow sibling `animaguru-video` for purpose → style → compact interview before new production. Reuse explicit choices and completed briefs; honor a requested interview skip. Share [the style gallery](https://animaguru.com/animation-styles#cartoon-host-explainer). Fold missing questions into the shared interview:

- What is the topic, and what must the film mention (a product, an offer, a link)?
- Who is the host: a drawn version of the user (from a photo they supply), the brand's mascot, or a new character? Name, look and colours.
- Whose voice: the user's own recording, or a generated voice?
- Where will it run: 9:16 for Reels, Shorts and TikTok (the default), or 16:9?

Then write the script yourself and show it before anything is recorded: a two-line hook (line 1 states the problem in under six words, line 2 promises the payoff), three to seven points, and one closing line that pays the hook off. Revise until the user approves it.

## Keep the host original

Design the host for this brief. Never copy another creator's presenter, mascot or signature look, and never draw a real person other than the user without that person's agreement. When the host is the user, work from their own photo and say so in the production notes. A statistic, review or result shown on a card comes from the user or a cited source in `production/FACTS.md`; invented examples say so on screen.

## Build the look and movement

Read `pixijs` and the relevant Container, Graphics, Text, Sprite and Ticker skills. Read `animaguru` before generating assets; discover current models and estimates, respect the user's budget, and reuse completed media. Captions, titles, labels, counters and card text stay authored canvas content, never baked into a picture.

Sizes below are for 1080 × 1920; scale them with the frame.

- **Paper and colour.** Warm cream paper (#EBE7E1) with fine grain, ink #1E1C1A, red #D7372C, grey #8A857E. Cards are #FBFAF8 with a 3 px ink border, 20 px corners and a halftone shadow: 1.7 px ink dots on an 8 px grid, offset 13 px left and 12 px down. The host's clothes can follow the brand; the furniture stays paper, ink and red.
- **Type.** Captions in Instrument Sans 500 at 62 px, top left (x 120, y 196, 850 px wide). One key word per line in Instrument Serif italic at 1.16× size, in red. Titles in Anton up to 176 px, first word ink and second red, with a hand-drawn red swash underline. Labels in JetBrains Mono 25 px grey at y 132: "// 01 · name" on the left, a stat on the right with its number in red bold. Stamps are Anton 52 px red in a 5 px red box, tilted −6°. All four families are under the SIL Open Font License: bundle the files and their licence in `public/fonts/` and load them with `loadFonts` from `src/kit/fonts.ts`.
- **The host.** An original cartoon bust with flat colours and 6 px dark-brown outlines, about 650 × 770 px from x 430, y 1170, built from parts: head, brows, eyelids, glasses or other features, ten mouth shapes and two hands. They never cover captions, titles or card text.
- **Never:** gradients, glow, soft drop shadows, stock photos, emoji, full stops in on-screen text, or any second where nothing moves.

**Structure.** The hook's line 1 brings a UI card showing the problem and a red strike-through draws across it; line 2 pops small cards in 0.16 s apart and draws a red ring around the payoff. A halftone wipe runs 0.3 s before point one and again before the last point. Each point: the label updates, the title slams in on its spoken word, the underline draws 0.12 s later, the main card rises 0.18 s after that with a number counting up over 1.15 s, a red #N badge spins in about 0.6 s later, and a terminal or search bar types one line in under 0.9 s. 0.3 s before the explanation everything exits upward and a demo acts out exactly what the voice says, with one stamp landing on its key word. The closing line pays off the hook, and the last frame matches the first so the reel loops.

**Motion vocabulary.** Pop: scale 0.55 → 1 in 0.34 s with a back-out overshoot (2.2). Rise: 70 px up in 0.4 s, cubic ease-out. Exit: 50 px up and fade out in 0.22 s. Slam: scale 1.22 → 1 in 0.24 s, quartic ease-out. Stamp: scale 1.75 → 1 and −18° → −6° in 0.2 s. Wipe: a 13 × 23 grid of ink dots grows to about 62 px from the centre out, then shrinks away, 0.9 s in all.

**Voice drives everything.** Generate line 1 in three voices and let the user pick, then record the whole script at about 1.1× speed. Cut silences longer than 0.24 s down to 0.24 s, only where the voice is truly silent. Take word timestamps from the final voice track and match them to the script: every caption word, title, stamp and gesture starts on a real word's start time, never an estimate. Each caption word appears in light grey #B5AFA7 on its frame and turns ink (or red) in 0.2 s.

**The host acts.** Pick the mouth shape every frame from the voice's loudness: closed at −42 dB, wide open at −16 dB, instant attack and a 0.55-per-frame release. Blink for 0.14 s every 2.4–4.2 s on a fixed seed. Sway the head slightly all the time and nod for 0.5 s on each key word. Raise a pointing hand from below for 1.7 s at every new point, and an open palm on every other explanation.

**Sound.** One sound effect per event: a pop on cards, a whoosh on scene changes, a tick roll under counters, typing under the terminal and a thud on stamps, each placed so its loudest point lands on its frame. Music sits far under the voice (about 0.16 of its level) and fades out over 0.8 s; master around −14 to −15 LUFS.

Use the [production recipe](references/recipe.md) for the tools, the host rig, word timing, the bundled original study and port-specific decisions. It is a technique example, not a prescribed film. Keep motions a function of absolute seconds. Prepare assets locally, preserve async seeking and register actual resource/cue times. Keep essential type editable and localized.

## Review and delivery

Check that every caption word, title, stamp and gesture lands on its spoken word, that the mouth is shut in every pause and at the end, that the badge number matches the point, that no on-screen text has a full stop, that nothing holds still for over a second, that no text sits under the host or outside the safe area (`"safeArea": "reels"` keeps text clear of feed buttons and captions), and that the last frame matches the first. Before the final render, look at a frame from the start of every point. Check moving playback with sound, desktop/mobile fit and cold seeks. Follow `animaguru-video` for production records, audio mixing and MP4 delivery. Describe the actual 2D rendering method accurately.
