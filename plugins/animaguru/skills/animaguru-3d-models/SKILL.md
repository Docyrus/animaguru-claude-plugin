---
name: animaguru-3d-models
description: Generate 3D model assets with AnimaGuru (GLB meshes, optionally auto-rigged with animation clips, or photoreal Gaussian splats built from one image) and put them into an AnimaGuru film as real three.js 3D shots composited with the PixiJS 2D layers. Use when a film needs a product, prop, set or character in actual 3D (turntables, orbits, real lighting and shadows, a character walking through a scene, a product photo that turns into 3D), or when the user asks for 3D models, GLB files, Gaussian splats, rigging or 3D animation.
---

# AnimaGuru 3D models

The 3D styles (`product-turntable-3d`, `character-stage-3d`, `toy-diorama-3d`, `exploded-teardown-3d`) build on this skill; each has a runnable study (`npm run example -- product-turntable-3d`).

A 3D shot is ordinary film code: `ThreeStage` (in the kit) renders a three.js scene into its own canvas, shown in the Pixi film as one Sprite. 2D art can sit behind it, because the canvas is transparent where nothing is drawn, and titles, captions and leader lines go on top as normal Pixi Text, so `npm run review`, the frame checker, HTML5 export and MP4 export all work unchanged. Read sibling `animaguru-video` for the setup, interview and review workflow, and `animaguru` for credits and jobs; this skill adds what changes.

## Make the models

Models are project assets of type `model`. Check `animaguru catalog --type model` for the generators, face ranges and named clips, then `--dry-run` for the estimate.

```sh
# Image-to-3D (best): draw or upload a clean reference first, then build from its blob SHA.
animaguru assets generate PROJECT_ID --type image --name "Speaker ref" --prompt "Studio product photo of …, whole object in frame, plain white background, soft even light, no shadow, no text" --yes --wait
animaguru assets generate PROJECT_ID --type model --name "Speaker" --reference SHA --yes --download public/assets/models/

# A rigged character: a full-body reference facing the camera in a T- or A-pose (arms clear of the body), plain background.
animaguru assets generate PROJECT_ID --type model --name "Explorer" --reference SHA --rig --animations idle,walk,wave --height 1.6 --yes --download public/assets/models/

# Text-to-3D when there is no reference image.
animaguru assets generate PROJECT_ID --type model --name "Lantern" --prompt "An old brass ship lantern with a glass chimney" --yes --download public/assets/models/
```

