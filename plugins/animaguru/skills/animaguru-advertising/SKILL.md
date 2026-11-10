---
name: animaguru-advertising
description: Develop and produce product, launch, offer, editorial and creator-led advertising in an AnimaGuru video workspace. Use after the Advertisement purpose is selected.
---

# AnimaGuru advertising

Read sibling `animaguru-video` and the selected visual skill. Purpose describes the video's job; visual style remains independently selectable. For new work, run the shared compact interview once and fold workflow-specific missing questions into it. Reuse explicit answers, saved project choices and completed briefs; honor a requested interview skip.

Infer a suitable workflow from the request or clarify it in that interview. Do not add a mandatory menu when the user's intent is clear. Save a listed workflow ID in `animaguru.project.json` only when it fits; leave it null for a custom brief. Choose from the one-line summaries below first, then open only that one reference; the others add nothing to the chosen film. A problem-to-solution product story usually fits `product-proof`; a new release fits `product-launch`. For a short vertical social ad, also read `animaguru-video`'s `references/short-form-ad.md`.

- **Product Proof Ad** (`product-proof`): Demonstrate an actual product interaction, mechanism or output. Read [the workflow](references/product-proof.md).
- **Product Launch & Feature Reveal** (`product-launch`): Introduce what is newly available with accurate product evidence. Read [the workflow](references/product-launch.md).
- **Comparison & Transformation** (`comparison`): Show a supported comparison under matched conditions. Read [the workflow](references/comparison.md).
- **Offer & Promotion** (`offer-promotion`): Present the actual offer, terms and next step. Read [the workflow](references/offer-promotion.md).
- **Creator & Testimonial Edit** (`creator-testimonial`): Edit supplied speech and media without changing its meaning. Read [the workflow](references/creator-testimonial.md).
- **Editorial Advertorial** (`editorial-advertorial`): Explain a buyer-relevant topic and integrate a product with sourced claims. Read [the workflow](references/editorial-advertorial.md).
- **Brand Identity & Bumper** (`brand-bumper`): Stage the supplied mark and identity through a short signature film. Read [the workflow](references/brand-bumper.md).
- **Game & Reward Promo** (`game-reward`): Show actual gameplay or a clearly illustrative reward reveal. Read [the workflow](references/game-reward.md).

Develop an original sequence from the user's sources, audience, tone, duration and desired outcome. Avoid importing fixed scene counts, mandatory emotional arcs, default audiences or a compulsory CTA. Respect supplied narration/music preferences. Discover AnimaGuru generation models and costs through the local main skill; this purpose selection does not authorize paid jobs.

Use `src/studies/media.ts` for optional deterministic source-time/trim mapping and cue comparison; prepare footage locally and await decoded frames before capture. `npm run review -- --headless` collects actual canvas text bounds, layout warnings, deterministic seek comparisons and review frames; `npm run frames` saves contact sheets for chosen times. Preserve resource timing and the player's embed and MP4 export contract. Review moving playback and audio as well as numerical checks.

Legacy `category: "advertorial"` means Advertisement with editorial intent. Reuse its selected style/brief; when no workflow is saved, use `editorial-advertorial` as the compatible interpretation. Do not re-interview a finished project merely to rename its category.
