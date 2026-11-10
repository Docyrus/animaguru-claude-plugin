# Palette and pixel-depth techniques

Choose one coherent treatment from the brief; these are visual/motion recipes, not mandatory stories. They apply to Explainer, Advertisement and General Video.

## Indexed palette changes

Use palette indices with explicit protected colors for semantic emphasis. Palette remaps must preserve useful warm/cool and shadow ranges rather than crushing a scene to black. Dither transitions should remain anchored to the logical pixel grid.

## Pixel diorama in 2.5D

Match sprite texel density to prepared environment planes. Keep nearest sampling, integer presentation scale and deliberate sprite cadence; light/camera may be continuous if the finish calls for it. The current treatment uses prepared layers; free 3D lighting and physical focus remain deferred.

## Output inspection

Inspect tile edges, outlines and palette transitions at actual export scale. Quantize parent camera offsets as well as sprites when the selected pixel treatment requires a fixed grid. A fractional CSS canvas size can blur the final display even when texture sampling is nearest.

Use the bundled absolute-time helpers in `src/studies/timing.ts` where appropriate. Keep actual resources and cues in the timeline, then inspect cold seeks, full-speed motion and exported frames. The shared video skill governs interviews, generation scope and delivery.
