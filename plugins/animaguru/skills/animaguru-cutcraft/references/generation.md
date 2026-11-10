# AnimaGuru generation adapter

## Discover the actual environment

For CLI work, inspect `animaguru --help`, `animaguru schema`, `animaguru auth status`, `animaguru credits` and `animaguru catalog`. Do not read credential files. If it is absent, use connected MCP or obtain agreement to install the CLI; installation and authentication are separate actions.

List projects before choosing one, then inspect the selected project and `assets list PROJECT_ID`. Reuse the user's project where appropriate. Use returned project IDs, asset IDs and file SHAs. Create a separate project when the film needs its own asset container. Saved filenames are not file SHAs.

The CLI catalog describes known capabilities; the live project's `availableModels` and `videoProfiles` describe enabled models. Choose from their intersection; leave the model out to use the studio's choice, which `defaultModels` names per type. A local `--dry-run` with `--model` can succeed for a disabled server model, so it does not prove provider availability.

With MCP, discover the equivalent project, catalog, assets, estimate, generate and job tools. If account linking is needed, let the user complete it. Never invent tool calls or fall back to database access.

## Plan and estimate

Save requests as JSON and validate each with `assets generate ... --dry-run` or a batch with `assets batch PROJECT_ID --file REQUESTS.json --dry-run`. Add all estimates, including speech and any music/SFX, before the first submission. These are AnimaGuru credits; compare returned amounts directly with the authorized credit budget. Actual usage can differ from estimates.

Use only a model and options returned by the live catalog. An image can establish an art direction or become a video reference. An illustrative prompt shell is:

> Original tactile editorial paper collage: matte warm cream cardstock, cobalt blue and fox-orange cutouts, visible paper fibers, slightly imperfect scissor edges, soft short shadows falling down-right. [One concrete composition and action.] Restrained studio lighting and readable silhouettes. Keep a quiet area for separately composed editorial type. No lettering, captions, logos or watermark.

Describe the subject, position, scale and material of each important element. Keep recurring character features verbatim between requests. Exact logos and text belong in the composition, not in model-generated pixels.

## Submit and track

For example, after replacing placeholders with discovered values and validating the settings:

```sh
animaguru assets generate PROJECT_ID --type image --name "cutcraft-keyframe" \
  --model IMAGE_MODEL --aspect-ratio 3:2 --prompt "SAVED ART DIRECTION" --dry-run
animaguru assets generate PROJECT_ID --type video --name "cutcraft-scene" \
  --model VIDEO_MODEL --workflow image-to-video --reference IMAGE_FILE_SHA \
  --seconds 8 --resolution 768p --mode speed \
  --prompt "SAVED VISUAL ACTION" --dry-run
```

The literal values above are examples, not assumed capabilities. Image aspect ratios, video modes, duration limits, soundtrack handling and audio support vary by model. Add `--yes` only for the user's authorized work. Save the queued receipt immediately. Submission results may be job receipts rather than completed assets.

Use `jobs list PROJECT_ID` and `jobs wait PROJECT_ID JOB_ID --timeout SECONDS` to track the original job. A timeout does not cancel it. Check the job and saved assets before resubmitting after an uncertain response. Do not repeatedly regenerate failed work without diagnosing the error and checking the remaining budget.

When a job explicitly fails because its provider is unavailable, preserve that receipt and inspect models from another provider. A replacement with compatible capabilities and an estimate inside the authorized scope can continue the task. Remove unsupported options when changing providers; a seed or prompt-expansion setting valid for one model may be invalid for another. Relay the returned charge or refund status without assuming all failed jobs are free.

Download finished assets with `assets download PROJECT_ID ASSET_ID --output FILE`. Keep stdout receipts separate from media and never overwrite an existing downloaded file inadvertently.

## Choose continuity deliberately

- For different explanatory ideas, use intentional cuts, a shared palette and a common layout. An unrelated next scene does not need the previous clip's last frame.
- For one continuous action, use a supported video extension workflow with the saved video file SHA as `--source`. Inspect the catalog for its resolution and duration limits. `extendOutput` distinguishes the combined video from continuation-only output; inspect and trim any returned overlap rather than counting it twice.
- First/last-frame workflows use `--reference` and `--end-reference` only when the model profile supports them. Both must be saved files belonging to the selected project.
- A locally extracted end frame is not automatically a project asset. Use an explicitly supported upload/import path before referencing it; do not invent an extract-frame or raw upload MCP tool. A character-import command can redraw and charge credits, so it is not a transparent generic frame upload.

Do not carry over the reference workflow's fixed ten-second clip assumption. Choose durations from the model profile and the story, and measure the returned files.

## Narration and assembly

Generate one narrator with `assets generate ... --type speech --prompt TRANSCRIPT`, on the studio's default speech model (`defaultModels.speech` in `assets list`) unless the user names another, with a `--voice` that model takes. Add `--delivery INSTRUCTIONS` only for a Gemini model; ElevenLabs takes audio tags in the transcript instead. Keep the spoken transcript independent of the visual directions. Download and measure the actual recording with `ffprobe`.

For generated motion layers, mute their sound when it conflicts with the separate narration. Reuse or generate a compatible instrumental bed at low level. Keep clip selection, crop, text, logos and all timing deterministic in the composition. Use an existing AnimaGuru HTML/Pixi film workspace when one is supplied; otherwise choose a local composition/export tool suited to the requested deliverable. Keep source files and a reproducible export command.

For controlled cutout animation, request `transparent: true` image assets (CLI `--transparent`) and check the downloaded alpha channel. Keep a subject's complete silhouette inside the image. Animate these assets as separate layers against a fixed setting; drive position, rotation, entrances and holds from absolute time. Use actual transparent silhouettes for a moving subject instead of moving an opaque rectangular illustration. If video providers are all unavailable, this route can complete the film using working image and speech providers without repeated failed video submissions.

Normalize frame size, frame rate and pixel format before concatenation. Export a broadly playable H.264/AAC MP4, or the user's requested format. Check duration, dimensions, audio presence, frame count and representative rendered frames. Preserve truthful asset attribution: motion made with AnimaGuru remains generated footage even when exact typography and editing are composed locally.
