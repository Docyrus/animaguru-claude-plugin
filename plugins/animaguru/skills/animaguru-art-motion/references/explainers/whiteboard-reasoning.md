# Whiteboard reasoning

Choose a continuous argument map or a sequence of separate paper pages. A moving-camera RSA-like board and a fixed-camera page-cut explanation are different grammars; keep the chosen spatial model consistent.

## Visual structure

Plan the final diagram before the drawing order. Use a visual metaphor or relational sketch, not a transcript handwritten in full. An off-white board, near-black line and one accent color are enough. A line width near .6–.7% of frame height is a useful source starting point; make hatching lighter. Define solid/dashed/dotted semantics once. Existing marks persist until explicitly erased or left outside the viewport.

## Motion and timing

Measure each stroke by arc length, derive its duration from pen speed, and return the reveal frontier as the pen-tip position. If revealing a complex image by a zigzag mask, attach the pen to that same frontier. Do not reveal several unrelated lines at once under a stationary hand. Source drawing tends to follow the spoken phrase slightly, often about .5 s; adapt English handwriting speed and phrase length to the measured voice. Complex art can be pre-drawn and discovered rather than drawn in real time.

## Camera and transitions

Fit the current drawing bounds with margins. Small smooth board moves retain substantial overlap with the previous argument. Use a whip only for a purposeful move to a distant area. A final pullback reveals the overall argument map and holds. A page-based version uses cuts to new pages instead. Keep board marks and pen in world space; keep any paper/erase texture scaled appropriately for the viewport.

## AnimaGuru adaptation and review

Use kit line primitives and local analytic path timing; generated hand art is optional if a hand helps the brief. The hand exits when idle and must not cover the conclusion. Print planned stroke completion times to catch a drawing that continues after the camera leaves. Check pen/frontier alignment, no cropped old words at edges, clear line semantics, connected argument groups and a real final reading hold. Whiteboard rendering alone does not establish a claim of better learning outcomes.

Adapted in English from [the upstream grammar](https://github.com/alchaincyf/huashu-art-motion/blob/2571ee0a9a0467c4d99e935ea9e0fadda19210b0/references/%E5%8A%A8%E7%94%BB%E8%AF%AD%E6%B3%95/y3_whiteboard.md) under the [MIT license](../../LICENSE). Numerical timings are starting points from source studies, not universal rules or current AnimaGuru benchmarks. See [provenance](../sources.md).
