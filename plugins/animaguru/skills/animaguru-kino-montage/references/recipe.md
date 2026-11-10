# Constructivist Montage production recipe

The workspace includes an executable original study in `src/studies/scenes.ts`, selected with `kino-montage`. Its drawing commands are consumed by `src/studies/pixi-renderer.ts`; geometry and time sampling are shared with the gallery renderer. All copy lives in `shared/locales/en/style-studies.json`.

In an untouched starter, run `npm run example -- kino-montage`, then `npm run dev`. The command refuses to replace an authored film, retains starter backups in `production/example-backup/`, and writes an 8-second study with its own resource tracks. `npm run export:html` and `npm run export:mp4` use this installed film normally. To use the recipe inside an existing film, import `studyFrame()` and `StudyRenderer`, then compose the selected scene into the project's timeline instead of running the installer.

## Evidence and sources

Internet Archive (read each item's `licenseurl`; for pre-1978 US film, check the title and end cards for a copyright notice — published 1930 or earlier is public domain by date), Wikimedia Commons (public domain, CC0 or CC BY, credited in full; not CC BY-SA), U.S. National Archives, Library of Congress, NASA and other federal agencies (federal works are public domain; check each item's rights statement), open-access museums such as the Met, Rijksmuseum and Smithsonian (CC0 where the object page says so), university and city library digitised ephemera (read the rights statement; "copyright status undetermined" is not usable). Download into the film's `public/` or `production/` folders, log every request, and record each asset's seconds used in `production/CREDITS.md` and every number, date and claim in `production/FACTS.md`.

## Adaptation decisions

- Composite each window as a masked `Container` (a rectangle or a sheared parallelogram) holding a graded `Sprite` or video texture; apply the duotone ink-to-paper grade with one `ColorMatrixFilter` shared by every window, photograph and document.
- Stand in for the segmentation-and-paper-border cut-out technique with flat `Graphics` silhouettes carrying a paper-coloured outline stroke; the signature tower stacks them with a simple eased camera climb tied to the floor counter.
- Drive every slam, wipe and flash from one beat-grid timing function (a `bar(n, beat)`-equivalent in `timing.ts`), shared by the diagonal bands, the type blocks and the cuts, so the whole poster cuts on the same grid.

The study is silent, original procedural art with illustrative values, labelled as such; it demonstrates material, layout and motion, not evidence. Replace its stand-ins with the real footage, photographs and documents described above, never with generated imagery. The gallery preview uses illustrative silhouettes, not real archive photographs, labelled as such. Configure the subject, palette, scene sequence, duration and soundtrack from the brief.

Use `src/studies/timing.ts` for deterministic easing, seeded variation, measured stroke truncation and cue helpers. `window.animaguru.texts` exposes visible study text bounds for `npm run review`; text declarations alone do not count as visual proof. Inspect the actual frames as well.

## Sources and attribution

Inspired by the following pinned references; source-specific 3D/media dependencies are not bundled. New study art and scene geometry are original. The workspace's `VIDEO-STYLE-NOTICES.txt` preserves the repository notices and clarifies third-party asset scope.

- [styles/kino-montage/STYLE.md](https://github.com/lemomo-ai/lemo-opuscar/blob/77ee8318df779b0736d7de0abe24387e51023735/styles/kino-montage/STYLE.md)
- [styles/kino-montage/demo/index.html](https://github.com/lemomo-ai/lemo-opuscar/blob/77ee8318df779b0736d7de0abe24387e51023735/styles/kino-montage/demo/index.html)
