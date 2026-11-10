---
name: animaguru-pixel-art-animation
description: Build animated videos using crisp pixel assets, limited palettes, sprite timing and tile-based scenes. Use for the Pixel Art Animation visual style in an AnimaGuru video workspace.
disable-model-invocation: true
---

# Pixel Art Animation

Create a deliberate pixel grid and movement language. The user's Explainer, Advertisement or General Video brief supplies the story, mood and audience; retro game references are optional.

## Establish the direction

Follow the sibling `animaguru-video` category → style → quick interview flow before new production. Reuse supplied choices and briefs; honor an explicit request to skip the interview. Share [the style preview](https://animaguru.com/animation-styles#pixel-art-animation). Include missing visual choices in the shared interview:

- What pixel density, palette and reference era or contemporary treatment fit the project?
- Which characters, objects, environments or interface elements are needed?
- Should movement be tightly stepped or smoother while preserving crisp pixels? Should text be pixel-styled or clean editorial type?

## Design and build

- Read `animaguru` and use its current `pixel` style for generated artwork when useful. Keep subject scale, outline thickness and palette consistent across assets. An image that merely resembles pixels may still contain inconsistent cell sizes; inspect the actual result.
- Read `pixijs`, assets, sprite and text guidance. Choose a logical scene resolution from the delivery dimensions and desired pixel size. Prefer integer enlargement in the final export; plan padding or composition if dimensions do not divide cleanly.
- Use nearest-neighbor texture sampling for pixel assets. Preserve that choice on spritesheet textures, render textures and any intermediate buffers. Avoid smoothing at one hidden compositing step.
- Quantize positions in logical coordinates, including camera transforms. Applying rounded sprite positions while a parent moves fractionally still causes shimmer. Make deliberate exceptions for typography or effects only when the brief supports them.
- Use pixel-aligned masks and transitions. Arbitrary rotation, skew and noninteger scale change the pixel grid; use authored directional frames or deliberate grid-snapped transformations when crispness matters.
- Set sprite pose cadence independently of the delivery fps. Compute the selected pose from absolute time; respect holds, event timing and loop boundaries. Do not advance animated sprites on a separate uncontrolled ticker during export.
- Use local bitmap fonts or an appropriately rendered font with sufficient glyph coverage. Keep labels readable at phone size and reconsider dense wording instead of shrinking it into noise.
- Treat palette cycling, tile reveals and pixel wipes as optional transition tools. Seed particles once, snap them to the grid and keep visual noise subordinate to the subject.
- Register actual spritesheets, backgrounds, text and effects in the resource timeline. Keep essential words and numbers authored rather than baked into generated artwork.

## Review and completion

Follow `animaguru-video` for audio and export. Inspect at 100% and integer magnification for blurred edges, inconsistent pixel size, atlas bleed and camera shimmer. Play full motion and test loops plus arbitrary seeks. Deliver coherent pixel assets, explicit logical/output dimensions and the finished film as an MP4.

## Additional visual treatments

Read [the material and motion variants](references/variants.md) when the brief calls for a specialized treatment. Choose the relevant recipe without imposing its example story.
