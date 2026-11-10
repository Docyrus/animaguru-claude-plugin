# Roman mosaic

Contour-following tesserae, stone variation and grout. Useful for architectural or historical art worlds.

## Material and construction

Compute tile layout once. Follow distance-field contours around important shapes; use a weighted L-infinity Voronoi construction for less mechanical stone boundaries. Tile half-width can start 8–28% above half the nominal spacing so bisectors carve convincing grout. Animate the sampled color or subject beneath the fixed stone layout, rather than changing tile topology every frame.

## Palette

Warm limestone, terracotta, cream and dark stone; use regional stone palettes instead of uniform color noise.

## Motion

Let a volcanic plume, sparks or water move through the tesserae. A border conveyor can loop, provided its baked pattern period matches the actual tile period. Sub-tile color travel may disappear through quantization; moving the tiled border itself makes travel visible. Preserve small facial features with a finer local treatment that does not form a rectangular patch.

## Transition

Flip or replace tiles in a coherent wave, keeping grout visible through the change.

## Failure cases and adaptation

A square grid with random colors reads as pixels. Rebuilding the layout causes boiling. Thin lettering breaks: use broad monoline forms with strokes at least two tesserae wide. Props narrower than roughly three tiles can merge into the scene; the upstream revision used a separate finer-tiled prop inset moving with the hand. Enlarge the dynamic redraw region beyond every affected tile, and keep the same wall layout and tile scale inside and outside that region. Otherwise its boundary becomes a visible patch.

Parameters above are upstream study values at approximately 1920×1080 unless stated otherwise. Scale them to the delivery format and check the actual result. These are English production adaptations, not bundled renderers or claims of validated AnimaGuru implementations.

Adapted from [the upstream card](https://github.com/alchaincyf/huashu-art-motion/blob/2571ee0a9a0467c4d99e935ea9e0fadda19210b0/references/%E9%A3%8E%E6%A0%BC%E9%85%8D%E6%96%B9/04_roman.md) under the [MIT license](../../LICENSE). See [provenance](../sources.md).
