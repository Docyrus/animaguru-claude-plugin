---
name: animaguru-presentation
description: "Make an AnimaGuru film into a presentation in a video workspace: slides that each play their build and hold until the presenter clicks, with point-by-point stops, gentle loops while a slide waits, speaker notes and clicker keys. Also builds a presentation from the user's own slides (a PowerPoint file, or a PDF from PowerPoint, Keynote or Google Slides), data slides from a spreadsheet, a talk that branches on the room's choice, the same talk in other languages, and a narrated video version with a presenter. Keeps its MP4, which plays straight through, and exports a PowerPoint file whose slides play their builds, for presenting from PowerPoint, Keynote or Google Slides. Use when the user asks for a presentation, slides, a deck, a pitch or keynote they will present, a talk, a class or lecture with slides, or to make their existing slides move."
---

# AnimaGuru presentation

A presentation is an ordinary AnimaGuru film plus a `deck.json` beside `film.config.json`. Its slides lie end to end on the film's timeline. The player plays a slide's **build** (its animation) when the presenter moves to it, then **holds** on the slide's last frame until the next click, so the room looks at a finished slide while the presenter talks. **Stops** hold inside a slide for a point-by-point build; a **loop** keeps a held slide gently moving; **auto** moves a slide on by itself; **notes** are the presenter's.

Holds take no time on the timeline: a 20-minute talk of 12 slides may need only 2–4 minutes of film. Every frame is drawn from the time alone, so going back is instant and exact, and text stays sharp on any projector. AnimaGuru's video pages present it the same way after `animaguru submit`. Capture, review and `npm run export:mp4` see the film straight through, so a presentation keeps its MP4 (a video version without holds). Read sibling `animaguru-video` first for the setup, interview, kit, audio and review workflow; this skill adds what changes.

## Start

