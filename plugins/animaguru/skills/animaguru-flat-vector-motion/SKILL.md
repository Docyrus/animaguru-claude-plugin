---
name: animaguru-flat-vector-motion
description: Build animated videos from flat geometric illustrations, icons, connectors and shape transitions. Use for the Flat Vector Motion visual style in an AnimaGuru video workspace.
disable-model-invocation: true
---

# Flat Vector Motion

Create a coherent language of shapes and intentional movement. The brief supplies subject, story, audience and pacing; this style supports Explainer, Advertisement and General Video projects.

## Establish the direction

Use the sibling `animaguru-video` category → style → quick interview flow for new films. Reuse supplied answers and completed briefs; honor an explicit request to skip the interview. Share [the style preview](https://animaguru.com/animation-styles#flat-vector-motion). Fold missing choices into the shared interview:

- Which palette, geometric language and illustration references match the brand?
- Should movement feel precise and restrained, soft and friendly, or energetic?
- Are icons or illustrations supplied, and are there shapes or visual metaphors to preserve or avoid?

## Design and build

- Read `pixijs` and its graphics, container and text guidance. Set shared stroke widths, corner radii, proportions and spacing before creating scenes. Keep perspective, icon detail and illustration weight consistent.
- Build simple geometry in PixiJS or SVG. Use AnimaGuru's `vector` style for complex illustrations when useful; inspect the current catalog and generation guidance. Generated vector-looking images remain bitmaps unless the delivered file is actually vector. Keep critical labels editable.
- Compose with a clear focal element and supporting shapes. Use size and whitespace to distinguish information levels. Choose flat fills and limited shading according to the brief.
- Connect scenes through shared shapes or layout anchors: a circle becomes a node, a card expands into a panel, or a connector guides the next reveal. Avoid arbitrary transitions unrelated to the composition.
- Use anticipation, travel and settling deliberately. Stagger related elements while allowing each composition to resolve. Motion should explain grouping, direction or emphasis.
- Interpolate authored geometry only when topology and point ordering match. For unrelated silhouettes, use a mask, matched transform or crossfade rather than an unstable point-to-point morph. Check the intermediate silhouettes.
- Cache static drawing where useful and animate transforms. Rebuild geometry only when its shape actually changes; do not regenerate assets during playback. Keep effects within the film's own player, so the MP4 export and hosted playback show them.
- Follow the shared deterministic timeline and resource metadata contract. Derive connector progress, masks and transforms from absolute time, including on backward seeks.

## Review and completion

Follow `animaguru-video` for source records, audio and export. Check outline consistency, seam-free masks, transition midpoints and readable holds at the intended viewing size. Confirm that essential meaning survives a still frame and silent playback when required by the brief. Deliver consistent vector styling, editable text, synchronized resources and the finished film as an MP4.

## Additional visual treatments

Read [the material and motion variants](references/variants.md) when the brief calls for a specialized treatment. Choose the relevant recipe without imposing its example story.
