# Machine Anatomy craft

What makes a figure read as a crafted object rather than a diagram, condensed from the Anatomy skill's craft guide and adapted for film. `K` is the bundled kit (`import * as K from "./kit/anatomy/iso-kit"`) and `P` its projection.

## What crafted means

1. **A real object you could build.** The viewer names it at a glance: a test rig, a dial gauge, a chest of drawers, a gantry plotter, a lock. It is invented for the subject, never traced.
2. **Many small, precise parts.** A single figure has 30–60 solids; a hero subject can carry far more. Density comes from structure (feet, rails, stops, bushings, knobs, screws), not texture. Every part rests on another, aligns to its neighbours and has a job.
3. **Volume.** Real thickness, four shaded sides, lighter tops, bevels that catch light and a soft halo under the base.
4. **Calm.** Thin lines, a restrained palette, one lit accent and motion slow enough to follow.
5. **Truth.** The readout shows correct, live numbers and the motion follows the model: real sizes, thresholds and spring behaviour.

| Idea | Machine |
|---|---|
| One shared resource serving many requests | A gantry plotter: one head visiting 16 wells |
| Work skipped when nothing changed | A pin-tumbler lock: when every pin matches, the plug turns |
| Items of different sizes | A chest of drawers, each as deep as its item |
| A queue with limited capacity | A coin chute with a fixed number of slots and a gate |
| A rate limit | A token hopper refilled by a metered wheel |
| Settings that interact | A test rig with springs, a probe and a dial gauge |

## Faults that get figures rejected

- **Abstract stacks.** Floating plates or tiles standing for "layers" read as nothing. Make them drawers, trays in a rack, plates on guide pillars or cards in a holder.
- **One big plain slab.** Break it into a base, a carriage and parts; add a groove, screws, a ruler and a label plate.
- **Diagram furniture.** Leader lines, numbered balloons, dimension arrows, hatching, dashed hidden edges and floating labels belong in the caption.
- **Lines that stop in mid-air.** Connectors that end short of a part, creases that stop before a corner, ticks floating on a bare face.
- **Wireframes.** See-through boxes whose back edges show. Every solid is filled in paper colour and hides what is behind it.
- **Colour everywhere.** Monochrome unless colour is the subject. A fluid is a tint of the figure's own inks, not a new saturated colour.
- **Words in the drawing.** At most one tiny engraved label on a face.
- **Snapping motion.** Parts that jump to a new value. Ease or spring everything.
- **Things through things.** A cable through a duct, a rod sunk into a block, a part that passes through its neighbour mid-move. Parts meet flush, tangent or rim-on-surface.
- **Textures that stop.** Ribs, rows of bolts, seams and ticks end on a real edge or fade out; they never stop mid-surface.
- **Fixing one frame by eye.** Re-ordering a part until one frame looks right breaks another. Decide order from geometry, then check every pose.

## Part recipes

Draw each recipe's solids in the order listed. Heights in world units, z up.

- **Base plate on feet.** `haloOf(PLATE, -17, 12, P)` blurred under everything; feet at `corners(PLATE, 22)`, sorted by `depthOf`, each a `cylinder` flange (tone `lo`) under a `cylinder` foot (`mid`); `slabOf(PLATE, -12, 12, P, 8, 1.6)` (`mid`); groove `planOutline(insetPlan(PLATE, 5), 0, P)` (`faint`); corner screws at `corners(PLATE, 10)`, a `ring` (`lo`) with a dot.
- **Ruler strip and label plate.** A 0.6-high strip slab (`lo`, no crease) with `topTicks(from, to, 4, 5, edge, 0.6, [2, 3.6], P)`, minor `lo`, major `mid`, rooted on the strip's edge. Label plate: a 0.8-high slab, an inset outline (`faint`), three rule lines of different lengths standing for print, and two screw dots.
- **Seams on a box.** `sideSeam(plan, z, P, steps)` wraps the visible corners and ends on the silhouette; pass the slab's own `steps` and draw it before the outline. A line on one face runs edge to edge.
- **Rails, end stops and a carriage.** Long thin slabs (`mid`, bevel 0.4–0.5) with screw dots; taller stops at both ends; a carriage slab with bushings at its corners, rivets along its front edge and a knurled handle.
- **Post, collar and clamp.** A `cylinder` collar under a slimmer post (no crease), faint `sideArc` seam rings, a clamp block with a thumb screw (neck slab, cylinder, `knurl`).
- **Knurled knob with a pointer.** `cylinder` (`mid`), `knurl` (`lo`) and a `lineOnTop` pointer (`hi`).
- **Coil spring round a rod.** `coil(from, to, [y, z], r, turns, "x", P)` returns `back` and `front`: draw `back` (`lo`), then the rod, then `front` (`mid`). Rebuild it each frame when it compresses.
- **Dial gauge, face up.** A puck `cylinder` (`hi`), knurled bezel band, bezel `ring`, `radialTicks` (minor `lo`, major `mid`), a crown on the side and a needle `lineOnTop` (`lit`) rebuilt each frame.
- **Drawer.** Case slab, a thin front slab with a pull (two posts and a bar) and a label holder; open it by moving along its axis, drawing the box behind the front.
- **Screws and rivets.** Dots 0.4–0.55 units across, `mid`, with a `ring` at plate corners.

