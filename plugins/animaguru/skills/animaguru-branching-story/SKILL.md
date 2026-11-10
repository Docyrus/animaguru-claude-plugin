---
name: animaguru-branching-story
description: Design and build a branching (interactive, choose-your-path) story film in an AnimaGuru video workspace, where viewers pick what happens next at choices and reach one of several endings. Plays as an interactive film on AnimaGuru and in `npm run dev`, never as an MP4. Use when the user asks for an interactive, branching, choose-your-own-adventure or multiple-ending film, ad, explainer or lesson.
---

# AnimaGuru branching story

A branching story is an ordinary AnimaGuru film whose timeline holds every segment of every path, laid end to end, plus a `story.json` beside `film.config.json` that says where each segment goes. The player plays one segment at a time: at a segment with choices it shows the prompt and buttons over the picture and continues into the segment the viewer picks; a segment with `next` flows on by itself; an ending shows its title with Play again and Back to the last choice. Review, frames, the frame checker and capture still see the whole timeline as one film, so every segment of every path is checked.

It plays only as an interactive film: locally in `npm run dev`, and on AnimaGuru's video pages, share links and embeds after `animaguru submit`. It cannot be downloaded. An MP4 has one path, so `npm run export:mp4` refuses a film with `story.json`, the cloud Animator offers no MP4 for it, and you should not promise one. Read sibling `animaguru-video` first for the setup, interview, kit, audio and review workflow; this skill adds what changes.

## Start

- In a workspace: `animaguru create animation NAME --story`. It writes a starter `story.json` over the starter film's three scenes (an opening with a choice and two endings), so `npm run dev` shows the mechanics at once. Replace both with the real story.
- An existing film becomes a branching story by adding `story.json`; a film without one is linear and unchanged.
- To ask questions on the way or at an ending (an interactive lesson), add a `quiz.json` too, following sibling `animaguru-quiz`; `--story --quiz` starts both.
- A presentation can branch too, for a talk where the room chooses the path: `--presentation --story` starts one, its segments runs of whole slides. Read `animaguru-presentation` ("A talk that branches") for how it differs.
- Category and style selection work as for any film. A story told for its own sake is General Video with workflow `branching-story`; an interactive explainer, lesson or ad keeps its own category and records the branching in `production/brief.md`.

## The interview, for a story

Fold these into the one compact interview round; reuse what the user already said:

1. **Shape:** how many choices on the way and how many endings (2–3 choices and 2–4 endings suit a 1–3 minute playthrough). Whether paths rejoin (a diamond: choices that change a scene and meet again), loop back ("try again"), or split for good.
2. **What a choice means:** the viewer steers a character, picks a topic to learn, or chooses a product path. Each option should lead somewhere visibly different; a choice that changes nothing feels broken.
3. **Timing:** whether choices wait for the viewer (default) or run a timer (`timeout`, 8–12 s) that takes a default, as in a lean-back film.
4. **Language** of the prompts, buttons and endings; the panels' own words (The end, Play again, Back to the last choice) are translated through `ui` in `story.json`.

Write the graph into `production/brief.md` as a short outline: each segment's id, what happens, and where it leads.

## story.json

```json
{
  "version": 1,
  "start": "opening",
  "segments": [
    { "id": "opening", "label": "The fork", "start": 0, "end": 12, "prompt": "Which way does Mo go?", "choiceAt": 8,
      "choices": [ { "label": "Into the forest", "to": "forest" }, { "label": "Along the river", "to": "river" } ] },
    { "id": "forest", "label": "The forest", "start": 12, "end": 22, "next": "home" },
    { "id": "river", "label": "The river", "start": 22, "end": 32, "prompt": "Mo hears a splash.", "timeout": 10, "default": 0,
      "choices": [ { "label": "Look closer", "to": "home" }, { "label": "Run back", "to": "opening" } ] },
    { "id": "home", "label": "Home", "start": 32, "end": 40, "ending": "Home before dark" }
  ],
  "ui": { "theEnd": "The end", "playAgain": "Play again", "back": "Back to the last choice", "choose": "What happens next?" },
  "theme": { "accent": "#2c6bd0", "surface": "#fffdfa", "text": "#16232a" }
}
```

