# Branching Story

Let viewers choose what happens next and reach one of several endings; plays as an interactive film on AnimaGuru.

Read sibling `animaguru-branching-story` now: it is the contract for `story.json`, scenes that stand on their own at both ends, choice windows, sound across jumps, review of every path and delivery through `animaguru submit` with no MP4. Start a new film with `animaguru create animation NAME --story`.

Fold this missing information into the shared quick interview: **How many choices and endings, what does each choice change, do choices wait for the viewer or run a timer, and in which language?** Reuse supplied answers. Outline the graph (each segment, what happens and where it leads) in `production/brief.md` before building scenes.

- Give every choice a visible consequence within a few seconds of the next segment; options that lead to the same picture feel broken.
- Keep each playthrough short (often 1–3 minutes) and the endings distinct; one ending may loop back to a choice ("try again") if the brief invites it.
- Write prompts and button labels as the story's voice, short enough to read in the choice window.

Completion: every segment reachable and every path ending, each path played through in the browser, the review notes addressed, and the film delivered with `animaguru submit`, with no MP4 or download promised. Use `animaguru-video` for the common production, budget and review contract.
