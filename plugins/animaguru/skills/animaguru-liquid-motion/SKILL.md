---
name: animaguru-liquid-motion
description: Build Liquid Motion visuals and motion in an AnimaGuru PixiJS video workspace. Use when this visual style is chosen for an explainer, advertisement or general video.
disable-model-invocation: true
---

# Liquid Motion

Graphics that behave like thick, glossy liquid: shapes pour, stretch into thin necks, snap and fuse; transitions are a wave of paint flooding the frame; a mark gathers from a single drop. Organic, satisfying and high-energy, it suits music videos, food and drink advertising, brand idents and transition packages. Subject, audience, emotional tone and story come from the user's brief. This style supports Explainer, Advertisement and General Video.

## Establish direction

Follow sibling `animaguru-video` for purpose → style → compact interview before new production. Reuse explicit choices and completed briefs; honor a requested interview skip. Share [the style gallery](https://animaguru.com/animation-styles#liquid-motion). Fold missing visual questions into the shared interview:

- Which liquid is it: candy-glossy paint, milk and cream, juice, molten metal or ink? Which 3–5 colours, and which ground behind them?
- What should form from the liquid at the end (a logo, a word, a product silhouette), and which beat should the paint wave carry?

## Build the look and movement

Read `pixijs` and the relevant Graphics, Filters, custom rendering (shaders), Container or Mesh skills. Read `animaguru` before generating assets; discover current models and estimates, respect the user's budget, and reuse completed media. Essential text, logos and exact geometry belong in authored canvas content.

- Model every liquid shape as a distance field and join shapes with a smooth minimum, so two drops grow a neck before they touch and fuse with a fillet. The cheaper route is the gooey filter: circles blurred by 20 px or more, then an alpha threshold (`ColorMatrixFilter` or a small custom filter); keep one route per film.
- Shade it as thick liquid, never flat blobs: a rounded surface-tension bead at every edge, a studio softbox reflected along the top-left of that bead, a sharp key highlight, a Fresnel rim, slightly brighter thin edges and a soft contact shadow on whatever lies behind.
- Liquid is thrown, never moved at constant speed: fast out, slow in (`cubic-bezier(0.22, 1, 0.36, 1)`). Nothing travels in a straight line or holds perfectly still; let surfaces swell and highlights drift.
- Stretch, neck, snap, rebound: a shape pulled away leaves a neck that thins, breaks in the middle, and each half recoils into its own end, with both ends ringing back over 2–3 frames.
- Secondary droplets follow the main mass 2–3 frames late and squash flat on landing before they fuse back in. Splashes throw a central jet that pinches off a droplet, plus a crown thrown sideways.
- Transitions are liquid wipes: a wave front with 3–5 bulges swelling out of phase, droplets thrown ahead of it and swallowed again. Two fronts in a row (a colour, then the next scene's ground) swap scenes without a cut or a crossfade.
- Form a mark from one drop through a simple intermediate shape (drop → pill → letters), morphing the distance fields point for point. Late droplets landing a beat after can complete it, for example as the full stop.
- When colours merge, keep clean zones (a swirl, a gradient through neighbouring hues) instead of averaging complementary colours into mud.

Use the [production recipe](references/recipe.md) for the bundled original study and port-specific decisions. It is a technique example, not a prescribed film. Keep motions a function of absolute seconds; separate drawing cadence from camera/light cadence when the material calls for it. Prepare assets locally, preserve async seeking and register actual resource/cue times. Keep essential type editable and localized.

## Review and delivery

Step through every neck snap and droplet landing frame by frame: the break, the 2–3 frame recoil at both ends and the late follower must all be visible. Check that wave fronts fully cover the frame before the scene behind them is swapped, that merged colours stay clean, that highlights sit on the edge facing the key light, and that the formed mark is legible on a still frame. Check representative full-resolution frames, moving playback, desktop/mobile fit and cold seeks. Follow `animaguru-video` for production records, audio mixing and MP4 delivery. Describe the actual 2D/2.5D rendering method accurately. Physically rendered 3D remains deferred.