## Tones

| Element | Tone |
|---|---|
| Base, feet, floors | `lo` |
| Structure: posts, rails, frame, carriage, case | `mid` |
| The subject | `hi` |
| The part to watch now | `lit` (one only) |
| Grooves, inset outlines, floor grids | `faint` |
| Minor ticks / major ticks / zero mark | `lo` / `mid` / `hi` |
| Creases | `faint`, or `lo` on `hi` parts |

The lit accent can move through a film: when the story's focus moves from the carriage to the gauge, hand the lit tone over with the beat.

## Painter's order

- Base first, then everything resting on it. Within a level, sort by `depthOf(centre, P)`, far before near.
- Split wrapping parts: a spring round a rod, a frame round a carriage. Draw the back half, the inner part, then the front half.
- A moving part keeps its slot in the order for its whole travel. If it could pass in front of and behind the same neighbour, split the neighbour or limit the travel so the order never changes.
- A vertical part passing through a horizontal one (a post through a clamp) is drawn in two segments, below and above.
- Parts higher up cover the tops of the parts they rest on: a beam is drawn after the posts under it, a head after the beam it runs on.

## Camera and composition

- Default azimuth 45°, elevation 30°. Turn the azimuth (35–60°) so the face that carries the mechanism faces the viewer; raise the elevation to look into trays, wells and open boxes.
- Fit with `fitProjection` to every extreme point, including the far ends of every moving part's travel.
- The object fills about 55–65% of the card, centred, clear of the corner labels. A series keeps one scale.
- Check a phone-size frame: if small parts disappear, reframe closer rather than thickening every line.

## Themes

`ANATOMY_PALETTES` holds both token sets. Light (paper) is the default and the reference look. Paper equals the card colour, so fills hide what is behind without showing as patches; the four shades sit about 3% apart; lines run from `faint` to `hi`, with `lit` black on light and white on dark. A cavity (the inside of a box, a well, a recess) gets darker shades as a physical ground. Anything that fades by opacity on paper gets a saturated colour so it does not turn grey.

## Exploded views

An exploded view earns its place when the parts are the explanation. Choose the assemblies the real thing comes apart into, move each along its real direction far enough to clear its neighbours, stagger them so nothing passes through anything in any frame, and keep every part attached to its own assembly. Re-sort depth at each frame if assemblies cross, and hold the apart pose long enough to read.

## Faces and screens

A display, a dial face or engraved text is drawn in the plane of its face (`sideMatrix` or `topMatrix`), clipped to its window, with the recess walls drawn. Text the machine displays is part of the object: fit its widest string in the window with a margin. Content seen through an opening is clipped by the opening and by its own plane.

## Motion

- Ease toward targets with exponential follow or critically damped springs; real springs only where the subject is springy, with stiffness and damping from the model.
- Read the readout from where the parts are, not from their targets, and take a phase word and its number from the same instant.
- One clear event at a time, then a hold. An 8-second figure usually carries one mechanism cycle or one sweep through its states.
- Under a fast cut or social pacing, keep the mechanism readable: shorter holds, never skipped steps.
