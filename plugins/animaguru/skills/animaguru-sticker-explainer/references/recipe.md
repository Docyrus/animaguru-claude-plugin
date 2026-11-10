# Sticker Explainer production recipe

The workspace includes an executable original study in `src/studies/scenes.ts`, selected with `sticker-explainer`. Its drawing commands are consumed by `src/studies/pixi-renderer.ts`; geometry and time sampling are shared with the gallery renderer. All copy lives in `shared/locales/en/style-studies.json`.

In an untouched starter, run `npm run example -- sticker-explainer`, then `npm run dev`. The command refuses to replace an authored film, retains starter backups in `production/example-backup/`, and writes an 8-second study with its own resource tracks. `npm run export:mp4` uses this installed film normally. To use the recipe inside an existing film, import `studyFrame()` and `StudyRenderer`, then compose the selected scene into the project's timeline instead of running the installer.

## Photos, data and sources

The user's own product shots, photos and data come first. Otherwise: Wikimedia Commons (read the licence on each file page: CC0, public domain or CC BY are fine; not CC BY-SA, "no known restrictions" or unclear licences), U.S. federal agencies (NASA, NOAA, USDA, USGS: works of federal employees are public domain), Openverse results filtered to CC0 or public domain, and official statistics from the publishing agency's own site. Download into the film's `public/` or `production/` folders, log every request, record each photo in `production/CREDITS.md` and each figure, with its source or arithmetic, in `production/FACTS.md`. When the brief allows generated cut-outs for generic objects, generate them on a plain background so the cut-out is clean, and list them in `CREDITS.md` as generated.

## Adaptation decisions

- Build the board as one `Container` holding every region; the camera is that container's position and scale, computed each frame from a table of shots (centre and zoom) and absolute time. Interpolate zoom in log space and multiply it by a `1 − k·sin(πu)` dip during a move so both regions stay in view. Keep the subtitle pill, chapter tag and honesty labels in a separate screen-space container above the board.
- Make each sticker texture once at load: cut the subject out (or use the photo's alpha), dilate its silhouette by a distance pass to a uniform 8–12 px margin at delivery scale, fill the margin white and render it to a `RenderTexture` with `renderer.generateTexture`. Draw the shadow as a second, blurred sprite underneath, offset down-right. Never use a live outline filter: its width would scale with the camera.
- Animate the slap on the sticker's own container (scale, rotation, alpha) and the shadow's offset and opacity separately; the board thump is a brief extra factor on the camera zoom.
- Draw charts with `Graphics` from one data model and redraw only while values change; set counters in per-digit `Text` or `BitmapText` cells so they never jitter, and finish on the exact formatted value.
- Draw threads and route lines as polylines truncated by arc length (`strokePoints` in `src/studies/timing.ts`) so they grow along the camera's path; a dashed line is a sequence of short segments.

The study is silent, original procedural art with illustrative values, labelled as such; it demonstrates the board, sticker, camera and chart system, not a real subject. Replace its stand-ins with the user's photos and sourced figures described above. The gallery preview renders its "photo" stickers procedurally (shaded height fields of a cup, beans, a coffee branch and a jute sack) with rounded, approximate figures, and says so on screen. Configure the subject, palette, scene sequence, duration and soundtrack from the brief.

Use `src/studies/timing.ts` for deterministic easing, seeded variation, measured stroke truncation and cue helpers. `window.animaguru.texts` exposes visible study text bounds for `npm run review`; text declarations alone do not count as visual proof. Inspect the actual frames as well.

## Sources and attribution

Inspired by the following pinned reference, which describes the PaperClip-style knowledge-video format; no code, footage, music or assets from it are bundled. New study art and scene geometry are original. The workspace's `VIDEO-STYLE-NOTICES.txt` preserves the repository notices and clarifies third-party asset scope.

- [prompts/19-paperclip.md](https://github.com/Vincentwei1021/mg-styles-15/blob/49052d80bfaf9fa8412cc9710530e5e95a3b8d8c/prompts/19-paperclip.md)
