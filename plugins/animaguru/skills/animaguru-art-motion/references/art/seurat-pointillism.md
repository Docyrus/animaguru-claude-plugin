# Pointillist optical mixing

Equal-size discrete pigment dots whose juxtaposition forms color.

## Material and construction

Lay a softly filtered flat base under a fixed hexagonal dot grid. Source pitch 10, row spacing 8.66 and radius 4.5 px produced about 24,000 dots. Select from a pure-color palette including pale mixtures. Project the target color onto candidate palette-pair segments, clamp the mixing weight to .2–.8, then choose a pigment by seeded hash. Cache quantized target-color matches and batch one path per pigment.

## Palette

Saturated blues, greens, yellow, orange, red-violet and purple, plus pale yellow, peach, green, blue and pink. Pure dark/saturated colors alone make light regions snowy.

## Motion

Let boats drift, a butterfly flap and river dots catch light. A restrained subset of dots may switch paired colors at stepped times; source 6 fps/7% was more visible than 4 fps/3%. Preserve the overall calm.

## Transition

Dots crystallize into the next image.

## Failure cases and adaptation

Hard palette-pair boundaries form bands: add small seeded target-color dithering before matching. An optional 8% complementary-dot pass and edge light transmission enrich the surface. Equal pure-color dots distinguish this from impressionist dabs; a regular computer grid may still need subtle fixed jitter.

Parameters above are upstream study values at approximately 1920×1080 unless stated otherwise. Scale them to the delivery format and check the actual result. These are English production adaptations, not bundled renderers or claims of validated AnimaGuru implementations.

Adapted from [the upstream card](https://github.com/alchaincyf/huashu-art-motion/blob/2571ee0a9a0467c4d99e935ea9e0fadda19210b0/references/%E9%A3%8E%E6%A0%BC%E9%85%8D%E6%96%B9/29_seurat.md) under the [MIT license](../../LICENSE). See [provenance](../sources.md).
