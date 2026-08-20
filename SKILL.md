---
name: voxel-food-photo-editor
description: Edit every supplied food or drink photograph so only edible contents become recognizable voxel-built versions of themselves while tableware, people, packaging, environment, perspective, and lighting stay photorealistic. Use for batch food-photo voxelization, blocky sandbox-game food treatments, or social-media food edits that must preserve the original dish rather than substitute generic game food.
---

# Voxel Food Photo Editor

Turn each supplied food photograph into a reality-versus-voxel image. The visual event is localized: recognizable food becomes block-built geometry inside an otherwise truthful photograph.

## Core Contract

- Process every readable image the user supplies. Do not rank, select, or discard usable images.
- Treat each image as an independent edit target and produce one final output per input by default.
- Never overwrite the source. Save preprocessing and final outputs with distinct filenames in the user-selected destination or a sibling `output` folder.
- Use one image-generation call per input and do not create variants unless requested. Retry at most once per image, and only to correct a clearly observed failure.

## Inspect Each Image

Before editing, inspect the actual image and identify:

- every visible food, drink, sauce, garnish, and edible decoration;
- the dish-specific silhouette, count, colors, layers, arrangement, and identifying details;
- all non-food invariants: people, skin, faces, hands, clothing, plates, bowls, cups, utensils, trays, wrappers, packaging, napkins, furniture, background, camera angle, perspective, focus, lighting, and shadows;
- ambiguous boundaries. Preserve ambiguous objects as photorealistic unless the user explicitly classifies them as edible or permits changing them.

Do not make claims about unreadable or missing files. Skip only files that cannot be decoded and report the reason.

## Food Boundary Rules

Default to food-only voxelization:

- Convert solid food, liquid contents, foam, ice, sauces, toppings, garnishes, and edible decorations.
- Keep plates, bowls, cups, glasses, mugs, chopsticks, cutlery, trays, cake boards, wrappers, branded packaging, and napkins photorealistic.
- For soup, noodles, rice, or food served in a vessel, voxelize the edible contents and keep the vessel real.
- For drinks, voxelize the visible liquid, foam, ice, fruit, or garnish and keep the cup or glass real.
- Keep steam, smoke, reflections, cast shadows, spills outside a vessel, and uncertain residue photorealistic unless the user explicitly requests otherwise.
- Voxelize food containers or tableware only when the user explicitly says “餐具也像素化” or “voxelize the tableware too.”

## Preprocessing

Perform restrained, non-generative preprocessing before voxel editing when it improves presentation:

- correct orientation;
- make a modest crop or alignment correction;
- adjust exposure, white balance, highlights, shadows, contrast, or saturation conservatively;
- use the platform ratio requested by the user; otherwise preserve the source ratio or make only a minimal crop;
- preserve realistic skin, materials, restaurant color, and the original direction of light.

Prefer deterministic local image processing for this stage so non-food pixels do not drift. Save the result as a separate `-preprocessed` file and inspect it before generation.

## Voxel Reconstruction

Compile an image-specific prompt from what is actually visible. Describe each dish rather than pasting a generic food list.

Require the edit to:

- transform only the edible regions;
- preserve the exact food category, count, silhouette, proportions, stacking, arrangement, dominant colors, layers, and distinctive toppings;
- rebuild food from chunky cubes, stepped voxel geometry, square edges, visible block faces, and deliberately low-resolution pixel textures;
- retain believable placement, scale, perspective, occlusion, light direction, and contact shadows within the real photograph;
- remain recognizable as the original meal at thumbnail size.

Default to an original generic voxel sandbox-game language. Do not copy official game textures, item sprites, logos, interfaces, typefaces, or branded assets. If the user uses a game name as shorthand, treat it as descriptive of block-built voxel geometry unless they explicitly provide licensed assets.

## Prompt Shape

Write the final generation prompt in four compact parts:

1. Edit target and the exact edible regions to transform.
2. Dish-specific identity cues that must remain recognizable.
3. Voxel geometry, texture, integration, and contact-shadow requirements.
4. Photorealistic invariants and hard prohibitions.

Repeat the core invariant clearly: change only edible contents; keep all non-food pixels as unchanged as possible.

## Hard Avoids

Avoid generic replacement food, random game items, flat 2D pixel overlays, smooth rounded food, glossy plastic toys, polished 3D-render materials, pixelated tableware, altered packaging, changed faces or hands, new objects, missing food, changed object counts, invented branding, official game assets, text, logos, UI, and watermarks.

## Quality Gate

Inspect every generated image before delivery:

- Every original food or drink remains immediately identifiable.
- Only edible contents are voxelized unless the user requested otherwise.
- Plates, bowls, cups, utensils, boards, packaging, people, and environment remain photorealistic.
- Composition, perspective, lighting direction, occlusion, and contact shadows remain coherent.
- The voxel food uses clear cube faces and stepped geometry rather than a generic pixel filter or plastic-toy look.
- Nothing was added, removed, duplicated, or relabeled.

If one major check fails, regenerate once with a short correction focused only on that failure. If the second result still fails, deliver it with the limitation stated rather than claiming full fidelity.

## Delivery

Return all successful outputs, mapped one-to-one to their input filenames. Report the saved paths, any skipped unreadable files, whether a retry occurred, and the final prompt used for reproducibility. Keep the explanation concise unless the user asks for a detailed comparison.
