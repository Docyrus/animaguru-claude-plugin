# 8-bit pixel art

Low-resolution silhouettes, limited colors and discrete sprite acting.

## Material and construction

Draw at a small logical resolution such as 240×135 for 1920×1080 output; enlarge with nearest-neighbor sampling. Use a limited palette around 14 colors and a one-logical-pixel outline per part. Place features on the pixel grid. Reuse supplied or generated sprite sheets with their actual frame rectangles and timing.

## Palette

A small indexed palette with deliberate shared ramps; avoid independently quantizing each frame.

## Motion

Step a tail through a few poses, bounce a collectible or question block, and animate a concise HUD event. Use discrete poses rather than fractional subpixel drift.

## Transition

Reveal pixel rows, assemble tiles or make a game-like screen change.

## Failure cases and adaptation

Smooth scaling and antialiasing blur the pixel grid. Overlapping outlined pieces need explicit occlusion order. Essential text needs a compatible bitmap or deliberately rasterized font, and sufficient logical pixels per character.

Parameters above are upstream study values at approximately 1920×1080 unless stated otherwise. Scale them to the delivery format and check the actual result. These are English production adaptations, not bundled renderers or claims of validated AnimaGuru implementations.

Adapted from [the upstream card](https://github.com/alchaincyf/huashu-art-motion/blob/2571ee0a9a0467c4d99e935ea9e0fadda19210b0/references/%E9%A3%8E%E6%A0%BC%E9%85%8D%E6%96%B9/14_8bit.md) under the [MIT license](../../LICENSE). See [provenance](../sources.md).
