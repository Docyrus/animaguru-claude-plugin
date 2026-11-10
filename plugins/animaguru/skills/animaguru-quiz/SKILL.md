---
name: animaguru-quiz
description: "Add a quiz to an AnimaGuru film in a video workspace (an educational explainer, lesson, training or onboarding film): questions that pause the film at checkpoints (one question or a quick round, for example after every scene), a final quiz after its end, and the viewer's score. Plays as an interactive film on AnimaGuru and in `npm run dev`, never as an MP4. Use when the user asks for a quiz, questions, knowledge checks, a test, an assessment or an interactive lesson or explainer."
---

# AnimaGuru quiz

A quiz film is an ordinary AnimaGuru film plus a `quiz.json` beside `film.config.json`. The player pauses the film at each **checkpoint** to ask one question or a quick round, shows whether the answer was right with the explanation, and continues; after the film's end it asks the **final quiz** and shows the viewer's score, with Retake the quiz and Watch again. A wrong answer at a checkpoint offers Watch that part again, which replays that part and asks again. The film works with or without a final quiz, with or without checkpoints, and inside a branching story (`story.json`) too.

The cards are HTML over the picture (buttons a viewer can tap, tab to, or press 1–6 for), so the questions play only in the interactive film: locally in `npm run dev`, and on AnimaGuru's video pages, share links and embeds after `animaguru submit`. A quiz film has no MP4 and cannot be downloaded, because its questions wait for a viewer's answers: `npm run export:mp4` refuses a film with `quiz.json`, the cloud Animator offers no MP4 for it, and you should not promise one. Capture, review and frames see the film without the cards. Read sibling `animaguru-video` first for the setup, interview, kit, audio and review workflow; this skill adds what changes.

## Start

