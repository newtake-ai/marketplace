# Two Reference Images and Identity Lock

The horizontal cross-section scrolling ad uses only two visual reference images, written `[ref1]` and `[ref2]` here for the canvas's own reference-image tokens. `[ref1]` locks the single product; `[ref2]` locks the same protagonist at the opening and ending. Landmarks, lighting, spatial forms, and seams are all defined through the video Prompt, so extra reference images do not introduce a perspective camera or the wrong framing.

Prefer reusing real assets the user provided and confirmed. When an asset is missing or unusable, generate it with **Seedream 5.0 Pro**, inspect it, and only then submit to Seedance 2.5. The asset images carry texture and format; fill in the specific appearance per project.

## [ref1]: The Single Product

Product image requirements:

- a single product laid flat or shown front-facing, in 1:1 or the product's original aspect ratio;
- the product fully spread, with no cropping;
- a pure-white seamless background `#ffffff` with soft, even studio lighting;
- clear color, pattern, material, shape, signature structure, and product text;
- no extra products, extra text, or unrelated accessories.

General Seedream 5.0 Pro Prompt:

```text
Flat lay product photo of a single [product type], laid perfectly flat and fully spread, [color, pattern, and text description], clean minimal graphic design, no other text, [no logo or exact logo requirement], visible [material] weave texture and soft sheen, shot straight from above, plain seamless pure white background #ffffff, soft even studio lighting, photorealistic, [aspect ratio]
```

If the product carries letters, text, or a logo, verify it character by character after generation. The video Prompt must state that these elements appear only on the product and are not copied onto buildings, vehicles, signage, or other objects.

Write one concise product definition that includes at least:

- the product category and its distinctive silhouette;
- geometric proportions, materials, surface finish, and color;
- pattern, stitching, seams, fasteners, or other identifying details;
- the position, orientation, and exact spelling of the product text or logo;
- the product's scale relative to the person;
- forbidden wrong colors, wrong materials, extra accessories, and duplicates.

The whole film has only this one product. As it leaves the protagonist, travels through the spaces, and returns to the protagonist, its appearance, scale, and text must remain continuous — it cannot vanish, duplicate, be replaced, or deform.

## [ref2]: Same Protagonist at Opening and Ending

The protagonist image only locks the facial features, hairstyle, and skin texture. Clothing is fully described in the video Prompt; do not rely on the asset image's clothing to lock it.

Protagonist image requirements:

- a 3:4 vertical head-and-shoulders close-up;
- a pure-white seamless background `#ffffff`;
- real, visible fine skin texture and a healthy sheen, avoiding a plastic look;
- clear facial features, bone structure, makeup look, hairstyle, hair color, expression, and gaze;
- no logo and no unrelated accessories.

General Seedream 5.0 Pro Prompt:

```text
[person type and style] high-fashion model, [bone structure and facial feature description], [makeup look description], [hairstyle and hair color], [realistic skin texture description], real not plastic, [expression and gaze], wearing [clothing key points, optional], no logo, no accessories, plain seamless pure white background #ffffff, soft clean studio lighting, photorealistic premium fashion magazine quality, head-and-shoulders portrait, vertical 3:4
```

Generate or submit only one protagonist identity image. The video Prompt must be explicit: the opening and ending show the same person; `[ref2]` provides only facial features, hairstyle, and skin texture; the reference-image background is not adopted; and the protagonist wears one project description of clothing throughout the film.

## Carrier, Framing, and Contact Relationship

Prefer the product itself as the rightward-moving carrier. Specify clearly, based on the product's attributes:

- how it is carried, worn, held, or supported at the opening;
- which specific physical actions, in which order, make the product leave the protagonist;
- the product's consistent movement method across the spaces and 3–4 visible dynamics;
- the material, folding, light transmission, or reflection behavior while the product moves;
- how it is caught, received, shown, worn, or stowed at the ending;
- whether the opening and ending contact relationships match real usage.

The protagonist reference image does not provide full-body scale. The video Prompt must lock it with numbers: a full-film wide shot, a standing person's height at 1/4–1/3 of the frame, the carrier's fully spread width no more than 1/3 of the person's height, and usually about head size while in motion.

## Checks

- Does `[ref1]` contain exactly one complete product, with accurate color, material, and text?
- Is `[ref2]` a clear 3:4 head-and-shoulders identity image with realistic skin and a pure-white background?
- Does the video Prompt separately specify the protagonist's outfit and keep it consistent at the opening and ending?
- Does the product have a text-containment rule?
- Does the product keep continuity and small scale when it leaves the hand, moves, and is caught again?
- Are only these two visual reference images provided to Seedance, with no landmark, scene, or lighting reference images?
