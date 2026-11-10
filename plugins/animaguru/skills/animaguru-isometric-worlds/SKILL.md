---
name: animaguru-isometric-worlds
description: Build dimensional isometric scenes with assembling objects, connected stations and controlled depth. Use for the Isometric Worlds visual style in an AnimaGuru video workspace.
disable-model-invocation: true
---

# Isometric Worlds

Compose a small dimensional world using a consistent parallel projection. Objects, architecture, machines or abstract blocks can all carry the user's message. Story and audience come from the Explainer, Advertisement or General Video brief.

## Establish the direction

Follow the sibling `animaguru-video` category → style → quick interview flow for new films. Reuse supplied choices and briefs; honor an explicit request to skip the interview. Share [the style preview](https://animaguru.com/animation-styles#isometric-worlds). Add missing visual choices to the shared interview:

- Abstract blocks, miniature environments, product components, or supplied illustrations?
- Flat geometric surfaces or textured illustration? What palette and level of detail?
- Is the camera largely fixed, or should it travel across connected areas?

## Design and build

- Read `pixijs`, graphics and scene-container guidance. Define a common world grid and projection before positioning assets. A useful basis is screenX = originX + (x − y) × tileWidth / 2 and screenY = originY + (x + y) × tileHeight / 2 − z × heightScale. Choose the ratio for the desired projection and use it throughout.
- Author simple blocks, platforms and paths in graphics. AnimaGuru `vector` or `painted` assets can supply more detailed objects with a clearly specified matching view. There is no dedicated isometric preset in the current catalog; inspect available styles and reference imports rather than inventing a style ID.
- Maintain the same visible faces, vanishing directions and lighting across assets. Place object pivots at ground contact points. Labels normally remain screen-aligned for legibility.
- Plan occlusion from the world coordinates. Sorting by ground depth is a useful starting point; wide overlapping objects may need separate front/back layers or explicit ordering. A single sprite cannot resolve every interpenetration correctly.
- Animate blocks rising, components assembling, paths revealing and markers travelling between anchors. Keep a marker attached to the projected path as the camera moves. Hold the receiving element when a connection reaches it.
- Use scaled or translated scene containers for controlled camera travel. Full camera orbits require additional views or a 3D approach and should not be promised from one flat illustration.
- Reserve readable space for labels and cues. Detail should survive the target viewing size. Use anchored contact shadows when they clarify depth.
- Drive all world positions, camera motion, depth decisions and connector progress from the absolute timeline; register real scene resources and intervals.

## Review and completion

Use `animaguru-video` for audio, records and exports. Check every connection, ground contact, occlusion and camera extreme. Inspect each assembled state at mobile size and verify labels never obscure the event they explain. Deliver a consistent projection, readable motion and the working HTML5 film; export MP4 when requested.

## Additional visual treatments

Read [the material and motion variants](references/variants.md) when the brief calls for a specialized treatment. Choose the relevant recipe without imposing its example story.
