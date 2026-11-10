# Rendering, camera and review

Contents: runtime mapping; material pipelines; characters and contact; camera; deterministic rendering; review and delivery.

## Map techniques to the installed runtime

The upstream source uses Canvas globals such as `PAINT`, `CAM`, `MO`, `DG`, `CL`, `CH`, `UI` and `TOON`. Those are provenance, not dependencies of this skill. Do not import them into AnimaGuru by name or claim their demos are locally installed.

In an existing AnimaGuru film, inspect `src/kit/index.ts` or workspace `runtime/kit/index.ts`, the film entry point and local skills. The current kit provides `FilmBase`, time windows, easing, seeded `rng`, text, panels, line reveals and asset helpers. Scene hooks register updates driven by absolute time. Use existing helpers before adding a small scene-local implementation. For Pixi code, read the available `pixijs` skill and relevant assets, container, graphics, sprite, text or filter references.

Keep the normal player contract: asynchronous seeking and frame rendering, film dimensions/fps/duration, local media, synchronized captions, audio and resource metadata. A hybrid SVG overlay outside the captured Pixi canvas may disappear from MP4 export; put intended film content inside the supported capture surface or explicitly rasterize/composite it. The source's standalone SVG demo is not compatible with a Canvas-only recorder without adaptation.

## Material pipeline

A useful default for painted scenes is:

1. Establish flat form, composition and value.
2. Repaint large regions with the selected material renderer.
3. Render small props separately with finer parameters.
4. Apply compatible material to subjects, preserving silhouettes and features.
5. Add motivated light, local motion and restored visible detail.

Change that order when the medium demands it. Ink starts with unpainted paper and adds strokes. Pattern art starts with a flat shape and its pattern. Chiaroscuro begins with a readable lit scene and multiplies a light map. Cut paper needs unified silhouettes and contact shadows. A universal filter on a completed flat scene rarely supplies those construction differences.

For brush and dot work, define a color group per region. Stable sampled colors with deliberate warm/cool relations work better than independent RGB jitter. Keep stroke positions fixed and change a flow field continuously; re-randomizing the whole screen produces flashing. Line boiling or a stepped pose cadence can be intentional in a local region. Distress, flakes and heavy dirt should usually protect focal faces and exact text.

Cache static surfaces, tessera layouts, patterns, masks and blur passes; prewarm heavy caches before capture. Reuse offscreens and reset their drawing state each frame. If reading pixels often, choose a read-friendly offscreen context. Write raw pixel data into an offscreen and composite it through the current camera/mask rather than bypassing them with `putImageData` on the final surface.

Keep compositing operations local. Repeated `source-in` can erase earlier patterns: build the pattern layer first and mask it once. `destination-out` on the final surface creates transparent holes; carve isolated pieces before compositing. A paper-color layer applied source-atop can wash a figure white; clip the texture and choose the actual intended blend. When a texture/brush pass excludes a rectangular prop region, it leaves a visible patch; draw that prop as a separate layer instead.

Check contour occlusion by part order. A final outline pass across every body part can draw hidden limbs through torsos. Either draw fill/texture/visible outline per part in depth order or derive a proper visible-line mask. Rounded caps and opposite path winding can leave holes at joints; union silhouettes before outlining when needed.

## Characters and contact

Measure landmarks from the actual art rather than guessing a generic skeleton. Preserve crop offset, alpha bounds, head/neck anchors, hands, feet and prop contact. Use the same transform for fill, material and outline. Squash and stretch around a support point; a center pivot makes the feet slide.

Use actual sprite-sheet rectangles, cadence and anchors from downloaded metadata. Do not assume every generated pose has identical height or padding. Normalize apparent height with measured feet/head landmarks, not destructive anatomical stretching. Do not mirror an asymmetric costume, prop or face detail merely to change travel direction. For walking, a genuine gait and distance-based phase are preferable to sliding a standing sprite.

For a hand meeting a world-space prop, transform the contact into the local rig coordinate space. Keep upper/forearm lengths and bend direction stable if using two-bone IK. A generated full-body frame enlarged for a face close-up can lose quality; prepare a matching bust/detail asset. Mouth activity should stop in silence. RMS-driven mouth opening is a coarse performance technique, not verified phoneme lip sync.

## Camera language

