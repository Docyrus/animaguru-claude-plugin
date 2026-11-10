# Storytime pose acting

Use for a first-person experience, a recurring original narrator and a script with reaction beats. Voice carries the story; the animation supplies decisive poses, expressions and silence. Data-heavy or impersonal material may need another grammar.

## Visual structure

Keep a recognizable character with a small pose/expression library. Medium shots can leave space for the object being discussed; a reaction close-up removes background competition, while a sudden wide shot can communicate helplessness. Characters have stronger contours and contrast than simplified backgrounds. Do not copy the upstream author’s mascot or a creator’s identity. Generate consistent character sheets through AnimaGuru when detailed human acting is needed; intentional simple geometric figures are also valid when they fit the brief.

## Motion and timing

Change a pose quickly, around .1 s as a starting point, then truly hold. A small contact-anchored compression and short decaying settle can accent the switch. Choose a limited mouth system or proper visemes according to quality needs. Audio RMS can drive open/half/closed mouths at about 12 updates/s, but is not phoneme-accurate lip sync. Use deterministic blinks and gaze that point at the spoken subject. Stop talking during actual silence.

## Camera and transitions

Hard cuts dominate. Use a jump to a reaction close-up, an occasional glance-motivated whip, or an over-shoulder screen shot. Wide and close views must refer to the same room geometry. Put a reaction in a real gap in the narration—often .8–1.5 s is useful—rather than immediately speaking over the joke. Leave the final reaction long enough to land.

## AnimaGuru adaptation and review

Use actual sprite metadata and feet/hand anchors. Match silhouettes across poses and normalize apparent height without stretching anatomy. Do not dissolve unrelated poses into double bodies. A high static-frame percentage may be intentional; review the sharp pose changes and story beats instead of forcing everything to float. Check scene edges at maximum camera distance, matching subtitle cuts, prop contact, recognition from behind and actual audio/mouth timing.

Adapted in English from [the upstream grammar](https://github.com/alchaincyf/huashu-art-motion/blob/2571ee0a9a0467c4d99e935ea9e0fadda19210b0/references/%E5%8A%A8%E7%94%BB%E8%AF%AD%E6%B3%95/y4_storytime.md) under the [MIT license](../../LICENSE). Numerical timings are starting points from source studies, not universal rules or current AnimaGuru benchmarks. See [provenance](../sources.md).
