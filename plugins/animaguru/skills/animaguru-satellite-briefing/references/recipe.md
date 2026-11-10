# Satellite Briefing production recipe

The workspace includes an executable original study in `src/studies/scenes.ts`, selected with `satellite-briefing`. Its drawing commands are consumed by `src/studies/pixi-renderer.ts`; geometry and time sampling are shared with the gallery renderer. All copy lives in `shared/locales/en/style-studies.json`.

In an untouched starter, run `npm run example -- satellite-briefing`, then `npm run dev`. The command refuses to replace an authored film, retains starter backups in `production/example-backup/`, and writes an 8-second study with its own resource tracks. `npm run export:html` and `npm run export:mp4` use this installed film normally. To use the recipe inside an existing film, import `studyFrame()` and `StudyRenderer`, then compose the selected scene into the project's timeline instead of running the installer.

## Evidence and sources

USGS Landsat (1972 on, worldwide), USGS NAIP (US, about 1 m), NASA Blue Marble, MODIS and VIIRS through NASA GIBS, and Copernicus Sentinel with its credit line ("Contains modified Copernicus Sentinel data [year]"); outlines from Natural Earth. Search by bounding box and date in the Planetary Computer STAC or USGS EarthExplorer and log every request. Not usable: Google, Bing, Esri, Mapbox, Planet or Maxar imagery, news photos or generated imagery. Download into the film's `public/` or `production/` folders, log every request, and record each asset in `production/CREDITS.md` and each claim in `production/FACTS.md`. Burn a readable credit into the frame where the medium calls for one.

## Adaptation decisions

- Load each plate as a texture inside one world `Container`, nested by resolution with feathered alpha masks. Scale the container in log space for the dive and cross-blend plates where their texel size meets the screen pixel. An oblique orbit can use `PerspectiveMesh` corners or a small shader; describe it as a 2.5D view unless a shader does the ray–sphere work.
- Apply the analyst grade with a `ColorMatrixFilter` or a small custom filter driven by one uniform. Keep marks in a separate, unfiltered layer drawn with `Graphics` from projected ground coordinates every frame.
- Put dated plates on one grid and reveal the newer plate behind a soft moving gradient mask; each outline prints behind the same mask edge, and earlier outlines stay as dashed history.

The study is silent, original procedural art with illustrative values, labelled as such; it demonstrates material, light, layout and motion, not evidence. Replace its stand-ins with the real data, imagery or scans described above, never with generated imagery. The gallery preview is procedural terrain drawn in code, labelled on screen as not a real place. Configure the subject, palette, scene sequence, duration and soundtrack from the brief.

Use `src/studies/timing.ts` for deterministic easing, seeded variation, measured stroke truncation and cue helpers. `window.animaguru.texts` exposes visible study text bounds for `npm run review`; text declarations alone do not count as visual proof. Inspect the actual frames as well.

## Sources and attribution

Inspired by the following pinned references; source-specific 3D/media dependencies are not bundled. New study art and scene geometry are original. The workspace's `VIDEO-STYLE-NOTICES.txt` preserves the repository notices and clarifies third-party asset scope.

- [styles/satellite-briefing/STYLE.md](https://github.com/lemomo-ai/lemo-opuscar/blob/b5e8ef93930b6d828f352055a689320f138237b1/styles/satellite-briefing/STYLE.md)
- [styles/satellite-briefing/demo/engine.js](https://github.com/lemomo-ai/lemo-opuscar/blob/b5e8ef93930b6d828f352055a689320f138237b1/styles/satellite-briefing/demo/engine.js)
- [styles/satellite-briefing/demo/overlay.js](https://github.com/lemomo-ai/lemo-opuscar/blob/b5e8ef93930b6d828f352055a689320f138237b1/styles/satellite-briefing/demo/overlay.js)
