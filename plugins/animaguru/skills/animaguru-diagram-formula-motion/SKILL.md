---
name: animaguru-diagram-formula-motion
description: Build animated diagrams, plotted geometry and equation transformations for visual explanation. Use for the Diagram and Formula Motion visual style in an AnimaGuru video workspace.
disable-model-invocation: true
---

# Diagram & Formula Motion

Make relationships visible through nodes, paths, geometry and symbols. Use the user's Explainer, Advertisement or General Video brief to determine the subject and depth; equations are optional.

## Establish the direction

Follow the sibling `animaguru-video` category → style → quick interview flow for a new film. Reuse supplied choices and existing briefs; honor an explicit request to skip the interview. Share [the style preview](https://animaguru.com/animation-styles#diagram-formula-motion). Include missing choices in the shared interview:

- Which concept and source should guide the explanation, and what knowledge can viewers assume?
- Prefer abstract diagrams, plotted geometry, equations, or a combination?
- Which notation, color meanings and degree of visual detail should remain consistent?

## Design and build

- Read `pixijs`, graphics, math and text guidance. Identify the quantities, entities and relationships before animating them. Maintain a small visual vocabulary so the same color and shape retain their meaning.
- Keep semantic objects stable across transitions: a node changes position but keeps its identity; an equation term becomes a labelled segment; a selected parameter changes the corresponding plot. Use explicit object IDs for these relationships.
- Use native graphics for simple diagrams and graphs. For typeset mathematics, create local SVG assets with an appropriate math renderer and import them into the Pixi canvas. Verify that fonts or glyph outlines are included. DOM-only formula overlays will be missing from canvas captures.
- Lay out equations as meaningful tokens or groups when individual terms must move. Preserve fraction rules, superscripts, signs and spacing. Ordinary text splitting does not understand mathematical structure.
- Distinguish equality-preserving algebra, substitution, approximation and changes of representation. Use the correct signs and keep stated domains and units consistent. Validate formulas and graph samples numerically where possible; consult authoritative sources for unfamiliar claims.
- Animate relationships at a readable pace: reveal a connection, move the relevant quantity, then allow the viewer to see the resolved state. Do not morph unrelated symbols in ways that imply a false equivalence.
- Compute plots from their functions or supplied data. Choose domains that expose the intended behavior; split paths around discontinuities and undefined values. Use one world-to-screen mapping for geometry and labels.
- AnimaGuru can provide authorized supporting illustrations and audio. Keep authoritative equations, values and diagrams authored and inspectable.
- Drive all states and parameter changes from absolute timeline time and update resource intervals. Use the existing PixiJS player and export pipeline; additional rendering tools may prepare assets without replacing the player.

## Review and completion

Check each transformation's meaning as well as its appearance. Inspect formula baselines, label collisions, graph endpoints and discontinuities at transition boundaries and small viewing sizes. Match visual events to the real narration where present. Follow `animaguru-video` to deliver source expressions, diagram data, validation notes and the working HTML5 film; export MP4 when requested.

## Additional visual treatments

Read [the material and motion variants](references/variants.md) when the brief calls for a specialized treatment. Choose the relevant recipe without imposing its example story.
