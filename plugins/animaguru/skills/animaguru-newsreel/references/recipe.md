# 1920s Newsreel production recipe

The workspace includes an executable original study in `src/studies/scenes.ts`, selected with `newsreel`. Its drawing commands are consumed by `src/studies/pixi-renderer.ts`; geometry and time sampling are shared with the gallery renderer. All copy lives in `shared/locales/en/style-studies.json`.

In an untouched starter, run `npm run example -- newsreel`, then `npm run dev`. The command refuses to replace an authored film, retains starter backups in `production/example-backup/`, and writes an 8-second study with its own resource tracks. `npm run export:mp4` uses this installed film normally. To use the recipe inside an existing film, import `studyFrame()` and `StudyRenderer`, then compose the selected scene into the project's timeline instead of running the installer.

## Evidence and sources

U.S. National Archives (films, often via Internet Archive "FedFlix" copies; federal works are public domain; Universal Newsreel 1929–1967 is in NARA too), Internet Archive (check each item's licence field and provenance; skip YouTube mirrors or "restored/AI enhanced" versions), Wikimedia Commons (PD-US-expired, PD-US-no-notice, PD-USGov, CC0 or CC BY only; not CC BY-SA or "no known restrictions"), Library of Congress, print published in the US before 1931 (newspapers, magazines, books on archive.org/HathiTrust/Commons, public domain), and sound recordings published before 1926 (public domain in the US). Download into the film's `public/` or `production/` folders, log every request, and record each asset in `production/CREDITS.md` and each claim in `production/FACTS.md`.

## Adaptation decisions

- Composite the gate as a `Container` clipped to a rounded-rectangle mask; apply the silver grade with a `ColorMatrixFilter` (greyscale, contrast, warm multiply/screen tint) plus a small custom filter or seeded `Graphics` noise for flicker, gate weave and scratches, applied to the picture layer only.
- Build the ident (searchlights, globe, title lettering) and the spinning-paper headline with `Graphics` and `Text` in OFL faces; animate the paper's slam with a scale/rotation tween that decays into a landing beat, never as "archive" imagery.
- Keep subtitles, place cards and the end card on an unfiltered type layer above the gate, so type never weaves or flickers with the picture; drive every cut and landing from one beat-grid timing function.

The study is silent, original procedural art with illustrative values, labelled as such; it demonstrates material, layout and motion, not evidence. Replace its stand-ins with the real archive film, photographs, print or recordings described above, never with generated imagery. The gallery preview shows only the code-drawn packaging (the ident, the spinning headline, a place card and an iris), with no footage standing in for real archive film. Configure the subject, palette, scene sequence, duration and soundtrack from the brief.

Use `src/studies/timing.ts` for deterministic easing, seeded variation, measured stroke truncation and cue helpers. `window.animaguru.texts` exposes visible study text bounds for `npm run review`; text declarations alone do not count as visual proof. Inspect the actual frames as well.

## Sources and attribution

Inspired by the following pinned references; source-specific 3D/media dependencies are not bundled. New study art and scene geometry are original. The workspace's `VIDEO-STYLE-NOTICES.txt` preserves the repository notices and clarifies third-party asset scope.

- [styles/newsreel/STYLE.md](https://github.com/lemomo-ai/lemo-opuscar/blob/77ee8318df779b0736d7de0abe24387e51023735/styles/newsreel/STYLE.md)
- [styles/newsreel/demo/index.html](https://github.com/lemomo-ai/lemo-opuscar/blob/77ee8318df779b0736d7de0abe24387e51023735/styles/newsreel/demo/index.html)
