# Early CGI and ray-traced plastic

Glossy primitives, chrome, checkerboard reflections and conspicuously synthetic surfaces.

## Material and construction

Use a coherent plastic shading model: base color, radial dark edge, environment reflection and hard highlight. Cylindrical limbs and rounded solids should share the same light source. A mirrored floor image can suggest reflection in a 2.5D scene; describe it as a controlled approximation. Use a real 3D renderer when actual ray-traced geometry is required.

## Palette

Bright plastic colors, chrome gray, a dark/light checkerboard and sharp white highlights.

## Motion

Rotate a torus, turn a reflective object and animate a glint or mechanical eye. Reflection motion should follow the subject rather than behave as an independent overlay.

## Transition

Wireframe resolves into shaded geometry, or a scanline reveals the next scene.

## Failure cases and adaptation

Blocky faces and legs weakened the source demo. Avoid claiming physically correct ray tracing for a painted highlight. Keep reflections aligned to the floor and contact points; a displaced mirror image breaks depth immediately.

Parameters above are upstream study values at approximately 1920×1080 unless stated otherwise. Scale them to the delivery format and check the actual result. These are English production adaptations, not bundled renderers or claims of validated AnimaGuru implementations.

Adapted from [the upstream card](https://github.com/alchaincyf/huashu-art-motion/blob/2571ee0a9a0467c4d99e935ea9e0fadda19210b0/references/%E9%A3%8E%E6%A0%BC%E9%85%8D%E6%96%B9/15_raytrace.md) under the [MIT license](../../LICENSE). See [provenance](../sources.md).