- In a workspace: `animaguru create animation NAME --quiz` writes a starter `quiz.json` (one checkpoint in the starter film's first scene and a short final quiz), so `npm run dev` shows the cards at once. Replace it with the real quiz. `--story --quiz` starts a branching story with a quiz.
- An existing film gets a quiz by adding `quiz.json`; deleting it makes the film plain again.
- An educational film is usually the **Explainer** category; record the quiz plan in `production/brief.md`.

## The interview: the designer decides where the questions go

Fold these into the one compact interview round, and reuse what the user already said ("one question after every scene" answers the first two):

1. **Where:** a question or quick round after every scene, at chosen moments, only a final quiz at the end, or both. Offer "one question after each scene plus a 3–5 question final quiz" as the default for a lesson.
2. **How many:** per checkpoint (1 is usual, 2–3 for a quick round; at most 5) and in the final quiz (3–8 is usual; at most 20). Mid-film rounds of more than three questions interrupt the film; move them to the final quiz.
3. **Kinds of question:** one right answer (multiple choice, 2–6 options), true or false (two options), or select all that apply. Ask whether to explain each answer (recommended).
4. **Scoring:** a pass mark (`pass`, a percentage) or just a score; and whether a wrong answer should offer Watch that part again (always on at checkpoints) and from where (`review`).
5. **Audience and language:** the learners' age or level sets the wording; questions in another language need the card's own words translated through `ui`.

Base every question on what the film itself shows or says, so a viewer who watched can answer it. Check facts the same way as the film's claims; never quiz on something the film does not teach.

## quiz.json

```json
{
  "version": 1,
  "checkpoints": [
    { "id": "light", "at": 15, "title": "Quick check", "review": 3.5, "questions": [
      { "prompt": "Where does moonlight come from?", "options": ["The Moon makes its own light", "Sunlight bouncing off the Moon", "Light from cities on Earth"],
        "answer": 1, "explanation": "The Moon has no light of its own; we see sunlight that bounces off it." } ] },
    { "id": "orbit", "at": 30.5, "questions": [
      { "prompt": "About how long is one cycle of phases?", "options": ["One day", "One week", "About 29.5 days", "One year"], "answer": 2 } ] }
  ],
  "final": { "title": "Moon quiz", "pass": 70, "questions": [
    { "prompt": "Which of these are phases of the Moon?", "options": ["Crescent", "Gibbous", "Eclipse", "First quarter"], "answer": [0, 1, 3],
      "explanation": "An eclipse is a different event, when a shadow falls on the Moon or the Moon blocks the Sun." },
    { "prompt": "True or false: at new moon, the Moon's sunlit side faces away from us.", "options": ["True", "False"], "answer": 0 } ] },
  "theme": { "accent": "#b4560f", "surface": "#fffaf0", "text": "#1a2238" },
  "ui": { "check": "Quick check", "final": "Quiz" }
}
```

- **A question:** `prompt` (up to 160 characters; keep it under about 110 for phones), `options` (2–6, each up to 100 characters, no two alike), `answer` (the right option's index, 0 for the first; for select all that apply, the right indices in increasing order, never every option), optional `explanation` (up to 280 characters, shown after the answer) and optional `id` (lowercase, hyphenated; stable ids keep reports comparable after edits). The card adds "Select all that apply." itself; do not repeat it in the prompt.
- **A checkpoint:** `id`, `at` (the second of the film's timeline it pauses at, from 0.5 to the duration), `questions` (1–5), optional `title` (the card's eyebrow, "Quick check" by default) and optional `review` (the second Watch that part again goes back to; by default the previous checkpoint, or the start). List checkpoints in time order, at least 2 s apart.
- **The final quiz:** `questions` (1–20), optional `title` ("Quiz" by default) and `pass` (1–100: the percentage of right answers that passes). The score counts every question on the viewer's path, checkpoints included; a checkpoint skipped by seeking counts as not answered.
- **In a branching story:** each checkpoint's `at` must lie inside one segment (a checkpoint at a segment's end belongs to that segment) and, in a segment with choices, no later than its `choiceAt`; `review` stays in that segment. The score covers the checkpoints of the segments the viewer played, and the final quiz plays at the first ending they reach, before the ending's card.
- `theme` colors the cards (accent for buttons and highlights, surface for the card, text); otherwise the brand's primary color on a light card. `ui` translates the player's words on the cards: `check`, `final`, `progress` ("Question {n} of {total}"), `selectAll`, `checkAnswer`, `correct`, `incorrect`, `answer` ("The answer: {answer}."), `continue`, `next`, `seeResults`, `watchAgain`, `score` ("You got {correct} of {total} right"), `passed`, `notPassed` ("{pass}% passes…"), `perfect`, `retake`, `restart`, `complete` and `skipped` ("{count} not answered"); keep the `{…}` placeholders. The player's own card words already come in English, Turkish, Swedish and Arabic.
- `languages` (optional): the quiz in the film's other languages (each with its `shared/locales/LANG/film.json`): `languages.LANG.checkpoints.ID` and `languages.LANG.final` give a round's `title` and its `questions`, each with its `prompt`, `options` and `explanation` in the quiz's own order and option count; `languages.LANG.ui` the cards' words. The right answers stay the quiz's own, so keep each translated option where its original is.
- `npm run build`, `npm run dev`, review and `animaguru submit` check the file (and, in a story, against its segments) and name the first problem.

## Writing good questions

- One idea per question, in the film's words and the learners' language. Ask about understanding (why, which, what happens next), not trivia from a single frame.
- Distractors are plausible mistakes a learner really makes (for the Moon: "Earth's shadow covers it"), similar in length and tone to the right answer. Avoid "all of the above", "none of the above", double negatives and trick wording.
- Vary the position of the right answer; review warns when it is always the same option.
- An explanation teaches: why the right answer is right and, briefly, why the tempting wrong one is wrong. The card already shows the right option when the viewer misses it.

## Scenes for a quiz

- **Put each checkpoint on a held frame.** The film stops on the frame at `at` and the card covers its middle over a dimmed picture, so end each scene with a settled, intentional picture: put `at` on that hold, 0.3–1 s before the scene's next transition, after the narration and captions have finished. Never pause mid-sentence or mid-movement.
- The question's subject should be what the scene just showed; the viewer can still see the dimmed picture around the card.
- The final quiz opens over the film's last frame, so end the film on a calm summary or title image rather than a cut to black.
- Add a `Quiz` track to `src/film-resources.ts` with a short clip at each checkpoint, so the authoring timeline shows where the film stops.

## Sound

The film's soundtrack pauses while a card is open and continues with the film. End each narration line and musical phrase before a checkpoint; a phrase cut by the pause sounds broken. Watch that part again replays the soundtrack from `review`.

## Review and delivery

- `npm run dev` plays the quiz. In the console, `animaguru.quiz.pick(1)`, `.check()`, `.next()`, `.retake()` and `.reset()` drive the cards and `animaguru.quiz.score` reads the score; `animaguru.state.quiz` says whether a card is open or asking. The page also receives an `animaguru:quiz` window event for each answer and when the quiz is complete. Play the whole film, answer right and wrong, try Watch that part again, Retake the quiz and Watch again, at desktop and phone sizes.
- `npm run review -- --headless` checks the film under the cards, then prints the quiz's checkpoints, questions and pass mark, plus notes (an answer always in the same position, questions without explanations, checkpoints close together, long prompts). Check the frame at every checkpoint with `npm run frames -- --at …`.
- Deliver with `animaguru submit --yes` (private by default); there is no file to download, and AnimaGuru's video page plays the quiz and labels the video with its number of questions. Say plainly that it has no MP4; a user who also wants an MP4 of the film needs a copy without `quiz.json`, which plays straight through with no questions.
