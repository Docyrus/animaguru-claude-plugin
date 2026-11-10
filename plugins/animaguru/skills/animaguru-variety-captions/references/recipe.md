# Variety Captions production recipe

The workspace includes an executable original study in `src/studies/scenes.ts`, selected with `variety-captions`. Its drawing commands are consumed by `src/studies/pixi-renderer.ts`; geometry and time sampling are shared with the gallery renderer. All copy lives in `shared/locales/en/style-studies.json`.

In an untouched starter, run `npm run example -- variety-captions`, then `npm run dev`. The command refuses to replace an authored film, retains starter backups in `production/example-backup/`, and writes an 8-second study with its own resource tracks. `npm run export:html` and `npm run export:mp4` use this installed film normally. To use the recipe inside an existing film, import `studyFrame()` and `StudyRenderer`, then compose the selected scene into the project's timeline instead of running the installer.

## Footage, fonts and sound

The user's own clip comes first. Otherwise: Wikimedia Commons (CC0 or public domain; read each file page, and not CC BY-SA or "no known restrictions"), Pexels or Pixabay only under a licence the user accepts, and the Internet Archive for public-domain material. Fonts come from Google Fonts or the foundry under the SIL Open Font License, bundled in `public/` with the licence text. Comedy sound effects (boing, pop, ding, slide whistle, record scratch) are generated or taken from CC0 libraries such as Freesound's CC0 filter. Record every asset's source, author and licence in `production/CREDITS.md`, and write a cue sheet in `production/` listing each gag beat and the caption that answers it.

## Adaptation decisions

- Build each caption line from prebuilt per-glyph `Text` objects measured after the fonts load, in four sibling containers (shadow, outer outline, white outline, fill) so every outline sits under every fill. Animate the glyph containers' position, rotation and scale, never the font size, and use a `FillGradient` with a hard stop for the gloss.
- Draw the burst frame, the converging speed lines, sweat drops and sparkles as `Graphics`, reseeded from the frame index every two frames so the hand-drawn flicker repeats exactly on seeks.
- Make the freeze by holding the footage at its source time (a still captured to a `RenderTexture` for video), push in with a container transform, and run the white flash and the shake on the same footage container, so captions stay locked above the picture.
- Prepare the rubber stamp once as an ink-worn `Sprite` texture and slam it with a scale tween and a short shake of the footage container.

The study is silent, original procedural art: a flat stand-in cat, mug and counter, labelled as illustrative footage. It demonstrates the caption layers, timing and reaction graphics, not a finished episode; replace its stand-ins with the user's footage. The gallery preview uses a procedurally rendered stand-in cat and kitchen, labelled as not real footage, to show the system at full finish. Configure the subject, palette, scene sequence, duration and soundtrack from the brief.

Use `src/studies/timing.ts` for deterministic easing, seeded variation, measured stroke truncation and cue helpers. `window.animaguru.texts` exposes visible study text bounds for `npm run review`; text declarations alone do not count as visual proof. Inspect the actual frames as well.

## Sources and attribution

Inspired by the following pinned references; no source code, fonts, footage or audio from them is bundled. New study art and scene geometry are original. The workspace's `VIDEO-STYLE-NOTICES.txt` preserves the repository notices and clarifies third-party asset scope.

- [prompts/18-hanazi.md](https://github.com/Vincentwei1021/mg-styles-15/blob/49052d80bfaf9fa8412cc9710530e5e95a3b8d8c/prompts/18-hanazi.md)
- [demos/18-hanazi/index.html](https://github.com/Vincentwei1021/mg-styles-15/blob/49052d80bfaf9fa8412cc9710530e5e95a3b8d8c/demos/18-hanazi/index.html)