- Each segment ends in exactly one way: `choices` (2–4, each a `label` of up to 60 characters and a target `to`), `next` (another segment) or `ending` (the ending's title).
- `start` and `end` are seconds of the film's timeline. Segments lie end to end without gaps or overlaps: the first starts at 0 and the last ends at `film.config.json`'s `duration`. The order on the timeline is yours; keep each path's segments in reading order where you can, which makes review easier to follow.
- `choiceAt` (seconds of the timeline, within the segment) is when the choices appear; by default at the segment's end. The segment keeps playing under them; a viewer who chooses early sees the segment finish, then the chosen segment. At the segment's end the player holds its last frame until a choice.
- `timeout` (3–60 s) counts from when the choices appear, while the film plays and while it holds; `default` (an index, the first by default) is taken when it runs out. Leave `timeout` out to wait for the viewer.
- `prompt` (up to 120 characters) shows above the buttons. `label` names the segment on the timeline and in the transcript. `ui` and `theme` are optional; the theme defaults to the brand's primary and text colors.
- `languages` (optional): the story in the film's other languages (each with its `shared/locales/LANG/film.json`): `languages.LANG.segments.ID` gives a segment's `label`, `prompt`, `ending` and `choices` (its choices' labels, in order), and `languages.LANG.ui` the panels' words. Where each choice leads stays the same. The player's panel words already come in English, Turkish, Swedish and Arabic.
- Every segment must be reachable from `start`, and every segment must still be able to reach an ending, so no path traps the viewer. `npm run build`, `npm run dev`, review and `animaguru submit` check the graph and name the first problem.

## Scenes for a story

- Drive scenes from `story.json`, so a re-timed segment moves its scenes: `import story from "../story.json"` and `const beat = storyBeats(story)` from the kit; `beat("forest").start`, `.end`, `.choiceAt` and `.length`. Pass `storyChapters(story)` as the film's `chapters` (or chapters with the same times), so the transcript and review cues follow the segments.
- **A segment must stand on its own at both ends.** It may be entered from several segments and left for several, so it starts from a clean picture (no object carried over from whichever segment came before on the timeline) and finishes in a picture that holds well as a still. Show each segment's scene only within its own `[start, end)`.
- **Design the choice window.** From `choiceAt` to the end, keep motion calm and loop-friendly (breathing, drifting, idle character motion) so the held last frame looks intended, and keep the bottom third of the frame free of text and captions: the prompt and buttons sit there over a dark gradient. Put the question's subject in the upper two thirds.
- An ending segment builds to a final image with room for the centered ending panel (title and buttons) over a dimmed picture; the film's own end card is optional.
- Set `poster` in `film.config.json` to a strong frame of the opening segment.

## Sound

`config.audio` stays one mixed soundtrack over the whole timeline. The player moves it to each segment's start when the story jumps and pauses it while a choice waits, so each segment's sound must begin and end cleanly at the segment's boundaries: no narration line or musical phrase across a boundary, a short fade at each segment's end, and an ending that resolves. For narration, list the VO segments in `production/audio/vo.json` in timeline order, one or more per story segment, and use `gapBefore` to leave each story segment's choice window or quiet ending before the next one's first line: `npm run audio:vo` places them in sequence, so lay out `story.json` from the result (the kit's `cueSheet(timing).segment(id)` gives each VO segment's start and end) rather than the other way round. For music, cut a bed per segment, or use a calm loopable bed, rather than one long track whose phrases run across jumps. Silent stories with burned-in captions work well too.

## Review and delivery

- `npm run dev` plays the story; `?segment=ID` starts at a segment, and in the console `animaguru.story.goTo("ID")`, `.choose(1)`, `.back()` and `.restart()` drive it. Play every path to each ending at desktop and phone sizes, try keyboard choice (Tab, or 1–4), a timeout, Back and Play again.
- `npm run review -- --headless` checks text, seeking and frames over the whole timeline, then prints the story's segments, choices, endings and shortest and longest playthrough, plus notes such as a timeout too short to read. `npm run frames` and `animaguru review check` work as for any film; choose times inside each segment.
- Deliver with `animaguru submit --yes` (private by default); there is no file to download. The submitted film records the story, so AnimaGuru's video page plays it interactively and labels it as an interactive story; its seek bar covers the segment playing. Say plainly that it has no MP4.
