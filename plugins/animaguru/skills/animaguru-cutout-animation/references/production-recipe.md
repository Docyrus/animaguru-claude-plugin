# Cutout production recipe

## Plan reusable layers

Start from the agreed brief and scene plan. List the required subjects, moving parts, props, background planes and textures. Decide which movements need generated video and which can use deterministic Pixi transforms. Reuse assets where appropriate without forcing a fixed cast, number of clips, duration or narrative pattern.

Read the installed AnimaGuru skill and inspect the current catalog, command schema, chosen project and asset list. Use the requested project and models. Save generation requests and receipts, then keep returned IDs, model choices, local files and hashes in the asset manifest. Reconcile an uncertain submission before retrying paid work.

## Generate cutout artwork

Specify the asset's material, framing, silhouette, pose or orientation, perspective, lighting, edge treatment and transparent/keyed background. Match these choices across assets. For articulated motion, plan separately drawable parts and sufficient overlap at joints before generating them.

An object prompt structure to adapt:

> The specified object, isolated with its complete silhouette and generous margin, viewed from the chosen angle, using the project's selected photographic or illustrated treatment. Consistent lighting and perspective with the other assets. Clean transparent background, no text, no incidental scene elements.

For people or animals, add only the casting, expression, wardrobe and pose needed by the brief. For paper or illustrated work, describe material and edge character. Avoid cropping parts that the planned movement will reveal.

Transparent source images are useful. For a video model that flattens alpha, use a uniform key color absent from the subject and props. Specify a locked camera and stable scale when the clip will be composited into an editorial scene. Inspect the output rather than assuming a prompt guarantees a clean key.

## Animate and composite

Keep a generated clip's motion request focused: describe the movement, its starting and ending pose, and whether a clean loop is needed. Choose duration and resolution from the selected model's supported profile. Use returned asset references rather than guessed identifiers.

For still layers, group related pieces in Pixi Containers and define pivots, masks and depth order explicitly. Compute translation, rotation, scale and stepped timing from absolute film time. Use seeded variation only where it serves the chosen material treatment.

Use source video when it preserves useful performance detail; use sprite sheets or still layers where they suit the motion. For green/magenta keying, read `pixijs-custom-rendering` and `pixijs-assets`. Apply a soft matte and conservative spill suppression; inspect fine edges and preserve genuine subject colors. Set the key explicitly per asset.

Exact-frame capture must pause video, seek to the required clip time, await decoding with a bounded timeout, update the texture source, and then render. Clamp or loop within the actual clip duration. Check a loop seam before repeating it.

## Integrate and verify

Keep assets local in `public/assets/` and resolve them with `publicAsset()` so the film also plays when AnimaGuru hosts or embeds it. Register each resource and its real cue times in `src/film-resources.ts`.

Follow the shared video skill for narration, music, factual claims and export delivery when those are part of the brief. Cutout Animation does not prescribe a voice, soundtrack, message, story structure or ending.

Replace the starter's demo scenes, update film timing, preserve the asynchronous capture API, and inspect representative full-resolution frames at transitions and movement extremes. Review the final film and produce the MP4 through the supplied export pipeline, or submit it with `animaguru submit` when the user asks for hosting.
