---
name: animaguru-painterly-depth-animation
description: Build layered animated scenes from painterly artwork, textured planes and atmospheric depth. Use for the Painterly Depth Animation visual style in an AnimaGuru video workspace.
disable-model-invocation: true
---

# Painterly Depth Animation

Bring brush-textured artwork into motion through composed depth, atmosphere and selected performances. The user's Explainer, Advertisement or General Video brief determines subject, emotional tone and story; this style supports many settings and audiences.

## Establish the direction

Follow the sibling `animaguru-video` category → style → quick interview flow for new films. Reuse supplied choices and completed briefs; honor an explicit request to skip the interview. Share [the style preview](https://animaguru.com/animation-styles#painterly-depth-animation). Include missing visual choices in the shared interview:

- What painting medium and references fit the film: gouache, watercolor, textured digital paint or another treatment?
- What palette, lighting and atmosphere support the brief?
- Should scenes feel like moving illustrations, a travelling layered environment, or character performances within painted settings?

## Design and build

- Read `animaguru` and inspect its current `painted` style and asset models. Available image tools can create supporting layers when appropriate. Specify consistent brush scale, lighting, perspective and palette across generated or supplied art.
- Plan foreground, subject, middle and distant planes before asset generation. Request or create enough overscan for the intended camera movement. A single finished painting does not contain the background hidden behind a removed subject; prepare that missing area before moving layers apart.
- Read `pixijs`, assets, container and sprite guidance. Build a depth stack with clear overlap and transform origins. Keep brush texture attached to its surface; global moving noise is not a substitute for painted material.
- Derive camera offset and per-plane parallax from absolute time. Choose motion amplitude from the available overscan, not arbitrary speed. Confirm that layer edges and transparent holes never become visible.
- Use restrained shape deformation only where the material supports it, such as foliage or fabric. Rigid objects should retain their form. Generated performance clips can supply organic movement; preserve character identity and match their paint treatment to the scene.
- Build atmospheric depth with value, color temperature, haze and selective softness. Avoid blurring the entire image or washing out text. Keep any grain stable and proportionate to the viewing size.
- Reveal scenes through foreground occlusion, brush-like masks, changing light or a composed cut. Texture reveals should expose a complete composition rather than obscure the message throughout the scene.
- Keep important text editable in the canvas, with quiet areas or backing shapes for legibility. Record every actual plane, performance and audio resource in the shared timeline.

## Review and completion

Follow `animaguru-video` for production records, audio and exports. Inspect camera extremes, disoccluded areas, edge halos, texture scale and lighting consistency. Check full-speed playback for texture swimming and arbitrary seeks for stable atmospherics. Deliver prepared local layers, intentional depth motion and the working HTML5 film; export MP4 when requested.

## Additional visual treatments

Read [the material and motion variants](references/variants.md) when the brief calls for a specialized treatment. Choose the relevant recipe without imposing its example story.
