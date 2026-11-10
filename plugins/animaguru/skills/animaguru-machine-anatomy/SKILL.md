---
name: animaguru-machine-anatomy
description: Build Machine Anatomy visuals and motion in an AnimaGuru PixiJS video workspace, explaining an idea as a crafted isometric machine of many small shaded parts in a framed figure card with a live readout. Use when this visual style is chosen for an explainer, advertisement or general video.
disable-model-invocation: true
---

# Machine Anatomy

Explain an idea by building it as a real, working object. A cache that skips repeated work becomes a pin-tumbler lock that turns only when every pin matches; one service shared by many customers becomes a gantry whose single head visits every well. Viewers understand the idea because they recognise the machine. Dozens of small, precise, four-tone solids sit in a framed figure card with a title and a live readout, and every number on screen comes from the model that moves the parts. Subject, audience, tone and story come from the user's brief. This style supports Explainer, Advertisement and General Video. It is adapted from the open-source Anatomy skill (MIT).

## Establish direction

Follow sibling `animaguru-video` for purpose → style → compact interview before new production. Reuse explicit choices and completed briefs; honor a requested interview skip. Share [the style gallery](https://animaguru.com/animation-styles#machine-anatomy). Fold missing visual questions into the shared interview:

- Which idea, product or process should the machine embody, and which real numbers (sizes, counts, rates, thresholds, prices) must the readout show?
- Light paper or dark plate? Monochrome with one lit accent, or one brand colour where colour carries meaning?
- One figure the camera explores, or a short series (Fig 1, Fig 2…) at one scale?

## Invent the machine

Write the concept and the parts list before any geometry; most of the quality is decided here.

1. **Truth first.** Collect the true numbers and behaviour. Write them as one small pure model, a function of absolute seconds, that drives the motion, the readout and the captions.
2. **Invent the object.** Choose a machine, instrument, tool or piece of furniture whose working maps one-to-one onto the idea, and say in one sentence what moves and what that motion means. Never boxes, arrows and labels; never a traced reference image.
3. **Parts list.** At least 40 parts, grouped: base (plate, feet, groove, corner screws, label plate, ruler strip), structure (posts, rails, frame bars, end stops), mechanism (carriage, bushings, springs, plunger, needle), controls (knurled knob, thumb screw) and the subject, the one lit part. Each part rests on another part and has a job.
4. **Plan the world.** World units with x and y on the floor and z up; plans as rounded rectangles. Camera azimuth 45° (35–60° to show the long side) and elevation 30° (higher to look into something open). Fit the projection to the full travel of every moving part so nothing leaves the card.

Read [craft](references/craft.md) before designing: tones, painter's order, part recipes, exploded views, faces and screens, and the faults that make a figure read as a diagram.

## Build the look and movement

Read `pixijs` and the relevant Graphics and Container skills. The workspace bundles the Anatomy geometry kit in `src/kit/anatomy/` (root `runtime/kit/anatomy/` in a multi-animation workspace): `iso-kit.ts` for the camera, solids and parts, `palette.ts` for light and dark tones, and `pixi.ts` with `drawSolid`, `drawLine` and `drawDots`. The [production recipe](references/recipe.md) covers the API, the bundled study and what is not bundled.

- Build static geometry once; rebuild only what moves or changes shape. Paint back to front, bottom to top: sort repeated parts with `depthOf`, split anything that wraps another part into back and front halves, and draw each moving part in the slot where it physically sits for its whole travel.
- Let the kit shade: four side tones by facing plus a lighter top. Base `lo`, structure `mid`, subject `hi`, and exactly one `lit` part, the one the viewer should watch now. Colour only where colour is the subject.
- Every line ends on something: a face, another line or a terminal dot. No leader lines, balloons, dimension arrows or floating labels in the drawing. Words go in the card corners (Fig n, title, hint, readout) or the caption, plus at most one tiny engraved label.
- Motion is calm and true: eased travel, critically damped or real springs, one event at a time and holds long enough to read the readout. Keep every position a function of absolute seconds so seeking is exact. A camera push may reveal a mechanism, then settles.
- Essential type stays editable and localized. AnimaGuru-generated media can supply a backdrop, a product inset or sound; the machine itself is authored geometry.

## Review and delivery

Zoom in like a critic. Save frames at 2–4× over every junction (feet, rails, carriages, collars, the subject) in each resting pose and mid-move. Nothing passes through anything, no line stops in mid-air, the painter's order holds through every frame of the motion, the readout matches the parts, and the figure still reads at phone size. Then ask whether it is instantly a real object, rich in small parts with volume, with no bare face or empty corner, and add the real parts that are missing. Check representative full-resolution frames, moving playback, desktop/mobile fit and cold seeks. Follow `animaguru-video` for production records, audio mixing and MP4 delivery. Describe the method accurately as projected 2.5D solids; physically rendered 3D remains deferred.
