---
name: animaguru-animated-data-visualization
description: Build animated chart videos from supplied data with traceable values, honest scales and readable comparisons. Use for the Animated Data Visualization visual style in an AnimaGuru video workspace.
disable-model-invocation: true
---

# Animated Data Visualization

Use charts, numbers and annotations as the visual language of an Explainer, Advertisement or General Video film. The brief determines the question and narrative; the data determines which claims the film can support.

## Establish the direction

Follow the sibling `animaguru-video` category → style → quick interview flow before new production. Reuse supplied answers and completed briefs; honor an explicit request to skip the interview. Share [the style preview](https://animaguru.com/animation-styles#animated-data-visualization). Include missing essentials in the shared interview:

- What data file or source should be used, and what do its units, categories and dates mean?
- Which comparison or finding matters, and is there an approved claim to verify?
- What visual density, palette, labeling and source attribution suit the audience and placement?

## Establish the data contract

Read [the data contract](references/data-contract.md) when ingesting data and before delivery. Preserve the source, transformations and chart-ready values in `production/`. If real data is missing, request it or use conspicuously labeled illustrative data with the user's agreement. Do not invent business metrics to fill a scene.

## Design and build

- Read `pixijs`, graphics and text guidance. Choose chart geometry for the relationship: bars for categorical magnitude, lines for ordered time, dots for comparisons, scatterplots for relationships. Record a short reason for the choice.
- Keep bar baselines at zero; use meaningful, explicit domains for other charts. A scale change needs a visible transition or annotation. Use common scales for direct comparisons. Preserve negative values, missingness and uncertainty where relevant.
- Directly label essential values and units. Reserve space for source/date notes. Choose accessible highlight colors; reinforce distinctions with labels or shapes.
- Stage the chart: establish its frame, reveal series, then emphasize the supported comparison. The story can take any order suited to the brief, but the visualization must not suggest evidence the source lacks.
- Derive positions, displayed numbers and annotations from one chart model. Count-up values are temporary interpolation states, not observations; finish at the exact formatted source value. Do not smoothly interpolate discrete observations in a way that implies measured intermediate data.
- Keep label layout stable while marks animate. Compute text bounds and chart domains before capture. Avoid fake depth and decorative movement that distorts perceived magnitude.
- Generate charts in code. AnimaGuru may supply authorized narration, music or contextual illustrations; generated imagery must not contain the authoritative plotted numbers.
- Follow the shared absolute timeline and resource metadata contract, registering series, annotations and captions separately where useful.

## Review and completion

Verify every final plotted value and claim against the transformed data programmatically, then manually check representative extremes, missing values and at least five values when available. Inspect chart transitions, label collisions and small-screen legibility. Deliver the source and transformation record, chart-ready data, validation notes and the finished film as an MP4. Follow `animaguru-video` for MP4 delivery.

## Additional visual treatments

Read [the material and motion variants](references/variants.md) when the brief calls for a specialized treatment. Choose the relevant recipe without imposing its example story.
