# Reverse Prompting From an Image

Reads an image the user provides into a SceneSpec, then compiles that SceneSpec through the adapter the user chooses. The goal is a prompt that regenerates **the same composition** under a different LoRA or model: the same framing, pose, hands, gaze, look, and light, with the rendering style left to the user's stack.

`Image → Read pass → SceneSpec → Model adapter → Final prompt`

Everything after the SceneSpec is the normal pipeline in `SKILL.md`. This file only covers how the image becomes a SceneSpec, and which normal rules change when the image, not the user's idea, is the source.

## Contents

1. Choosing the output format
2. The read pass
3. What changes from normal compiling
4. What stays out
5. Output
6. Example

## 1. Choosing the output format

The output format follows section 2 of `SKILL.md`. When the user hasn't named a model and none is established, ask which one to reverse into (Krea 2, Qwen Image 2.1, Anima, or several) before writing. Several formats come from one read pass and one SceneSpec, so they describe exactly the same image.

The output format is the only thing to ask. The image already answers everything else, including the E-level, the camera, and the girl's look, so never ask the user for those. A user can still add an edit on top ("反推，但改成晚上"), which applies as a named edit after the read pass.

## 2. The read pass

Look at the image in this order and write the answers into the SceneSpec. Frame first, because composition is what the user most needs to survive the LoRA change.

1. **Frame.** Aspect ratio and orientation. Shot size, judged by where the frame edges cut the body (`the bottom edge cuts across her chest`). Where the subject sits (centered, left third) and roughly how much of the frame she fills. How much margin lies above her head. What is cropped or partly outside the frame.
2. **Camera.** Camera height, tilt, and subject orientation, using the terms in `references/camera.md`. A slight tilt or head angle counts when it is visible.
3. **Pose and hands.** What each hand does and exactly what it touches or holds, which hand is higher, where the elbows go, the head tilt, and the body's lean. Hands and contact are what a different LoRA drifts on most, so be precise.
4. **Face.** Gaze direction (at the viewer, away, down), expression, and visible face states such as blush, tears, or a hidden mouth.
5. **Look.** Hair color, length, style, bangs, and loose strands. Eye color. Every garment with its material and how it drapes, folds, or layers. Accessories with their exact location. Describe what is there. The design-a-look rules and `character-looks.md` don't apply.
6. **Environment.** The background as it is. A plain or empty background is recorded as plain (`plain white background`), not filled in. Real settings get their visible objects in their positions.
7. **Light.** The one light logic the image shows: direction, softness, and where shadows fall. Flat, even light is recorded as flat.
8. **Extras.** Any drawn element that isn't the subject, such as a small doodle, an emote, speech bubbles, or effect lines. Keep it at low emphasis with its position, because it is part of the composition.
9. **E-level.** The lowest level that matches what is visible, plus the exposure style. The image sets the level, so it is never asked for, and nothing is added or removed from it. The level changes only when the user asks for it, such as `same scene, E2`.

**Look carefully at uncertain details.** When a detail is too small or ambiguous to read (hair color under colored light, a hidden hand), describe what can be seen at the level of certainty the image gives (`her other hand is hidden inside the sleeve`), instead of guessing a specific object.

## 3. What changes from normal compiling

The image replaces the user's idea as the requirement, so the rules that let the skill invent content are switched off, and the others apply as usual.

- **No invention.** Don't design a look, add concept fusions, escalate boldness, or add objects to reach three environment objects. Every phrase describes something in the image. This includes posture the frame can't show: when the lower body is out of frame, don't say she sits or stands.
- **Keep what the image shows, even when it is unusual.** An odd pose, crop, or garment is a requirement, just like an intentional detail in a text request.
- **Subject tokens still apply.** The female subject is `girl`, and a male is `boy` with minimal description, even when the image shows more of him. When the image shows a character who is clearly a child, don't reverse it, in line with the adult rule in `SKILL.md`.
- **Known characters.** When the image looks like an existing character, still describe the visible look and don't name the character. Name them only when the user says who it is.
- **Composition gets more words than usual.** State the shot size with its frame edges, the subject's position in the frame, and the head margin, because those are what keep composition consistent. For Anima, the camera and framing tags carry this, and the sentences state position and cropping.
- **Weighting (Anima).** When a pose or hand action is the thing most likely to be lost, weight it in place as `references/anima.md` describes.

## 4. What stays out

- Signatures, artist handles, usernames, watermarks, logos, and site marks. They belong to the source post, not the scene. Real in-scene text (a sign, a label) follows the normal text rule.
- The source's art style, medium, line quality, and coloring technique (`thin lineart`, `flat colors`, `watercolor`). The LoRA controls style.
- Artist names and artist tags, even when the signature makes the artist obvious.
- Real-camera terms, as always.

## 5. Output

Follow the output contract in `SKILL.md`: the prompt, or one labeled prompt per model. After the prompts, add one short line in the user's language giving the source aspect ratio and resolution (for example `原圖比例約 3:4 直式（800×1045），生成時用相同比例構圖最一致`), because generating at a different aspect ratio changes the composition no matter what the prompt says. Nothing else unless the user asks to see the reading.

The SceneSpec from the image stays in the conversation, so later requests such as `same scene, E2`, `same scene, Qwen`, or `make it night` edit it like any other SceneSpec.

## 6. Example

Image: a vertical full-body shot of a girl sitting on a stone staircase at dusk. She sits two-thirds up the frame on the right, knees together, holding a paper cup in both hands. A shopping bag leans against her shin, a streetlamp glows at the top left, and a watermark sits in the lower right corner.

The watermark is dropped, and only objects visible in the image appear.

```
Krea 2:
A girl with long black hair tied in a low ponytail sits on a worn stone staircase with her knees pressed together, holding a paper coffee cup in both hands at her lap while she looks down the steps to her left. Her navy wool duffle coat falls open over a cream turtleneck, and a white paper shopping bag leans against her right shin. A slightly low full-body view places her in the right third of the frame, two-thirds of the way up, with the lower steps filling the bottom of the frame. A streetlamp glows at the top left, casting warm light across her face, hands and the cup, while the stairs below fade into blue dusk shadow.
```
