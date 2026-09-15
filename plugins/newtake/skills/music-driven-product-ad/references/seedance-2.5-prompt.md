# Seedance 2.5 Horizontal Cross-Section Scrolling Ad Prompt

Use this template to generate a horizontal cross-section scrolling, one-take product ad. Write the Prompt in English and keep it around 1500–2000 characters, with each sentence expressing exactly one visual or action requirement.

## Parameters and Asset Boundaries

- Set the project's total duration, aspect ratio, and resolution in the Seedance interface; this Skill defaults to D = 20 seconds. When the user specifies a duration such as 25 seconds, use D uniformly for all action ranges and the interface duration. The 2.5 in the filename is the model version, not a duration. Keep only the time ranges the continuous action needs in the body.
- Write the two reference tokens exactly as `@图片1` and `@图片2`. They are the interface's reference-image tokens, not words: never translate, renumber or re-spell them, and before submitting confirm they match how the canvas labels the reference images you attached.
- `@图片1` is the single product reference image, used to lock the color, pattern, material, and the product's own text.
- `@图片2` is a 3:4 head-and-shoulders identity image that locks only the protagonist's facial features, hairstyle, and skin texture. The protagonist's outfit is written into the video Prompt; the reference image's background does not enter the video.
- Provide only these two visual reference images to the video model. Describe landmarks, lighting, and spatial forms entirely in text.
- Do not write music, beats, or sync points in the Prompt. Ask the video not to generate background music and to keep only the specific environmental sound of each space; the Zen Piano WAV is composited in post.
- Do not ask the video model to generate an added logo, subtitles, or precise text correction. When the product already has text, lock it via `@图片1`, state that the text must not leak onto other objects, and verify it after output.

## Fixed Template

Replace the square brackets with project content. When the product has no letters or text, delete the corresponding text-containment sentence.

```text
@图片1 is used for the [color, pattern, and material key points] of the [product]. The whole film has only this one [product]. [Letters or text] appear only on the [product], and not on any other object, building, vehicle, or sign.
@图片2 is used for the protagonist's facial features, hairstyle, and skin texture, and appears only at the opening and ending. The opening and ending are the same person, and the image background is not adopted. The protagonist's outfit is [outfit description].

[Generation goal]
A fashion ad, one continuous take, with no cuts, no dissolves, blends, or semi-transparent overlaps. The whole film is one real, continuous horizontal stage cross-section. Space boundaries slide left with the background, not as separate splits or edit wipes. Each space is a flat side-view cross-section with no vanishing point; all structural lines stay only horizontal or vertical. The horizon always sits at the lower quarter of the frame. Camera height, camera distance, and viewing angle stay unchanged throughout. [N] spaces are joined side by side on the same horizon. The space seam is a straight vertical hard edge that belongs to the same continuous stage's background structure. The horizon height, scale, and viewing angle are identical on both sides of the hard edge; lighting may differ. The hard edge slides left across the frame with the lateral move. Before the previous space has fully slid out of the left side, the next space has already entered from the right, and both coexist in the same frame. There is no obstruction at the boundary, only a vertical hard edge.

[Framing and scale]
The whole film is a wide shot with a distant camera. A standing person's height occupies only one quarter to one third of the frame height. Plenty of environmental space remains around the person, and the full scene structure is visible. The [carrier] always stays small. Its fully spread width is no more than one third of the person's height, and for most of its motion it is about head size — a small, eye-catching [color] point in the frame. Person size and [carrier] size stay consistent across all spaces.

[Carrier motion]
The [carrier] continuously [movement verb] from left to right, crossing every hard edge. It [specific description of being driven by the driving force] and does not follow a straight route. It [dynamic 1], [dynamic 2], [dynamic 3], [dynamic 4], and shows [softness, folds, light transmission, reflection, and other material details]. The overall trend is always rightward, and the path is a curve with a sense of breathing.

[Motion direction rules]
All active motion in the whole film moves only rightward. The camera pans right; the [driving force] goes from left to right; the [carrier] [movement verb] rightward; and [vehicles, animals, or objects in each space] move right. All people face right or track right with their gaze, and the protagonist finally walks out of frame to the right. The background layer slides from right to left because of the camera pan, with slight parallax between foreground and background. No active leftward motion appears, and no person turns to face left.

0–[t1] seconds: the camera is still. [Space 1 city or place name], [2–3 iconic visible features]. [Cross-section geometry sentence: camera position; the ground extends horizontally along the bottom edge of the frame; the subject runs across the frame from left to right; only the side facing the camera is visible]. [Lighting], [2–3 environmental details]. [Scene event] has already happened in the first frame. The protagonist [carries or wears the product] and enters from the left edge [hurriedly or at a quick pace], in profile facing right with [pursuit action].

[t1]–[t2] seconds: [write, in order, the specific body actions and physical reason the product leaves the protagonist]. From this moment the camera pans right at a constant speed until second [t_stop]. The [carrier] [movement verb] rightward. The protagonist stays on the left side of the frame and holds [frozen pose]. A vertical hard edge enters from the right edge. To the right of the hard edge is [space 2], with its horizon at the same height as [space 1 horizon].

[t2]–[t3] seconds: [space 2], wide shot. [Cross-section geometry sentence]. [Landmark] appears once in the background layer, facing the camera directly; no partial structure of [landmark] appears in the foreground. [Light direction and color temperature]. The [carrier] [movement verb] rightward in the [lower, middle, or upper] third of the frame, with [one small dynamic change]. [Person], in profile facing right, [near-catch action made of body movement and an obstacle or distance], gaze tracking right. The next vertical hard edge enters from the right; to its right is [space 3], at the same horizon height.

[t3]–[t4] seconds: [space 3], wide shot. [Cross-section geometry sentence]. [Landmark] appears once in the background layer, and the foreground does not duplicate its structure. [Lighting and environmental details]. The [carrier] [movement verb] rightward and completes [dynamic change]. [At most one moving object in the space] moves right, showing only the side facing the camera. The next vertical hard edge enters; to its right is [space 4], at the same horizon height.

[t4]–[t5] seconds: [space 4], wide shot. [Cross-section geometry sentence]. [Landmark, lighting, and environmental details]. The [carrier] [movement verb] rightward in the [lower, middle, or upper] third of the frame. [Person's specific near-catch action], the person faces right, gaze tracking right. The next vertical hard edge enters; to its right is [space 5], at the same horizon height.

[t5]–[t_stop] seconds: [space 5], wide shot. [Cross-section geometry sentence]. [Foreground structure] runs across the foreground as a horizontal line. The [carrier] [movement verb] rightward and gradually lowers within the frame, approaching the protagonist. The protagonist stands in profile at [position], facing right. [Visible environmental effect on her]. She looks up and sees the [carrier].

[t_stop]–[total duration] seconds: the [carrier] drops toward the protagonist, and she [grabs or catches the product]. The camera fully stops at this moment and stays still until the end. She [shows the product briefly, product text facing the camera], then [puts on or stows the product] and completes [a small tidying action]. She turns and walks out of the right edge of the frame in profile, facing right. The frame leaves an empty [space 5] cross-section with [one environmental micro-motion], holds still for two seconds, and ends.

[Consistency]
The whole film has only one [product], consistent with @图片1, and [color, pattern, text] never change. The protagonist at the opening and ending is the same person, consistent with @图片2, with unchanged clothing. Horizon height, camera height, camera distance, viewing angle, and framing stay the same throughout — always a wide shot. Scale is consistent across all spaces. People are the same size in all spaces. The [carrier] is the same size in all spaces and always stays small. Each landmark appears once, only in the background layer.

No background music, keep only environmental sound: [write one specific sound for each space]. The environmental sound of each space transitions smoothly. No subtitles.
```