- **Generators.** `tripo-h3.1` is the built-in default (staff may choose another; `defaultModels.model` in `assets list` names it): about 30 credits textured, 20 untextured, 2K PBR textures, 3–5 MB files, sized in metres. `hunyuan-3d-3.1-pro` keeps finer surface detail: about 53 credits with PBR, but 500,000 faces and 4K PNG textures (40–60 MB) unless you pass `--faces` (40,000–1,500,000, about 15 credits extra). Optimise its files before using them (below).
- **Rig.** `--rig` adds Meshy's humanoid auto-rig: about 20 credits plus 12 a clip, up to 10 clips. Name clips from the catalog (`idle`, `walk`, `run`, `wave`, `cheer`, `talk`, `jump`, `dance`…) or use any Meshy library number 0–696. Free `basic-walk` and `basic-run` cycles are added too. Rigging needs at most 300,000 faces; with Hunyuan3D, pass `--faces`.
- **Limits.** The rig has about 24 joints, no finger bones and no face blend shapes, so characters can walk, gesture and act with the body but cannot lip-sync or make expressions. Keep talking heads as 2D characters or avatars, or keep 3D characters at medium and wide shot sizes. Generated meshes fuse hair, clothes and props to the body. If rigging fails (non-humanoid shapes, hands touching the body), the model is still saved, without a rig, and the job report says why. Check `assets list` for the model's facts (triangles, clips, `rigError`).
- **What you get.** Every saved model faces +Z (glTF's front) and stands upright. Its asset record lists triangles, file size, height, joints and clips with their lengths.
- **Licensing.** Generated models are the account's assets like generated images. Record each in `production/` with its prompt, reference and job like other generated media.

## Photoreal splats from one image

`--model idol` (Sperid Labs' Idol) turns one saved image of an object into Gaussian splats: millions of soft coloured points that keep the image's own colours, materials and lighting. For a real product this is the most faithful option: glass, liquids, brushed metal, fabric and printed labels look like the photo, because they are the photo. It costs about 10 credits, takes about 20 seconds, and needs a saved image (`--reference SHA`); it makes no model from text.

```sh
# A clean product photo or render: the whole object in frame, sharp, ideally on a plain background (Idol cuts it out).
animaguru assets generate PROJECT_ID --type model --model idol --name "Perfume" --reference SHA --yes --download public/assets/models/
# --photo when the reference is a camera photo (a looser crop); --splats 524288 for finer detail (32,768–1,048,576, default 262,144); --seed N to repeat one.
```

- **What you get.** An `.spz` file (about 3 MB at the default 262,144 splats, about 13 MB at the maximum), upright (+Y) with the side the image showed facing +Z, inside a cube of side 1. The asset record's `result.model` lists `splats`, `bytes`, `height` and `view`: where the reference image was taken from, in the splat's own coordinates. Its preview is the cut-out image Idol built from.
- **Strengths and limits.** The side the image shows is exact; the sides it hid are invented and softer, so plan the camera: a half turn to three-quarter turn reads best, and a full turn shows the back for only a moment. Splats are not lit by scene lights or environments and cast no shadows (the image's light is baked in), so match the set's light direction to the photo's. They can't be rigged, deformed by bones or re-textured, and fine thin parts (straps, cables) may be fuzzy. Several objects in one image become one splat; generate each product from its own image.
- **When to use which.** Splats for real products and props the camera admires (turntables, hero reveals, photo-to-3D openings). Tripo or Hunyuan3D meshes for anything lit by the scene, cast shadows, exploded into parts, rigged or animated.

## Optimise and place the files

Download into `public/assets/models/` and load them with `publicAsset`-relative paths. Shrink large files before building the film; this needs no install:

```sh
npx --yes @gltf-transform/cli@4.5.1 optimize public/assets/models/speaker.glb public/assets/models/speaker.glb --compress meshopt --texture-compress webp --texture-size 2048 --simplify-ratio 0.1 --simplify-error 0.0005
```

Drop `--simplify-ratio` for rigged characters and for Tripo models that are already small; simplifying a skinned mesh can tear it. A 62 MB Hunyuan3D speaker became 1.5 MB this way. `ThreeStage.load()` decodes meshopt and WebP itself. Keep HDR environments in `public/assets/` too: a 1K studio `.hdr` (for example from Poly Haven, CC0) lights products well.

## Stage splats

```ts
import { ThreeStage, THREE, normalize, photoView, softShadow } from "./kit";

const stage = new ThreeStage({ width: 1920, height: 1080, supersample: 1.5 });
const scene = new THREE.Scene();
const perfume = normalize(await stage.splat("assets/models/perfume.spz"), 0.3);  // metres, on y = 0, centred
const holder = new THREE.Group(); holder.add(perfume, softShadow(0.2)); scene.add(holder);
const camera = new THREE.PerspectiveCamera(30, 1920 / 1080, 0.02, 60);
const view = { position: [0, -0.438, 12.049] as [number, number, number], fov: 8.07 }; // the asset's result.model.view
this.on((t) => {
  holder.rotation.y = 0.35 * t;
  if (t < 1) photoView(perfume, view, camera);   // opens on exactly the product photo…
  else { /* …then ease into an orbit, as for any model */ }
  return stage.draw(scene, camera);              // return it: splats are sorted for each frame's camera
});
await stage.warm(scene, camera);
```

- **Return `stage.draw()`.** Spark sorts splats for the camera in a worker, so with splats in the scene `draw()` returns a promise, and the film waits for it before the frame. An update that drops it renders splats in the order of an earlier camera. Every frame is still a pure function of `t`: cold seeks and sequential playback give identical frames.
- **Colour.** The first splat switches the stage from AgX to Neutral tone mapping, which keeps the photo's colours through `stage.post()`; meshes in the scene look a little crisper than with AgX. Set `stage.renderer.toneMapping` after loading to choose otherwise.
- **Placing.** `normalize()`, `bounds()`, `project()` and holders work as for meshes. Use `softShadow(width, depth, opacity)` under each splat, on a plinth or floor. Splats mix with meshes in one scene and respect their depth. `photoView()` needs the splat placed first.
- **Size.** Each splat file loads whole: keep a film to a few splats at the default count (a 1080p frame with two takes about 50 ms to render on a Mac), and count their megabytes in HTML5 exports.

## Build the shot

```ts
import { FilmBase, easeInOut, clamp01, lerp, txt, ThreeStage, Rig, THREE, strideSpeed, normalize, vecAt } from "./kit";

// In build():
const stage = new ThreeStage({ width: 1920, height: 1080, supersample: 1.5 });
const { env } = await stage.environment("assets/hdr/studio_small_09_1k.hdr");
const scene = new THREE.Scene();
scene.environment = env;
const camera = new THREE.PerspectiveCamera(30, 1920 / 1080, 0.1, 60);
const gltf = await stage.load("assets/models/explorer.glb");
const hero = normalize(gltf.scene, 1.6);         // metres, feet on y = 0, centred
const holder = new THREE.Group(); holder.add(hero); scene.add(holder);
const rig = new Rig(hero, gltf.animations);
const speed = strideSpeed(rig, hero, "walk");    // Meshy's walks are in place
this.world.addChild(backdrop, stage.sprite, titles); // 2D behind, 3D, 2D on top
this.on((t) => {
  const s = t - 6;                                // shot time
  const wave = clamp01((s - 3.3) / 0.35);         // crossfade by easing weights
  rig.pose([{ clip: "walk", time: s, weight: 1 - wave }, { clip: "wave", time: s - 3.3, weight: wave, loop: false }]);
  holder.position.x = -3 + speed * Math.min(s, 3.4);
  holder.rotation.y = lerp(Math.PI / 2, 0, easeInOut((s - 3.1) / 0.7));
  vecAt(s, [[0, [-1.2, 1.7, 10]], [6, [0.5, 1.5, 8.5]]], camera.position);
  camera.lookAt(0, 1.1, 0);
  const head = stage.project(hero.getObjectByName("Head")!.getWorldPosition(new THREE.Vector3()), camera);
  label.position.set(head.x + 40, head.y - 80);  // 2D label that follows the head
  stage.draw(scene, camera);                     // last: uploads this frame to Pixi
});
await stage.warm(scene, camera);                 // compile shaders before the first frame
```

- **Determinism.** Every frame must be a pure function of `t`, and `npm run review` checks cold seeks. Pose with `Rig.pose()` (never `mixer.update(delta)`), drive cameras and objects from `t`, give custom shaders a time uniform you set from `t`, and seed any randomness with the kit's `rng()`. Register the update that calls `stage.draw()` after every update that moves 3D objects, and call `stage.warm()` for each scene before the film starts.
- **Walking speed.** Meshy's walk and run clips are in place: `strideSpeed(rig, model, "walk")` measures the speed from the planted foot, so move the holder at that speed (times the clip's playback rate) and the feet do not slide. Clips from other sources may travel forward instead; `inPlace()` strips that root motion and returns its speed. Measure before turning the holder, and turn the holder, not the model, so `normalize()` stays valid.
- **Facing.** Saved models face +Z. A holder rotated by `Math.PI / 2` faces +X.
- **2D over 3D.** `stage.project(worldPoint, camera)` gives film coordinates for labels, leaders and callouts (`behind` is true when the point is behind the camera). Anchor exploded-view labels and product callouts this way so they follow the orbit.
- **3D over 2D.** Leave `scene.background` unset over painted 2D scenery, and add a ground plane with `new THREE.ShadowMaterial({ opacity: 0.3 })` and `receiveShadow`, so the character casts its shadow onto the painting.
- **Look.** Light products with an HDR `scene.environment` plus one shadow-casting key light. AgX tone mapping is the default. Use `stage.post(scene, camera, { bloom, bokeh })` for an MSAA pass with depth of field (set the returned pass's `uniforms.focus.value` to the subject distance each frame) and restrained bloom (threshold 0.9 or more). Add fog that matches the background colour to hide a floor's horizon. Toon looks are `THREE.MeshToonMaterial` with an outline pass or inverted-hull outline.
- **Several shots.** One `ThreeStage` can draw different scenes. Draw the scene for the current shot only.

## Check it

Run `npm run review` and look at the frames: scale against the set, feet on the ground (no floating, no sinking), the shadow under the character, labels on their parts, no clipping through props, and textures sharp at the closest framing. At 1080p with 1.5× supersampling, a headless MP4 export of a 3D film runs at about real time on a Mac with a GPU; machines without a GPU render post effects several times slower. Keep the total model size in an HTML5 export to a few MB.
