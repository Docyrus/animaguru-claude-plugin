# Flat outline television cartoon

A Rick-and-Morty-inspired drawing treatment using original characters and semantic parts.

## Material and construction

Use hard flat fills, sparse same-hue shadows, rounded contours and low-contrast background mottling. Source contours were #222323 at 2.35 px, with details 1.6–2.6 px at 1920 width. Separate body, head, arms/prop, eyelids and pupils into semantic groups. Establish a convincing still, then animate existing anchors. Build a tail from a centerline and width profile.

## Palette

Warm gray wall #CDBF96, wood #9B7752, skin #EFC4A0 and sky #A7D6EA are source examples; adapt them to the new subject.

## Motion

Move gaze, deterministic blinks, a small head turn, a slow prop lift and a continuous tail. Keep the shoulder anchored while the sleeve follows the hand. The source jump moves body and tail together; it contains no full walk cycle or landing compression.

## Transition

An intentional cut, prop match or simple scene-camera change; traveling through other art styles is optional.

## Failure cases and adaptation

The upstream example is standalone SVG, unlike the 35 Canvas scenes. Do not assume its renderer API exists in AnimaGuru. Rebuild semantic groups in the current runtime or rasterize intentionally. SVG DOM state can be deterministic while screenshots vary with partial rasterization; verify the actual capture configuration. Do not reuse show characters, voices or upstream demo likenesses.

Parameters above are upstream study values at approximately 1920×1080 unless stated otherwise. Scale them to the delivery format and check the actual result. These are English production adaptations, not bundled renderers or claims of validated AnimaGuru implementations.

Adapted from [the upstream card](https://github.com/alchaincyf/huashu-art-motion/blob/2571ee0a9a0467c4d99e935ea9e0fadda19210b0/references/%E9%A3%8E%E6%A0%BC%E9%85%8D%E6%96%B9/37_rick_morty.md) under the [MIT license](../../LICENSE). See [provenance](../sources.md).
