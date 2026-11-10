# Sports Telestrator production recipe

The workspace includes an executable original study in `src/studies/scenes.ts`, selected with `telestrator`. Its drawing commands are consumed by `src/studies/pixi-renderer.ts`; geometry and time sampling are shared with the gallery renderer. All copy lives in `shared/locales/en/style-studies.json`.

In an untouched starter, run `npm run example -- telestrator`, then `npm run dev`. The command refuses to replace an authored film, retains starter backups in `production/example-backup/`, and writes an 8-second study with its own resource tracks. `npm run export:html` and `npm run export:mp4` use this installed film normally. To use the recipe inside an existing film, import `studyFrame()` and `StudyRenderer`, then compose the selected scene into the project's timeline instead of running the installer.

## Evidence and sources

Wikimedia Commons (many clips are cut from broadcasters' own YouTube uploads under CC BY; read the licence on each file page; not CC BY-SA or "no known restrictions"), a broadcaster's or club's own verified YouTube channel when its video page states a Creative Commons Attribution licence (save the evidence: channel id, verification, licence field, date checked; never a re-upload or fan mirror), the league's or broadcaster's own match page for facts (scores, minutes, how a goal was scored), and Commons photographs (CC BY/CC0) for player portraits. Download the native resolution, never an "AI-upscaled" stream; record each asset in `production/CREDITS.md` and every counted number and its measurement method in `production/FACTS.md`.

## Adaptation decisions

- Track reference points (feet, ball) as hand-authored keyframes in source-pixel coordinates, interpolated the same way across slow motion and freezes; check them against full-resolution crops, never a scaled contact sheet.
- Use a `PerspectiveMesh`, or a small custom shader doing the equivalent projection, for the flatten into a top-down board; drive both the broadcast overlay and the board positions from the same homography point set.
- Build the freeze entry (white flash, punch-in, desaturate, spotlight) as one small filter and transform chain applied uniformly to every freeze, so overlays drawn afterward inherit the same transform and never slide off the players.

The study is silent, original procedural art with illustrative values, labelled as such; it demonstrates material, layout and motion, not evidence. Replace its stand-ins with the real match footage described above, never with generated imagery. The gallery preview uses an illustrative match with no real footage or team behind it, labelled as such. Configure the subject, palette, scene sequence, duration and soundtrack from the brief.

Use `src/studies/timing.ts` for deterministic easing, seeded variation, measured stroke truncation and cue helpers. `window.animaguru.texts` exposes visible study text bounds for `npm run review`; text declarations alone do not count as visual proof. Inspect the actual frames as well.

## Sources and attribution

Inspired by the following pinned references; source-specific 3D/media dependencies are not bundled. New study art and scene geometry are original. The workspace's `VIDEO-STYLE-NOTICES.txt` preserves the repository notices and clarifies third-party asset scope.

- [styles/telestrator/STYLE.md](https://github.com/lemomo-ai/lemo-opuscar/blob/77ee8318df779b0736d7de0abe24387e51023735/styles/telestrator/STYLE.md)
- [styles/telestrator/demo/index.html](https://github.com/lemomo-ai/lemo-opuscar/blob/77ee8318df779b0736d7de0abe24387e51023735/styles/telestrator/demo/index.html)
