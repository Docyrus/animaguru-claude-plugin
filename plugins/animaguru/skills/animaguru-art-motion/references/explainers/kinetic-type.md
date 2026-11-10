# Kinetic typography

Use words as performers for an opening, list structure, quotation, key number or chapter transition. Long explanatory passages usually need images, evidence or diagrams between typographic sections. Design English copy by measured width and reading time; do not import Chinese character-count limits literally.

## Visual structure

One dominant word or short phrase, one supporting line and at most one supporting evidence object make a useful starting point. A roughly 3:1 main/support size ratio creates hierarchy. Use a chapter palette and an intentional alignment grid. Maintain margins and safe areas at the real aspect ratio. Vary page structures before the film starts feeling like repeated title slides.

## Motion and timing

Land the main phrase on a spoken stress or measured musical beat. A brief scale slam, around .35 s settling from roughly 1.7×, can establish emphasis. Supporting text can rise through a mask over .3–.35 s; a card can move in over .4 s. Reveal one focus at a time. An exit can be shorter than entry, around .18 s. Once readable, type stays fixed. Background motion or a tiny beat pulse is optional, with no need to make the whole film continuously drift.

## Camera and transitions

Expand a meaningful letter or colored shape into the next background, use a band wipe, or move across a continuous layout. Schedule the visible reveal on the accent, rather than scheduling only the transition’s first frame: transitionStart = accentTime − revealFraction × transitionDuration. For a .45 s transition revealing at .55, start about .2475 s before the accent. Check the actual rendered reveal; easing changes its perceived arrival.

## AnimaGuru adaptation and review

Use editable local type, font measurement, masks and the shared audio cue sheet. Keep a progress track in screen space so it does not move with a page. Essential wording should never depend on generated lettering. Review reading time after the last character finishes, final hold, the gap to an evidence card, glyph coverage and alignment between text impact and sound. For narration, prioritize the stressed word; for music, use the measured beat grid. Do not add an effect or sound to every small element if it competes with the spoken message.

Adapted in English from [the upstream grammar](https://github.com/alchaincyf/huashu-art-motion/blob/2571ee0a9a0467c4d99e935ea9e0fadda19210b0/references/%E5%8A%A8%E7%94%BB%E8%AF%AD%E6%B3%95/y5_kinetic_type.md) under the [MIT license](../../LICENSE). Numerical timings are starting points from source studies, not universal rules or current AnimaGuru benchmarks. See [provenance](../sources.md).
