---
name: animaguru-general-video
description: Develop and produce original films, music visuals, titles, ambient loops and visual essays in an AnimaGuru video workspace. Use after the General Video purpose is selected.
---

# AnimaGuru general video

Read sibling `animaguru-video` and the selected visual skill. Purpose describes the video's job; visual style remains independently selectable. For new work, run the shared compact interview once and fold workflow-specific missing questions into it. Reuse explicit answers, saved project choices and completed briefs; honor a requested interview skip.

Infer a suitable workflow from the request or clarify it in that interview. Do not add a mandatory menu when the user's intent is clear. Save a listed workflow ID in `animaguru.project.json` only when it fits; leave it null for a custom brief. Read only the applicable reference:

- **Original Short Film** (`short-film`): Create a film from a subject, character or idea with an intentional ending. Read [the workflow](references/short-film.md).
- **Music & Lyric Video** (`music-lyrics`): Choreograph visual changes to the actual track, lyrics and sections. Read [the workflow](references/music-lyrics.md).
- **Titles & Event Motion** (`titles-event`): Present names, credits or event identity in a composed sequence. Read [the workflow](references/titles-event.md).
- **Ambient & Seamless Loop** (`ambient-loop`): Build a mood or display loop with continuous motion at its boundary. Read [the workflow](references/ambient-loop.md).
- **Visual Essay & Podcast** (`visual-essay`): Add accurate graphics and chapters to source text or recorded speech. Read [the workflow](references/visual-essay.md).
- **Branching Story** (`branching-story`): Let viewers choose what happens next and reach one of several endings; plays as an interactive HTML5 film, never MP4. Read [the workflow](references/branching-story.md) and sibling `animaguru-branching-story`.

Develop an original sequence from the user's sources, audience, tone, duration and desired outcome. Avoid importing fixed scene counts, mandatory emotional arcs, default audiences or a compulsory CTA. Respect supplied narration/music preferences. Discover AnimaGuru generation models and costs through the local main skill; this purpose selection does not authorize paid jobs.

Use `src/studies/media.ts` for optional deterministic source-time/trim mapping and cue comparison; prepare footage locally and await decoded frames before capture. `npm run review` collects actual canvas text bounds, deterministic seek comparisons and review frames through the browser. Preserve resource timing and the HTML5 embed/export contract. Review moving playback and audio as well as numerical checks.
