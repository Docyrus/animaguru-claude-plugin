# Screen mapping

Record a map for each screen: source path, intrinsic width/height, displayed crop, placement, scale, control bounds, target center, resulting state and callout text. Coordinates must name their space: intrinsic screenshot pixels, crop-local pixels or film pixels.

For an unrotated crop whose intrinsic top-left is `(cropX, cropY)`, a uniform scale `s` and film placement `(left, top)`, the target is:

```
filmX = left + (sourceX - cropX) * s
filmY = top  + (sourceY - cropY) * s
```

Account for letterboxing when fitting an image into a frame. CSS dimensions and device pixel ratio are not intrinsic screenshot coordinates. A normalized target `(u, v)` maps to `(u * sourceWidth, v * sourceHeight)` before cropping and projection. For rotated or nested containers use the actual scene transform; do not manually duplicate only some of its operations.

Inspect the target over the screenshot at output resolution. Save its control bounds as well as the click point to make the target easy to audit. When cropping or panning changes, verify the target remains visible and inside its control. Derive click ripples and focus masks from the same target data.

For recordings, await decoded frames on seek as required by the shared capture API. Use the recording's actual cursor or an authored replacement consistently. Hide duplicate cursors. Keep every screen and annotation inside the Pixi canvas so the player and the MP4 show the same sequence.
