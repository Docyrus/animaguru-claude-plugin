# Machine Anatomy production recipe

The workspace includes an executable original study in `src/studies/scenes.ts`, selected with `machine-anatomy`: one dispensing head on a gantry fills a 4 × 4 tray of wells in a serpentine pass while the card's readout counts the well and the millilitres dispensed. The figure is built in `src/studies/anatomy-plotter.ts` with the bundled kit; the gallery preview renders the same module at a larger size. Its drawing commands are consumed by `src/studies/pixi-renderer.ts`. All study copy lives in `shared/locales/en/style-studies.json`.

In an untouched starter, run `npm run example -- machine-anatomy`, then `npm run dev`. The command refuses to replace an authored film, retains starter backups in `production/example-backup/`, and writes an 8-second study with its own resource tracks. `npm run export:html` and `npm run export:mp4` use this installed film normally. To use the recipe inside an existing film, import `plotterFrame()` or the kit directly and compose the figure into the project's timeline instead of running the installer.

## The kit

`src/kit/anatomy/iso-kit.ts` is the core of the Anatomy kit, vendored unchanged with its MIT `LICENSE` beside it. World points are `[x, y, z]` with z up; paths come back as SVG `d` strings in screen pixels.

```ts
import { Graphics } from "pixi.js";
import * as K from "./kit/anatomy/iso-kit"; // "../../../runtime/kit/anatomy/iso-kit" from animations/NAME/src/
import { drawDots, drawLine, drawSolid } from "./kit/anatomy/pixi";

const PLATE = { x: -120, y: -70, w: 240, d: 140, r: 8 };
const P = K.fitProjection(K.boxCorners(PLATE, -16, 90), 1280, 620, { pad: 24, azimuth: 45 });
const base = new Graphics();
drawSolid(base, K.slabOf(PLATE, -12, 12, P, 8, 1.6), { tone: "mid", width: 1.2 });
drawLine(base, K.planOutline(K.insetPlan(PLATE, 5), 0, P), { tone: "faint", width: 1 });
drawDots(base, K.pointsAt(K.corners(PLATE, 10).map(([x, y]): K.Point3 => [x, y, 0]), P), { size: 1.1 });
```

| Need | Kit calls |
|---|---|
| Camera and depth | `fitProjection`, `boxCorners`, `iso`, `depthOf`, `screenRise`, `axisVector`, `towardViewer` |
| Solids | `slabOf(plan, z, h, P, steps, bevel)`, `cylinder(cx, cy, r, z, h, P, steps, bevel)`, `extrude(ring, z, h, P, { convex })`, `insetPlan`, `corners` |
| Lines on faces | `planOutline`, `ring`, `onTop`, `lineOnTop`, `segment`, `rise`, `sideSeam`, `sideArc`, `sideRing` |
| Parts | `topTicks`, `sideTicks`, `radialTicks` (rulers and dials), `knurl`, `coil` (back and front halves), `dotGrid`, `haloOf` |
| Faces | `topMatrix`, `sideMatrix` map flat local coordinates onto a top or side face, for a screen, a dial face or engraved text |

`drawSolid` paints like the kit's `solidSvg`: paper fill, four side shades, top, crease and bevel, then the outline; a `lit` solid gets the white face and the lit edge. Widths are screen pixels: about 1 px at 1280 wide and 1.5 px at 1920, a little heavier for the lit part. For the soft shadow under the base, fill `haloOf(...)` into its own Graphics with a `BlurFilter` and the palette's `halo` colour at `haloOpacity`. Move a rigid part by rebuilding it at its new position, or by translating a Graphics built at rest by `axisVector(P, [dx, dy, dz])`; rebuild a part whose shape changes (a compressing coil, a turning needle). The kit's SVG and HTML helpers (`solidSvg`, `figureSvg`, `plateHtml`, `ISO_CSS`) remain available for stills and overlays but are not needed in Pixi.

Not bundled: the upstream lathe (turned parts on any axis), tube (pipes and cables), geometry audit, WebGL and 3D modules. Draw round parts on vertical axes with `cylinder`, keep cables and pipes few, short and clear of the subject, and prove order and clearance with 4× frames instead of the audit.

## Adaptation decisions

- An interactive figure becomes timed choreography. Its idle tour is the film's timeline, pointer input becomes scripted beats, and the readout is computed each frame from the same model and schedule as the parts.
- The card corners (Fig n, title, hint, readout) and the caption are editable, localized text. At 1280 wide, 14–16 px monospace reads; keep the drawing itself free of words.
- A series of figures shares one camera, one scale and one palette. Cut or crossfade between figures, or push into one mechanism and settle.
- Light paper is the default; for a dark plate use `ANATOMY_PALETTES.dark` everywhere and never mix theme tones.

The study is silent, original procedural art built to demonstrate construction, tones, order and motion. It makes no product claims. Configure an original machine, numbers, palette, scene sequence, duration and soundtrack from the brief. Use `src/studies/timing.ts` for deterministic easing, springs and cue helpers. `window.animaguru.texts` exposes visible study text bounds for `npm run review`; inspect the actual frames as well.

## Sources and attribution

Adapted from [Anatomy](https://github.com/wheresryan22/anatomy) by Ryan ([@wheresryan22](https://x.com/wheresryan22)), MIT, pinned at commit `1482e8469b0a9e0d8cc18ea2740a01423d29ae80`. `iso-kit.ts` is a verbatim copy; the craft and workflow guidance is condensed and adapted for film. The study figure, its gallery preview, the palette module and the PixiJS adapter are original AnimaGuru work. The workspace's `VIDEO-STYLE-NOTICES.txt` and `src/kit/anatomy/LICENSE` preserve the notice.

- [SKILL.md](https://github.com/wheresryan22/anatomy/blob/1482e8469b0a9e0d8cc18ea2740a01423d29ae80/SKILL.md)
- [references/craft.md](https://github.com/wheresryan22/anatomy/blob/1482e8469b0a9e0d8cc18ea2740a01423d29ae80/references/craft.md)
- [references/motion.md](https://github.com/wheresryan22/anatomy/blob/1482e8469b0a9e0d8cc18ea2740a01423d29ae80/references/motion.md)
- [kit/iso-kit.ts](https://github.com/wheresryan22/anatomy/blob/1482e8469b0a9e0d8cc18ea2740a01423d29ae80/kit/iso-kit.ts)