When using 3–4 spaces, delete the extra space blocks, keep the time ranges continuous, and leave no empty placeholders.

## Placeholder Rules

| Placeholder | How to fill |
|---|---|
| Cross-section geometry sentence | Write visible relationships: the camera is opposite or level with the subject; the ground extends horizontally along the bottom edge; the vehicle runs across the frame showing only one side; the landmark faces the camera directly with a vertical tower |
| Movement verb | One word, consistent across the film, e.g. float, roll, fly, slide, or walk |
| Carrier dynamics | Write 3–4 visible action words such as bob up and down, tumble, spin, speed up and slow down, and add material reaction; do not use "lively" or "vivid" |
| Trigger event | Specify the physical reason the product leaves the protagonist and the order of the body actions |
| Near-catch action | Write the body, obstacle, or distance, e.g. fingertips a palm's width from the rear corner, blocked half a step by a railing, held back by the belt, or a palm's width below the hand |
| Landmark | Write "appears once in the background layer facing the camera directly" and "its structure does not appear in the foreground" |
| Moving object in a space | At most one per space, clearly moving right, showing only the side facing the camera |
| Space 1 opening | Write the place and 2–3 iconic visible features; the event has already started and the protagonist is the pursuer |
| Environmental sound | One audible, specific sound per space; do not write music |

When the London Underground is a space, do not write only "London Underground". Write the visible features such as the red, white, and blue rounded carriages, the curved white-tile walls, and the Underground roundel; then specify that the camera is on the opposite platform, the tracks extend horizontally along the bottom edge of the frame, the train body runs across the frame from left to right, and only the side facing the camera is visible. In the opening first frame, have the doors already closing, with the protagonist entering as the pursuer.

## Known Failure Modes

| Symptom | Fix |
|---|---|
| Depth perspective appears | Do not write only "side view"; add the cross-section geometry sentence for the camera, ground, the subject's run-across direction, and showing only one side |
| Landmark repeats in foreground and background | Do not use objects at the seam; the landmark appears once in the background, and its partial does not appear in the foreground |
| Seam slanted or horizon misaligned | Use an unobstructed vertical hard edge and lock equal horizon height and the same scale on both sides |
| Separate split-screen or wipe instead of lateral move | Specify the same physical stage and the background's continuous leftward slide; do not write it as a mapped split-screen; if the result still does this, honestly label it as not achieving a one-take |
| Dissolve between spaces | Forbid dissolves, blends, and semi-transparent overlaps at the start of the generation goal |
| Sky scene becomes aerial | Write the camera level with the subject, the horizon in the lower quarter, and the sky taking about the upper three quarters |
| Product text copied into the scene | State that the text appears only on the product and not on any other object |
| Carrier moves in a straight line or like a rigid board | Write the carrier motion block separately, using 3–4 specific dynamics and material words |
| Framing too close or carrier huge | Write the framing-and-scale block separately, giving clear numeric ratios for person and carrier |
| Place misidentified | Write the city name and visible colors, materials, signs, or structures, not just the place name |
| Opening action order wrong | Have the scene event already happened in the first frame and make clear the protagonist is the pursuer |

## Newtake Submission Boundary

- Use the live Seedance 2.5 schema to set duration, aspect ratio, resolution, and the two real reference images; do not guess parameter names.
- Generate one one-take video of the full target duration. Do not split it into multiple nodes per space, stitch after generation, or write it as a multi-shot edit.
- The reference order of `@图片1` and `@图片2` must match the uploaded nodes.
- If the live schema has a separate Negative Prompt field, write constraints such as no cuts, no reverse motion, no perspective vanishing point, no camera change, no seam obstruction, no dissolves, no product duplication or text leakage, no protagonist identity drift, and no subtitles or watermark. Do not invent unsupported fields.
