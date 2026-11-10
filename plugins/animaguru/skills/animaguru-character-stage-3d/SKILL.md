---
name: animaguru-character-stage-3d
description: Build 3D Character Stage films in an AnimaGuru video workspace, where a rigged 3D character walks, turns and gestures in front of a painted 2D backdrop and casts real shadows onto it. Use when this visual style is chosen for an explainer, advertisement or general video.
disable-model-invocation: true
---

# 3D Character Stage

A rigged 3D character performs on a painted 2D set: it walks in at its stride's true speed, turns to the camera, waves, points or talks with its hands, and its shadow falls across the painting as if the paint were the ground it stands on. Captions carry the story. The character is real 3D, posed at absolute film time; the set is one painting matched by a 3D camera. Subject, audience, emotional tone and story come from the user's brief. This style supports Explainer, Advertisement and General Video.

## Establish direction

Follow sibling `animaguru-video` for purpose → style → compact interview before new production. Reuse explicit choices and completed briefs; honor a requested interview skip. Share [the style gallery](https://animaguru.com/animation-styles#character-stage-3d). Fold missing visual questions into the shared interview:

- Who is the character, and is there an approved design or reference to build the 3D model from? What do they do in each shot (walk in, wave, explain, cheer)?
- Which place does the painting show, in what painterly treatment, and where is its light coming from?

## Build the look and movement

Read sibling `animaguru-3d-models` before generating anything: it covers the costs, the `model` asset type, rigging, clip names, optimisation and the kit's `ThreeStage`, `Rig` and `normalize()`. Read `animaguru` for credits and jobs, and `pixijs` for the 2D layers.

- **The set.** One wide painting (16:9, no people, a clear ground plane and horizon, one strong light direction), generated as an image asset in the brief's painterly style or supplied by the user. It sits behind the transparent `stage.sprite`; titles and captions go above it.
- **The character.** Generate a reference image of the character standing in a T- or A-pose on a plain background, facing the camera, then a rigged model (`--rig --animations idle,walk,wave,talk`). The rig is humanoid with about 24 joints, no fingers and no face: the character acts with its body, so keep dialogue as captions or off-screen narration, never fake lip-sync.
- **Match the camera to the painting.** Keep the camera level at the painting's eye height and shift the lens so the 3D horizon lands on the painted one (set `camera.projectionMatrix.elements[9]` after `updateProjectionMatrix()`); tilting the camera would bend the painting's verticals. Choose the field of view so the character's size at the stop point agrees with doors and chairs painted at that depth. Eyes sit on the horizon only when the camera is at eye height; a low painted eye level means a low camera.
- **Ground and light.** A large `ShadowMaterial` plane at y = 0 receives the shadow; tint its colour toward the painting's shadow colour (warm brown at golden hour, blue-grey in daylight) rather than black. Aim the shadow-casting `DirectionalLight` from the painted light so the character's shadow runs the way the painted shadows do; add a hemisphere light and a soft fill in the painting's colours so the figure isn't darker than the set. A small soft dark disc under the feet grounds them where a long shadow can't.
- **Walk without sliding.** Meshy's walks are in place: measure the speed with the kit's `strideSpeed(rig, model, "walk")` (the planted foot's backward speed) and move the character's holder at that speed, or play the clip faster and multiply the speed by the same rate. Clips that carry root motion instead give their speed through `inPlace()`. Turn the holder, never the model. Plan the path so the walk ends where the character performs, and keep painted foreground objects (chairs, planters) clear of its path, or the 3D figure draws in front of them.
- **Performance.** Crossfade clips by easing their weights in `Rig.pose()`: walk fades into idle as the character stops and turns to camera (0.6–0.9 s), then one clear gesture per caption beat. Calm one-hand waves read better than big full-body waves in a close shot; the talk clip suits a "here's what I mean" beat.
- **Integration.** Tone-map with ACES when the painting is saturated, give the 3D layer a slight warm grade and softness (a 2D filter on the sprite) and, if the painting glows, a faint screen-blended blur of the figure. Reframe the whole composite in 2D (paint and sprite together) for camera follows and push-ins; a 3D camera move would slide the figure against the painting.
- **Captions.** Short lines in the lower third, one beat each, timed to the action they describe, over a soft darkening of the painting's lower edge. Keep them editable `Text`.

Use the [production recipe](references/recipe.md) for sources, the bundled original study and port decisions. Keep motion a function of absolute seconds; never advance the mixer with frame deltas.

## Review and delivery

Step through the walk frame by frame: the stance foot must not slide, feet must touch the painted ground (no floating, no sinking), and the turn should read as a pivot, not a skate. Check that the shadow runs the painting's way and its colour matches the painted shadows, that the character's scale agrees with painted doors and furniture at its depth, that it never draws in front of painted foreground objects, that the clothes don't tear in gestures, and that captions hold long enough to read. Check representative full-resolution frames, moving playback, desktop/mobile fit and cold seeks. Follow `animaguru-video` for production records, audio mixing and HTML5 delivery; export MP4 when requested.
