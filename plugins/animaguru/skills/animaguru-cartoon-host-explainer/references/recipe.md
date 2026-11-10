# Cartoon Host Explainer production recipe

The workspace includes an executable original study in `src/studies/scenes.ts`, selected with `cartoon-host-explainer`. Its drawing commands are consumed by `src/studies/pixi-renderer.ts`; geometry and time sampling are shared with the gallery renderer. All copy lives in `shared/locales/en/style-studies.json`.

In an untouched starter, run `npm run example -- cartoon-host-explainer`, then `npm run dev`. The command refuses to replace an authored film, retains starter backups in `production/example-backup/`, and writes an 8-second study with its own resource tracks. `npm run export:mp4` uses this installed film normally. To use the recipe inside an existing film, import `studyFrame()` and `StudyRenderer`, then compose the selected scene into the project's timeline instead of running the installer.

## Frame, fonts and layers

Set `film.config.json` to 1080 × 1920 at 30 fps with `"safeArea": "reels"`, and read `animaguru-video`'s `references/short-form-ad.md` for the vertical command sequence. Download Instrument Sans, Instrument Serif (italic), Anton and JetBrains Mono from Google Fonts into `public/fonts/` with their `OFL.txt`, and load them with `loadFonts` before the first frame. Stack five layers from the bottom: paper, scenes, presenter, captions, wipes. Give each point its own scene `Container` with its own timing function of absolute seconds, so a point can be moved or cut without retiming the others.

## Voice and word timing

1. Generate line 1 in three voices with `animaguru assets generate … --type speech` and let the user choose; then generate one segment per sentence in that voice (`assets batch`, see `animaguru`).
2. In `production/audio/vo.json` set `"tempo": 1.1` and `"maxPause": 0.24`, then run `npm run audio:vo`. It caps only real silences and writes `production/audio/work/vo-track.wav` and caption times in `production/audio/timing.json`.
3. Take word start times from that final track, not from the script. With the user's agreement, install faster-whisper (`pip install faster-whisper`; it runs locally and free), transcribe `vo-track.wav` with `word_timestamps=True`, match the recognised words to the script in order, and save `production/audio/words.json` as `[{ "word", "start", "end" }]`. Fix any word the matcher could not place by listening, and say so. Only if no word timestamps can be made, spread each caption's words over its `timing.json` span by length and tell the user the sync is approximate.
4. Cue everything from `words.json`: caption words, the title slam, the stamp, the badge and every gesture start on a word's `start`.

## The presenter rig

- Draw the host once as separate parts. Either generate an SVG with `animaguru assets generate … --type vector --shapes simple` (a front-facing bust on a plain background, flat colours, one outline weight) and load it as geometry with `parseAsGraphicsContext`, or draw the parts in code with `Graphics`. Keep a `Container` hierarchy: body (breathes), head (sways, nods and tilts about the neck), brows, eyelids, glasses, ten mouth shapes as children with one visible, and two arms.
- Mouth: decode `vo-track.wav` with `decodePcm` and take `peakLevels` at one hop per film frame (both in `scripts/audio-tools.mjs`). Convert each level to dB, map −42 dB to shape 0 and −16 dB to shape 9, apply an instant attack and multiply by 0.55 per frame on release, and save the shape indices as `production/audio/mouth.json`. Pick the shape from that array by frame.
- Blinks from a seeded random sequence (0.14 s every 2.4–4.2 s), head sway as sums of sines whose periods divide the film length so the loop closes, and a 0.5 s nod on every key word.
- Arms: a pose table of elbow and wrist positions, hand angle, raised fingers and thumb (down, pointing up, open palm). Draw each arm per frame as two `Graphics` strokes along shoulder → elbow → wrist, an outline stroke wider than a coloured core with round caps, so the outline stays even. Raise the pointing hand from below the frame for 1.7 s at each point and the palm on alternate explanations, snapping in about 0.25 s with an overshoot.
- Halftone: render one dot tile to a texture and fill an offset copy of a silhouette with it (a `TilingSprite` masked by the shape, or a pattern-filled `Graphics`). Cards and the host halo share the tile.

## Captions, titles, cards and wipes

- Lay each caption out once: measure every word with `CanvasTextMetrics.measureText` in its style (sans, or the red serif italic for the key word) and place one `Text` per word, so each can change colour on its frame without reflowing the line. Hidden words still hold their space. Put captions in plain lines, never in a flex layout that drops the spaces.
- The title is two `Text` objects; the swash underline is a slightly wavy `Graphics` stroke under the red word, drawn on by arc length with `strokePoints` from `src/studies/timing.ts`. Counters use fixed-width digit cells.
- Hide every element until its cue by computing visibility from time, not by setting it at frame zero, or it flashes on the first frame.
- The wipe is a 13 × 23 grid of ink circles (23 × 13 in 16:9) whose radius rises and falls with a delay proportional to each dot's distance from the centre; switch scenes at its fullest moment.

## Sound

Take effects from `animaguru library search … --type sfx` or generate them with `--type sfx`, one file per event. Find each file's loudest point with `peakLevels` and offset it so that point lands on its event frame. Run `npm run audio:mix` with `"musicDb"` set low (about −16 dB) for the voice and music, then mix the effects in with FFmpeg (`adelay` per effect, `amix`), keep them under the voice, and measure loudness again.

The study is silent, original procedural art with an invented café and illustrative figures, labelled as such; it demonstrates the furniture, word-timed captions, host rig, motions and wipe, not a real subject. Its captions use Arial Bold advance estimates because the study's node model cannot measure text; a production film measures real text. The gallery preview draws its host, Juno, entirely in code, with macOS stand-ins for the four fonts. Replace the stand-ins with the user's host, points and sourced figures described in the skill. Configure the subject, palette, beats, duration and soundtrack from the brief.

Use `src/studies/timing.ts` for deterministic easing, seeded variation, measured stroke truncation and cue helpers. `window.animaguru.texts` exposes visible study text bounds for `npm run review`; text declarations alone do not count as visual proof. Inspect the actual frames as well.

## Sources and attribution

Adapted from a free explainer-reel prompt posted on X by @finnardley on 30 October 2026 (https://x.com/finnardley/status/2116010421740007894). Its palette, type, motion timings, structure and presenter rules are restated here in our own words; its HyperFrames, Kokoro and faster-whisper toolchain is replaced by this workspace's PixiJS film, AnimaGuru speech and audio tools, with faster-whisper kept as the optional word-timing step. No footage, characters, code, fonts or audio from the post are bundled, and the host, study and preview art are original. The workspace's `VIDEO-STYLE-NOTICES.txt` clarifies third-party asset scope.