- In a workspace: `animaguru create animation NAME --presentation` writes a starter `deck.json` (a slide for each of the starter film's three scenes), so `npm run dev` presents at once. Replace it with the real slides. `--presentation --quiz` adds a quiz (see `animaguru-quiz`), and `--presentation --story` makes a talk that branches (below).
- An existing film becomes a presentation by adding `deck.json`; deleting it makes the film plain again.
- Choose the category by purpose: **Explainer** for a lesson, briefing, report or training; **Advertisement** for a sales pitch or product launch; **General Video** for anything else. Record the presentation plan in `production/brief.md`.

## From the user's own slides

When the user brings slides, build the presentation from them; their words and numbers are the source.

- Ask for the deck as a **PowerPoint file (.pptx) and a PDF of it**: the .pptx has the exact words, the speaker notes, the numbers behind each chart and every picture and video at full size; the PDF shows how each slide looks. PowerPoint: the file itself, and File › Export › PDF. Keynote: File › Export To › PowerPoint, and To › PDF. Google Slides: File › Download › Microsoft PowerPoint, and › PDF. A `.key` file or a Google Slides link cannot be read directly. A PDF alone works too (exporting PowerPoint's Notes Pages, or Keynote's PDF with presenter notes, brings the notes).
- Read it: `npm run slides -- --animation NAME path/to/deck.pptx path/to/deck.pdf` writes `production/slides/DECK/slides.json`. For each slide: its `title`, `text` in reading order (bullet levels indented), `paragraphs` with their levels, `notes`, `tables`, `charts` (each series' categories and values), its `section`, whether it is `hidden`, its `media` saved in `media/` (pictures with their alt text, videos with their poster) and `image`, the PDF's picture of it (`page-01.png`…). A PDF leaves hidden slides out, so ask whether to keep them. With a PDF alone (`npm run slides -- --animation NAME deck.pdf`), each page has its text in order and its picture. Read every slide's text and look at every picture; a slide without text is a picture or a scan, so read it from its picture. By default each of their slides becomes one slide; keep the order, the slide titles and the on-screen copy word for word, and every number exactly. Ask before merging, splitting, dropping or rewording slides, and before adding anything the deck does not say.
- Keep their notes as each slide's `notes`. Where a slide has none, write short ones from the slide only if the user asks.
- Reuse the deck's own pictures, logos, videos and charts when the user owns them. Redraw a chart from its numbers in `charts`, not from its picture. Take colors and type from the brand kit, or from the deck when there is none.
- The animation is what you add: how each slide builds, which points appear one click at a time, and gentle motion while it holds. Show the user the slide-by-slide plan before building.

## The interview

Fold these into the one compact interview round, and reuse what the user already said:

1. **How it is given:** live in a room with a clicker, on a video call, or sent as a link people click through themselves. All three use the same player. Ask too whether it needs a narrated video version (below), for people who miss the talk.
2. **The talk:** its length and how many slides (about 1–2 minutes of talking per slide is usual: 10–15 slides for 20 minutes). The film is only the builds.
3. **Audience and outcome:** who is in the room and the one thing they should remember or do.
4. **Material:** their slides (a PowerPoint file and a PDF of it), notes, data, script, brand. Ask too whether they must present from PowerPoint or Keynote, as some venues and IT rules require (below).
5. **The screen:** 16:9 (1920 × 1080) unless the room says otherwise; set `width` and `height` in `film.config.json` for another shape, such as 1440 × 1080 for 4:3 or 1920 × 1200 for 16:10.
6. **Languages:** the language it is given in, and any others it should also be given in (below).

## deck.json

```json
{
  "version": 1,
  "slides": [
    { "id": "title", "title": "Welcome", "start": 0, "end": 3.7, "loop": 2.5, "notes": "Who we are in one line." },
    { "id": "problem", "title": "What slows us down", "start": 3.7, "end": 10.7, "stops": [6, 8.5], "notes": "Three things, one per click." },
    { "id": "numbers", "title": "Q3 in numbers", "start": 10.7, "end": 18, "notes": "Walk through the three numbers." }
  ]
}
```

- **Slides** are listed in the order they are presented: the first starts at 0, each starts where the one before ends, and the last ends at the film's `duration`. 1–200 slides, each at least 0.5 s.
- `id`: lowercase and hyphenated. `title` (optional, up to 80 characters): the slide's name in the slide grid and for screen readers.
- `stops` (optional, 1–20): seconds inside the slide where it also holds, in order, each at least 0.25 s after the slide's start or the stop before and 0.25 s before its end.
- `loop` (optional): while the slide holds at its end, it replays from this second to its end. It starts at or after the last stop and at least 0.5 s before the end. Make it seamless: the frame at `loop` must match the frame at the slide's end, so only periodic motion (a slow drift, a pulse, a shimmer) runs over that span.
- `auto` (optional, 1–600): seconds each of the slide's holds waits before the presentation moves on by itself. Use it only where the user wants that, such as a title loop before the talk or a screen left running; a live presenter usually wants every click.
- `notes` (optional, up to 4000 characters): the presenter's speaker notes; line breaks are kept.
- `ui` (optional): the player's `next`, `back`, `slide` ("Slide {n} of {total}"), `notes`, `grid` ("All slides") and `close` ("Back to the presentation") labels; keep the `{…}` placeholders. The player has its own words in English, Turkish, Swedish and Arabic, so set these only for another language or other wording.
- `say` (optional): the slide's narration for the narrated version: one text for the whole slide, or a list with one text per hold (its stops, then its end), `""` where nothing is said. See below.
- `languages` (optional): the presentation in other languages: `languages.LANG.slides.ID` gives that language's `title`, `notes` and `say` for a slide, and `languages.LANG.ui` its player words. See below.
- `npm run build`, `npm run dev`, review and export check the file and name the first problem.

## Slides from the motion library

Start each slide from a finished one where one fits. The motion library's `presentation-slides` category holds slides made for decks: a cover, an agenda that doubles as each section divider, the problem (a pile of pains, chaos to order, why now), market size, a product screenshot with hotspots, pricing, traction, a logo wall, case-study results, a comparison checklist, a positioning matrix, the team, the ask, a roadmap, OKRs, SWOT, one hero number and Q&A. They already follow the rules below: large text inside the projector's margin, a stop after each reveal and a seamless loop while held. Searching spends no credits.

1. Find one for each slide in the plan: `animaguru motion search "agenda with sections" --category presentation-slides` (the Cloud Animator's planner searches the same library). `animaguru motion get ID` prints its beats, its options and the deck.json times for its default content; name the example each slide starts from in the slide-by-slide plan.
2. `animaguru motion get ID --write animations/NAME/src/scenes` (`src/scenes` in a standalone project) writes the scene. Call its entry from `build()` with `at` set to the slide's start and the slide's own content, for example `agendaProgress(this, { at: 12.4, title: words.agenda.title, sections: words.agenda.sections, panel: hex(branding.colors.primary), fontFamily: [branding.fonts.heading.family] })`, with `branding` the film's brand context. Replace every sample word, name, logo and number (the library's slides speak for fictional companies), and take colours and fonts from the film's brand context.
3. The scene's `…Slide(options)` function returns `{ stops, loop, end, duration }` for the content you give it (a list's length decides its stops). Add the slide's start to each and write them into `deck.json`; the slide ends at its start plus `end`, where the next slide starts, and the scene's exit plays under the next slide's build. Give the scene `exit: false` to hold it instead, as for the last slide.
4. A slide with stops says one text for each hold in the narrated version (`say`: the helper's stops, then its end), or one text for the whole slide.
5. In a presentation given in several languages, pass every text option from the film's words (`words.agenda.sections`), so each language draws its own, and check the longest language still fits: titles wrap, list rows and labels do not. The hero number's `locale` sets each language's digit grouping and decimal mark; the other slides write amounts the English way ($1.2M). The library's slides lay out left to right: for Arabic, mirror one yourself, or use it as a reference for a slide of your own.
6. A data slide (the hero number, market size, traction, case-study results, OKRs, pricing, the ask, the logo wall's counter) takes its numbers as options: give it the data's values (below), and record every number it shows in `production/facts.json`, as the held frame shows it, at the end of its count (review reads a counter drawn a digit at a time as its whole number). A slide that numbers its items, as the agenda does (01, 02…), shows numbers that make no claim: list them in `ignore`.
7. Examples from other categories are made for video: when you use one, raise its small text to the size below, put stops where it has settled, and end the slide before its exit.

## Scenes for a presentation

- **One slide, one scene, one idea.** The slide's build brings its content in (1–4 s is usual; review notes a build over 12 s between holds, since the room waits through it). What the presenter says goes in the notes, not on the slide.
- **End each slide where it shows complete.** The audience looks at that frame while the presenter talks. A scene's exit belongs to the start of the next slide's build: end the slide just before its scene starts leaving, as the starter does 0.3 s before each fade. Review notes a slide that holds on a frame with most of its text gone.
- **Point by point:** for a list, bring in one point per stop, each settled before its stop. Never put a stop mid-movement.
- **Readable from the back row:** few words, large type. Review fails a presentation whose text is under 3.3% of the shorter side (36 px at 1080) and notes text inside the projector's margin (the `projector` safe area), unless `film.config.json` sets its own `minTextSize` or `safeArea`; keep headings well above that. Keep contrast high: projectors wash colors out.
- **No captions for a live talk:** the presenter speaks, so give the film no captions track (an empty `captions` list in its film options) and keep any text the talk needs on the slides or in the notes.
- Add a `Slides` track to `src/film-resources.ts` with a clip per slide, so the authoring timeline shows where each starts and holds.

## A talk that branches

A sales talk can ask the room "pricing or features?" and go on down the chosen path; a class can take a detour. `--presentation --story` (or a `story.json` beside `deck.json`) makes the presentation a branching story (read `animaguru-branching-story` for the format):

- Each story segment is a run of whole slides: it starts where a slide starts and ends where a slide ends. The story starts with the segment at 0 s.
- A segment's choices show when its last slide holds complete; leave `choiceAt` out. The presenter (or the room) picks with a click or 1–4; Next waits until they do. A `timeout` with a `default` still picks by itself, and a screen takes the default.
- Next and Back follow the path taken: Back from a segment's first slide returns to the slide before it on that path, with its choices showing again. A slide's number and Enter, or the grid, jumps to any slide, and Back then returns to where the jump left. The ending segment's last slide ends the talk, without the story's ending card.
- Presenter view shows the slide the path leads to, or that the room's choice decides. A talk that branches plays only as an interactive film, as every story does: no MP4 and no narrated version.

## Every language

One presentation can be given in Turkish, Swedish, Arabic or any other language, on the same timeline:

- The film's words for each language go in `shared/locales/LANG/film.json`, the same keys as the film's own. The starter film reads its words through `localized(import.meta.glob("../shared/locales/*/film.json", …), config.language)` from the kit; a film that imports one locale file directly plays in that language only, so switch it to `localized` first.
- `deck.json`'s `languages.LANG.slides.ID` translates each slide's `title`, `notes` and `say`; the slides' times stay the same in every language. A talk that branches translates its choices in `story.json`'s `languages`, and a quiz its questions in `quiz.json`'s (see those skills). Write each language naturally, not word for word, and keep its numbers exact. Slides from the motion library take their words, and the hero number its `locale`, from each language's words (above).
- The player plays the language `?lang=LANG` names (`window.animaguru.languages` lists them, `setLanguage(code)` reloads in another at the same slide), and AnimaGuru's video pages show a language menu. Its controls and labels follow the language.
- Arabic and other right-to-left languages lay the page out from the right, and the canvas draws each text right to left. The film's own layout is yours: mirror it for right-to-left (text anchored at the right margin, the flow running right to left), and keep a brand name or a Latin label as it is. A brand font without Arabic letters falls back to the system's.
- `--language LANG` on `npm run review`, `frames`, `handout`, `narration`, `export:mp4` and `export:pptx` works in that language; review each language on its own (`production/review/LANG/`).
- A soundtrack spoken in one language needs one per language: `film.config.json`'s `languageAudio` gives a language its own track (or `null` for none); a language without one plays the film's `audio`.

## The narrated version

The same presentation can present itself, as a video for people who missed the talk, a course or YouTube. Give each slide a `say` (above): what a presenter would say while it shows. Then:

1. `npm run narration -- --animation NAME script [--language LANG]` writes `production/audio/narration/LANG/speech.json`, a speech request per take named for it (`SLIDE_ID`, or `SLIDE_ID-1`, `-2`… per hold). Choose a voice that suits the language and the studio's default speech model (`defaultModels.speech` in `animaguru assets list PROJECT_ID`; `animaguru catalog --type speech` lists voices), add it to its `defaults`, and run the `animaguru assets batch … --dry-run`, then `--yes --download` command it prints. Ask the user before spending credits.
2. `npm run narration -- --animation NAME [--language LANG]` times the takes: each slide's build plays as its take starts, and the slide holds until the take has finished and a short pause (`--pause`, 0.8 s); a hold with nothing said waits for the slide's `auto` time, or two seconds. It writes the narration track and `narration.json`, and names any take still missing.
3. `npm run export:mp4 -- --animation NAME --narrated [--language LANG] --headless` makes `NAME-LANG-narrated.mp4`: the film drawn along that schedule, held slides looping where they loop, its captions the sentences spoken (as `.srt`/`.vtt`), and a chapter per slide inside the MP4 and in `NAME-LANG-narrated.chapters.txt`. `animaguru submit --file` and the CLI's YouTube upload add the chapters to the description, so YouTube shows one per slide; give every slide a `title` for them.
4. A presenter: make a HeyGen avatar clip for each take, lip-synced to it and cut out of its background (`animaguru avatars video PROJECT_ID --look LOOK_ID --audio TAKE_SHA --transparent --aspect-ratio 9:16`; read `animaguru`'s `references/avatars.md`, and ask before spending credits). A transparent clip needs a look that supports matting, as most studio avatars and digital twins do; for a look that does not, `--background "#00FF00"` renders a green screen instead. Save them as `production/audio/narration/LANG/presenter/TAKE.webm` (or `.mp4`) and run `npm run narration -- --animation NAME presenter [--corner bottom-right] [--size 0.5] [--key "#00FF00"]`: `NAME-LANG-narrated-presenter.mp4` shows the presenter standing at the picture's edge while each take speaks, the slide around it (`--key` keys out a green screen, `--crop x,y,width,height` keeps a part of each clip, in fractions of it, to leave out a prop beside the presenter; a clip with a background shows boxed in the corner). Public HeyGen looks are photo avatars, which may not render transparent: a photo avatar made from a prompt that asks for a plain chroma-key green background, and nothing else in the frame, keys out cleanly. Look at its picture before making the clips. Keep that side of the slides clear of text. A cartoon host instead is a style of its own (`animaguru-cartoon-host-explainer`).

A change to the slides or their `say` after timing makes the narration stale: the export says so, and `npm run narration` times it again.

## Slides from real numbers

When the user gives data, a CSV, TSV or Excel file (or a spreadsheet attached in AnimaGuru), the data slides show its numbers and nothing else:

- `npm run data -- --animation NAME path/to/file.xlsx` reads every sheet into `production/data/NAME.json`, each cell by its A1 name with the text the file stores, and prints the first rows to cite.
- Write `production/facts.json`: `{ "version": 1, "facts": [{ "slide": "q3", "shown": "€1.2M", "data": "q3-sales", "sheet": "Sales", "cell": "C4", "value": "1234567", "note": "rounded to a tenth of a million" }], "ignore": ["2026"] }`. Each number a slide shows is a fact: as it is shown, and the cell it comes from with the value that cell holds. `ignore` lists numbers on screen that make no claim, such as a year or a slide's number; a label such as Q3 or FY26 is not a number.
- A number a slide works out from the data is a fact too: a share of a total, a rounded amount ($3M), a percentage, a count-up's last value. Cite the cell it comes from, and say how in its `note` (`"45% of B2"`).
- In a presentation given in several languages, a number written each language's way has one `shown` per language: `"shown": { "en": "12,400", "tr": "12.400" }`. Review checks each language's own (`--language`).
- `npm run review` then checks that each cell holds the value given, that each fact is on screen on its slide where it holds complete, and that every number a slide shows complete is a fact or ignored; it fails otherwise. Never invent, estimate or carry over a number the data does not hold: leave it out, or ask.
- Charts are drawn from the cells too (read `animaguru-animated-data-visualization` for chart craft); keep `production/FACTS.md` with the source of anything not in the data.

## A presentation that recurs

A monthly report or a pitch made for each client starts from the last one: AnimaGuru's film templates (Individual Pro and Team) save a finished presentation, and a new film started from one keeps its slides. In a film started from a template, keep every slide's id, order, structure and timing; change only what the new brief, data and brand call for. Its `production/template-FACTS.md` and `production/template-facts.json` are the last issue's facts, for reference only: write this issue's `facts.json` from the new data, and never show an old number as current. Take colours, fonts and the logo from the film's brand context rather than hard-coding them, so another client's brand kit re-skins the same slides.

## Changing one slide

When the user asks for a change to one slide ("on slide 4, show Q3"), change that slide and nothing else: its scene, its `deck.json` entry and its notes. A slide's number is its place in `deck.json`, from 1.

1. Before editing, `npm run deck:frames -- --animation NAME save` keeps a fingerprint of every slide's frames.
2. Make the change. Keep the slide's length unless the change needs another; the slides after it then move along the timeline with it, which is fine.
3. `npm run deck:frames -- --animation NAME compare --only SLIDE_ID` draws every slide again and fails if any other slide changed. The first moment of the next slide may change with it, since its build starts with the changed slide's scene leaving; compare says so. If another slide changed, undo that part, or tell the user why it had to change.

## Sound

A live talk is usually silent; the presenter's voice carries it. The film's soundtrack pauses at every hold and continues with the next build, so music under a presentation stops and starts at each click: leave it out, or keep sound to short effects inside builds that end before their hold.

## Review and delivery

- `npm run dev` presents it. Next: Page Down, →, ↓, Space, Enter or a click on the picture (during a build it skips to the build's hold); back: Page Up, ←, ↑ or Backspace. B or . covers the screen in black, W or , in white; a slide's number then Enter goes to it; Home and End; G opens a grid of every slide to pick from. F5, which clickers send to start a slide show, goes full screen. Speaker notes show closed under the player. In the console, `animaguru.deck.next()`, `.back()`, `.goTo(number or id)`, `.pick(number or id)`, `.grid(open)` and `.blank("black" | "white" | null)` drive it, `animaguru.state.deck` says where it is, and the page receives an `animaguru:deck` window event as it moves. Present the whole thing with a clicker or the keyboard, at desktop and phone sizes.
- **Presenter view:** the transport's presenter button opens a second window for the presenter's own screen: the slide the room sees, kept in step, the next slide, the notes, a timer and the clock, with Back, Next and Black. A clicker works from either window. Rehearse counts the seconds on each slide; Copy the times gives them as JSON, which can set a slide's `auto`. AnimaGuru's video pages open the same view from their bar.
- **Phone remote:** on AnimaGuru's video pages, share links and embeds, the bar's phone button shows a QR code; the presenter's phone then changes slides, blacks the screen and shows the slide's notes. A session lasts 12 hours, and anyone with its code can use it.
- `npm run review -- --headless` checks the film straight through, then lists the slides and holds with notes: slides without speaker notes, long builds, short loops, and slides holding with most of their text gone. Check each slide's held frame with `npm run frames -- --at …` (a slide's end minus 0.001 s).
- `npm run handout -- --animation NAME` makes the handout: a PDF page for each slide with its complete frame, its number and title, and its notes (`--no-notes` leaves them out, `--letter` prints on Letter); the slide's own text lies over its picture, so the PDF can be searched and copied.
- Deliver with `animaguru submit --yes` (private by default): AnimaGuru's video page, its share links and embeds present it slide by slide, with Back, Next, the slide number and title, the slide grid, a language menu for a presentation in several languages, and a Present button that goes full screen, and they answer a clicker's keys. A share link sent to someone lets them click through at their own pace; viewers who allow analytics are counted, and the video's page shows its owner, and in a team's workspace the team, the time spent on each slide and how far viewers got (Slide analytics). For a room with no network, present from the PowerPoint file (below), play the MP4 or use the PDF handout (above).
- **PowerPoint:** when the talk must be given from PowerPoint or Keynote, as on a venue's or a company's own machine, `npm run export:pptx -- --animation NAME` makes `NAME-LANG.pptx`. Each hold (each stop and each slide's end) becomes a slide whose video plays its build as the slide opens and stays on its complete frame, so each click moves on to the next build, as in the player. Each slide's notes are in its notes pane, and an `auto` slide moves on by itself. It renders the MP4 first (`--video FILE` reuses one `export:mp4` made of the whole film, in the same language). A loop stays on its last frame, and a branching story or a quiz cannot be exported. Google Slides shows each video as a picture, so `--stills` makes `NAME-LANG-stills.pptx` of pictures only, each hold where it shows complete, for Google Slides (File › Import slides) and wherever videos cannot play. Tell the user to play the file from the start in their PowerPoint or Keynote before the talk: each slide's video should start by itself. An existing file is never replaced; a new one gets the next free name.
- **Screen mode:** `?screen=1` on the player, an embed or a share link (`/videos/ID?embed=1&screen=1`, `/s/TOKEN?screen=1`) runs the film on a public screen, such as a menu board, a waiting room or a booth: it plays by itself, muted and looping, with no controls or pointer; a presentation moves on after each slide's `auto` time or `?hold=` seconds (6 by default); the screen stays awake, and the page reloads once the network comes back after a drop. `npm run export:mp4` gives a video version that plays straight through without holds. For the user's own PowerPoint, Keynote or Google Slides deck, `npm run export:mp4 -- --slide NUMBER_OR_ID --gif` exports one slide as an MP4 and a GIF, and `--slides` cuts every slide into its own clip: a slide's clip plays its build and ends on its complete frame, so set the video to play automatically when the slide opens. Google Slides plays a video only from Drive or YouTube; a GIF plays anywhere.
