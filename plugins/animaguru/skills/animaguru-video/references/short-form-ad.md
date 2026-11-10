# Short-form vertical ad (Reels, Shorts, TikTok)

A tested sequence for a 15–60 s 9:16 ad with voiceover, music and burned-in captions, first used for a 45 s B2B product reel. It replaces exploring the CLI, the catalog and older films. Adapt the story to the brief: the beats below are a starting point, not a template.

## 1. Brand and claims

- If the shared kit is a placeholder, run `npm run inspect:site -- https://SITE --pages /product,/about` and follow `animaguru-brand-kit`. Look at `hero.png` and the saved logo files before using them.
- Take product claims from the saved `text.md` pages and record them in `production/sources.json`. Do not invent customers, figures, testimonials or prices; label example values in interface mock-ups as illustrative.

## 2. Film setup

- `animaguru create animation NAME`, then save category, template and skill in its `animaguru.project.json`.
- `film.config.json`: `"width": 1080, "height": 1920, "fps": 30, "duration": 45, "safeArea": "reels", "poster": END_CARD_SECONDS`.
- One remote asset project for the film's media: `animaguru projects create --name "BRAND — reel"`.

## 3. Script and beats

A read at about 2 words per second, sped up 1.12×, fits 85–95 words into 45 s with a 3–4 s end-card hold. One voiceover segment per beat (`vo-01-hook`, `vo-02-problem`, …). This beat pattern worked for a 45 s ad:

| Beat | Time | Job |
| --- | --- | --- |
| Hook | 0–5 s | One concrete, visual problem |
| Problem | 5–11 s | Why it happens |
| Turn | 11–15 s | The reframing line |
| Product | 15–19 s | The product enters on the music drop |
| Proof | 19–33 s | Two or three capabilities as interface moments |
| Outcome | 33–37 s | What the viewer gets |
| End card | 37–45 s | Logo, tagline, call to action, URL; voice ends by about 41 s |

## 4. Generate the audio

- `production/generation/vo-lines.json`: `{"defaults": {"type": "speech"}, "assets": [{"name": "vo-01-hook", "prompt": "…"}]}`. Leaving out the model uses the studio's default speech model (`animaguru assets list PROJECT_ID` shows it under `defaultModels.speech`). Direct the read the way that model takes it: Gemini takes a `voice` name and `delivery` such as "Confident, crisp diction, medium-brisk pace, short pauses at full stops."; ElevenLabs a voice ID, with audio tags in the transcript; HeyGen Voice reads the transcript as written. `animaguru catalog --type speech` lists the voices.
- `animaguru assets batch PROJECT_ID --file production/generation/vo-lines.json --dry-run`, then `--yes --download production/audio/vo/`.
- `animaguru assets generate PROJECT_ID --type music --name music-bed --prompt "STYLE, instrumental, tense intro, a clear drop, strong final hit" --yes --download production/audio/music/`. The bed comes back longer than the film; step 5 fits it.
- Eight speech lines and one music bed cost about 10 credits for the first reel; always dry-run first and stay within the authorized budget. Keep the JSON receipts in `production/generation/`.

## 5. Cut, fit and mix

1. `production/audio/vo.json` with each segment's on-screen `captions`, then `npm run audio:vo -- --animation NAME`.
2. `npm run audio:music -- --animation NAME --file production/audio/music/music-bed.mp3 --length 45 --drop PRODUCT_BEAT_START --end-hit END_CARD_START+5.5`.
3. `npm run audio:mix -- --animation NAME`.

## 6. Build the film

- `src/film.ts`: `FilmBase` with `captions: joinCaptions(timing.captions)`; `cueSheet(timing)` times every scene; `film.mark(DROP, "Music drop")` records music hits for review. Scenes go in `src/scenes/*.ts`, one per beat.
- Layout inside the Reels safe area: headlines at 72–96 px in the top third (y 260–600), interface cards in the middle (y 650–1350), labels at 26 px or more, and nothing but the caption below y 1440. The caption bar sits at about y 1500 by default.
- `npm run build -- --animation NAME` typechecks.

## 7. Review in two or three rounds

- `npm run review -- --animation NAME --headless`, then fix every overlap, safe-area, small-text and caption line it prints.
- `animaguru review check --animation NAME --yes` checks the review frames for an empty hook frame, cut-off or overlapping text and broken letters. Open the frames it flags first.
- `npm run frames -- --animation NAME --at TIMES`, with each beat's midpoint and each transition, gives one contact sheet per 12 frames. Fix what it shows, then re-run only the changed times.

## 8. Export

- `npm run export:mp4 -- --animation NAME --headless --burn-captions` for the feed upload (muted autoplay needs captions in the picture), and the same without `--burn-captions` for a clean MP4 with `.srt`/`.vtt`.
- Report what was measured (frames, duration, codecs, loudness) separately from what was watched or listened to.