First identify what the viewer should inspect and whether it is already readable. If so, holding is appropriate. Fit the target's actual bounds with a margin; do not tune arbitrary coordinates until the words nearly fit. Keep neighboring half-cut labels outside the final frame.

| Action | Purpose | Useful starting range |
|---|---|---|
| Hold | Read, watch an existing action, or let a reaction land | Follow the voice and reading need. |
| Push | Make a specific detail readable | .6–1.5 s, eased. |
| Pull back | Restore context or reveal the whole relation | .8–2 s, a controlled long tail. |
| Pan/glide | Find the next object in one continuous world | .5–.9 s; longer for following a connecting line. |
| Fast push or slam | A reveal, reversal, key number or joke | Roughly .17–.35 s, followed by a hold. |
| Hard cut/jump-in | Change viewpoint or land a reaction | Immediate, with matched geometry when it is the same world. |
| Drift | Sustained atmosphere or an expressive music passage | Use only when the composition and mood benefit. |

These are source-derived design suggestions, not quotas. Do not fill every pause with a slow zoom or every noun with a fast one. Once pushed in, consider a pullback, sideways move or held cut. Source footage may already supply sufficient motion. A still image cannot prove camera smoothness; watch at normal speed.

For scale travel, use `z = exp(lerp(log(z0), log(z1), easedProgress))`. Continue rendering the live world through the transition rather than enlarging a low-resolution still. Preserve color/position landmarks at the cut, and make the mask or portal cover the complete frame. Use a larger world, background fill and blur overscan to prevent exposed edges. Keep captions, progress and persistent HUD in screen space when they should not move with the scene.

## Deterministic capture

Derive every state from absolute film time and stable IDs/seeds. Incremental particle integration, uncontrolled video clocks and render-call-order RNG make random seeks unreliable. Derive particle positions analytically, or use a reproducible simulation with deterministic checkpoints. Seed textures once; derive time-varying variation from explicit quantized time where required.

Compare a cold render of time A with warm/seek-order renders A → B → A. Inspect the actual raster output as well as state. Ensure caches include any inputs that alter their output, and invalidate them when those inputs change. Missing scenes, failed imports or syntax errors should fail visibly rather than silently produce a placeholder.

The upstream SVG example obtained equal screenshots under a specific Chromium configuration that disabled partial rasterization. Do not generalize that result to every browser. Verify the AnimaGuru capture surface and browser configuration actually used. Await decoded video frames and texture uploads before a frame render resolves.

Profile end-to-end capture, including GPU completion when relevant. Upstream milliseconds are measurements of another engine, machine and resolution. They are not guarantees. Optimize heavy work only after measuring the new film: cache static rendering, batch patterns and dots, and reduce unnecessary full-screen passes.

## Review and delivery

In the installed starter, use its build, `review`, `frames` and MP4 tools as documented by `animaguru-video`. For a multi-animation workspace, run from the workspace root with the selected animation argument. Keep the film's real resources and clip timing in the resource registry so the timeline and review tools inspect the finished film.

Review representative full-size stills, transition midpoints, extreme expressions and the smallest intended display. Watch the complete film at normal speed and listen to the final mix when those capabilities are available. Check:

- Does the selected material read immediately, including on the subjects?
- Does each visible event explain or express something, with natural reading holds?
- Are exact text, numbers, sources, labels and captions correct and unobscured?
- Are contact points, layer order, frame edges and scene continuity sound?
- Do cue timing, mouths, impacts and the actual recording agree?
- Are arbitrary seeks stable and exports complete at the requested dimensions, duration and frame count?

Motion-area, static-frame and jump statistics are diagnostics. A noisy VHS frame can score as moving while nothing meaningful happens; storytime and mathematical explanations may intentionally contain long static holds. Inspect suspicious intervals rather than enforcing a universal threshold or speeding up scenes to pass a score. Do not claim an independent review when none occurred.

Deliver the film as an MP4 with production sources; films download only as MP4. Check that the film plays from its local `public/` assets in `npm run dev`, and in AnimaGuru's hosted player and embed when the user has it submitted. For MP4 verify codecs, audio, dimensions, duration and exact frame count using the existing exporter. State any unperformed playback/listening checks. Publishing, uploading and package release are separate actions from local film creation.
