# 3D Exploded Teardown production recipe

The workspace includes an executable original study in `src/studies/three/exploded-teardown-3d.ts`, rendered by `src/studies/three-film.ts` through the kit's `ThreeStage`. Its on-screen copy lives in `shared/locales/en/style-studies.json` (`threeStyles`).

In an untouched starter, run `npm run example -- exploded-teardown-3d`, then `npm run dev`. The command refuses to replace an authored film, retains starter backups in `production/example-backup/`, and writes an 8-second study. `npm run export:mp4` uses the installed film normally. To use the technique inside an existing film, copy the study's part, lift and callout functions into a scene and register its update with `film.on()`.

## Sources

- **Real products:** the user's CAD first (STEP, IGES, glTF/GLB, OBJ), then the maker's published CAD or open-hardware files with their licence (CC0, CC BY and MIT are fine with credit; CC BY-SA, CERN-OHL and GPL hardware: name the terms and ask). Convert offline to GLB with one named mesh per part, metres as units, and the assembly's normal along +Y; record each file in `production/CREDITS.md` and each claim in `production/FACTS.md`.
- **Invented products:** model the parts in code or Blender, or generate the whole object with `animaguru assets generate --type model` and split it (Tripo part generation, Hunyuan3D part splitting), then rebuild any fused part by hand. Label the product as invented and its specs as illustrative.
- **Light:** CC0 HDRIs from Poly Haven (studio sets such as `studio_small_09`) or the kit's `room()` environment, which needs no file.

## Adaptation decisions

- One `THREE.Group` per part, built at its assembled position; the lift is a translation along the part's axis times an eased 0–1 amount, `open × (1 − close)`, so seeking anywhere gives the same pose. Screws also rotate by a multiple of that amount as they back out.
- Fasteners first, then a short stagger down the stack; the camera's distance follows the opening amount so the whole stack stays in frame, and its azimuth sweeps on its own ease across the film.
- Callout anchors are points on each part's camera-facing edge, transformed by the part's world matrix and projected every frame. Labels sit outside the projected bounding box of the whole product on the part's side, relaxed vertically so neighbours keep a fixed gap. Draw leaders and dots in one `Graphics` and the words as `Text` above the stage sprite.
- Studio grey (or a dark plate for an evidence look) is a Pixi gradient behind the transparent stage; a `ShadowMaterial` floor gives the floating stack its shadow. Large textures (boards, screens, labels) are canvas textures painted once, seeded so they never change between frames.

The study is silent, original procedural art: an invented console with illustrative parts and numbered callouts, labelled as such. Replace it with the product's own files as described above. The gallery preview is rendered in code from an original model with the same technique, lit by a CC0 Poly Haven HDRI.
