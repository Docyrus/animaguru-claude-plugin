---
name: animaguru-bauhaus-geometry
description: Build Bauhaus Geometry visuals and motion in an AnimaGuru PixiJS video workspace. Use when this visual style is chosen for an explainer, advertisement or general video.
disable-model-invocation: true
---

# Bauhaus Geometry

A kinetic poster in the Bauhaus and Swiss tradition: circles, triangles, quarter discs and bars in red, yellow, blue and black on cream paper move only along a strict modular grid, one exact action per beat, until the composition locks into a finished poster with its type. Order is the point: every move is a whole number of modules, every landing sits on a grid line, and nothing overshoots. Subject, audience, emotional tone and story come from the user's brief. This style supports Explainer, Advertisement and General Video.

## Establish direction

Follow sibling `animaguru-video` for purpose → style → compact interview before new production. Reuse explicit choices and completed briefs; honor a requested interview skip. Share [the style gallery](https://animaguru.com/animation-styles#bauhaus-geometry). Fold missing visual questions into the shared interview:

- What sets the beat (a music track's tempo, or a reading pace), and which moment should land on the downbeat?
- Which words carry the poster (a title, a three-word line, a date or place), and do brand colours replace the primaries or join them?
- Should the finish read as flat screen graphics or as a printed sheet (paper, ink, registration marks)?

## Build the look and movement

Read `pixijs` and the relevant Graphics, Text, Container or Filters skills. Read `animaguru` before generating assets: generation can supply music or narration; the geometry and type are authored code, never a generated image. Discover current models and estimates, respect the user's budget, and reuse completed media.

- The grid is the score. Pick one module and derive every position, size and distance from it (for example 80 px at 1280 × 720: a 14 × 8 field inside an 80/40 px margin, so the frame centre is a grid crossing). Moves are whole modules; sizes are whole or half modules; edges land on lines. Show the construction grid as a pale line, at least while the composition assembles.
- Palette: red `#E03C31`, yellow `#F2B705`, blue `#1E4FA3`, ink black and cream paper `#F1E9DA`, or the brand's own limited set used the same way. Flat fills, no gradients on the shapes. One geometric sans for display (Futura-like), one condensed grotesque for small caps; set type horizontally or vertically on the grid.
- One action per beat (0.5 s at 120 bpm): a slide, a swing, a sweep, a cut-in, a split. Ease with easeInOutQuad or linear over a fraction of the beat (about 0.3 s); never a spring, bounce or overshoot. Bars and rules may grow at constant speed. Cut-ins land exactly on the beat.
- Alternate pivots and make each rotation a quarter or half turn so the shape lands on the grid: a shape's own centre, one of its vertices or corners (a triangle swinging about its right angle, a quarter disc sweeping about its corner like a clock hand), and the frame centre (a whole composition turning 180° maps the grid onto itself).
- Drive arrays with phase offsets, like p5.js kinetic posters: a wave of quarter turns crosses a row of tiles column by column, each tile a fixed fraction of a beat after its neighbour, and the whole wave finishes inside its beat.
- Build to a held poster: the composition assembles, has one big hero move (a turn or a cascade) at 60–75 % of the runtime, then the type cuts in and the frame holds with the grid stepping back. End on a cut or a mechanical camera pull-back, never a dissolve.
- For a printed finish, lay the colours as separate ink layers on a paper texture: slightly ragged edges, a little density variation, a pixel of misregistration between layers, and registration marks in every layer so the offset shows. Keep small type crisp enough to read.

Use the [production recipe](references/recipe.md) for the bundled original study and port-specific decisions. It is a technique example, not a prescribed film. Keep motions a function of absolute seconds so any frame can be sought cold. Prepare assets locally, preserve async seeking and register actual resource/cue times. Keep essential type editable and localized.

## Review and delivery

At full resolution, check every landing against the grid (positions and edges on module lines), every action against the cue sheet (one per beat, cut-ins on the beat), easing curves free of overshoot, the colour count, and type legibility and margins at the intended size. Step through the fastest moves frame by frame and seek into the middle of them cold. Follow `animaguru-video` for production records, audio mixing and HTML5 delivery; export MP4 when requested. Describe the actual 2D rendering method accurately. Physically rendered 3D remains deferred.
