# Camera and Framing

This pass fills the SceneSpec `CAMERA` field. Every prompt gets a camera decision. When the user names a shot or angle, use it. When they don't, choose the one that best serves the scene (section 1). Model-specific density is in the adapter files. Composition techniques such as depth and negative space are in `composition.md`.

## Contents

1. Choosing a camera when the user doesn't
2. How to write a camera: term plus visible definition
3. Shot size
4. Camera height and tilt
5. Subject orientation
6. Viewpoint: POV, over-the-shoulder, selfie, mirror, peeking
7. Crops, occlusion, and frame-within-frame
8. Two-person and intimate framing
9. Camera and emotion
10. Real-camera terms are filtered out
11. Conflicts and lint rules

## 1. Choosing a camera when the user doesn't

Decide the camera from what the image must show, in this order:

1. **What must be visible?** Identify the body parts and objects the event depends on. The frame must contain these, and the rest of her may fall outside it:
   - The event is a face or expression → close-up or medium close-up
   - Hands, a held object, or touch between people → upper body (waist up) or cowboy shot
   - Stance, a gesture involving the hips, or two people's body distance → cowboy shot or knee shot
   - The whole pose, the full outfit, or where she stands → full body
   - The place tells the story (isolation, scale, a room's evidence) → wide or very wide shot
2. **What does the layout need?** Fit the shot to the layout from `composition.md` section 2. Pull back when the layout needs open space around her, or move in and let the frame cut her when it needs closeness. The frame doesn't have to hug her outline.
3. **What is the emotion or power relation?** Pick the height and angle from section 9: eye level for neutral or everyday scenes, low angle for strength or threat, high angle for vulnerability, a Dutch angle for unease.
4. **Whose view is it?** Use an external camera by default. Consider POV when a boy is the girl's partner and the image should center entirely on her (section 8).
5. **One choice per slot.** Pick one shot size, one placement, one height, one orientation, and at most one viewpoint relation.

Prefer the less obvious choice when it serves the scene better. A waiting scene might use a high-angle wide shot with negative space instead of a default eye-level medium shot. Record the choice in the SceneSpec so it stays fixed across same-scene edits.

## 2. How to write a camera: term plus visible definition

Neither target model has a verified vocabulary of film jargon. A bare term like `cowboy shot` or `knee shot` may be misread, for example as a shot *of* a knee. So write the term followed by what the frame literally contains:

`cowboy shot, framed from mid-thigh up, both feet outside the frame`

The visible part is what actually steers the model. The term is optional support. Build the camera from up to six slots. Placement is always included, and the rest only when this image needs them:

`[shot size + visible boundary], [placement in the frame], [camera height/direction], [subject orientation], [viewpoint relation], [crop or visibility constraints]`

Placement comes from the layout in `composition.md` section 2: where she sits, how much of the frame she takes up, and what fills the rest (`framed from the waist up, she sits in the right third of the frame with the bright window filling the left`).

Keep camera position and the subject's gaze separate. `seen from behind, her head turned back toward the camera` is coherent. `seen from behind, facing the viewer` fights itself.

## 3. Shot size

Shot size describes how much of the body is inside the frame, not how far away the camera is.

| Term (中文) | Write it as |
|---|---|
| Extreme close-up (大特寫) | `extreme close-up, only a small facial detail fills the frame, such as one eye and part of the cheek` |
| Close-up (特寫) | `close-up, the face fills most of the frame, cropped from the top of the head to just below the chin` |
| Bust shot (胸上) | `framed from the upper chest up, with the full head and shoulders visible` |
| Medium close-up (中近景) | `medium close-up, framed from mid-chest up` |
| Upper body (半身、腰上) | `upper-body shot, framed from the waist up` |
| Cowboy shot (牛仔鏡、大腿以上) | `cowboy shot, framed from mid-thigh up, both feet outside the frame` |
| Knee shot (膝上) | `framed from just below the knees up, with both feet outside the frame` (never the bare term) |
| Full body (全身) | `full-body shot, the entire body visible from head to feet with a small margin around her` |
| Wide shot (遠景) | `wide shot, her full body visible at a distance with substantial environment around her` |
| Very wide shot (大遠景) | `very wide shot, her whole figure small in the frame and the environment dominant` |
| Extreme wide shot (極遠景) | `extreme wide shot, a tiny figure seen from very far away inside a vast environment` |

To make a figure large while keeping her whole body in view, write `full body filling most of the vertical frame` rather than combining close-up with full body.

## 4. Camera height and tilt

| Term (中文) | Write it as |
|---|---|
| Eye level (平視) | `camera at her eye height, looking straight ahead` |
| Low angle (仰拍) | `low-angle view, the camera below her looking upward` |
| High angle (俯拍) | `high-angle view, the camera above her looking downward` |
| Bird's-eye (鳥瞰、正上方) | `directly overhead bird's-eye view, the camera looking straight down` |
| Worm's-eye (蟲視、貼地仰拍) | `worm's-eye view from near ground level, looking steeply upward` |
| Dutch angle (荷蘭角、傾斜) | `Dutch angle, the whole camera rolled about 20 degrees so the horizon is visibly tilted` |

Write the camera's direction explicitly. Otherwise `low angle` can turn into the girl looking up, and `Dutch angle` can turn into her leaning while the background stays level.

## 5. Subject orientation

| Term (中文) | Write it as |
|---|---|
| Front view (正面) | `seen straight from the front, both shoulders facing the camera` |
| Three-quarter front (斜前方) | `three-quarter front view, her face and body turned about 45 degrees from the camera` |
| Side view (側面) | `seen from the side at about 90 degrees` |
| Profile (側臉) | `profile view, only one side of her face clearly visible` |
| Three-quarter back (斜後方) | `three-quarter back view, seen mostly from behind with part of one cheek visible` |
| Back view (背面) | `seen from behind, her back facing the camera` |

## 6. Viewpoint: POV, over-the-shoulder, selfie, mirror, peeking

A viewpoint says who owns the camera. Always name the owner and which of their body parts, if any, may appear.

| Term (中文) | Write it as |
|---|---|
| First-person POV (第一人稱、主觀視角) | `first-person POV from the boy's eye position, only his hands entering from the lower foreground` |
| POV with partial body (局部身體主觀) | `first-person POV with only the viewer's [hands / forearms / knees] visible along the lower edge of the frame` |
| Over-the-shoulder (過肩) | `over-the-shoulder view, the edge of the near person's shoulder and head in the left foreground, the girl in clear view beyond` |
| Selfie (自拍視角) | `selfie perspective from arm's length, her extended arm reaching toward the camera, eyes on the lens` |
| Mirror (鏡中) | `she is seen inside a visible mirror, its frame and the real room around it showing that this is a reflection` |
| Peeking or hidden observer (窺視) | `viewed through the narrow gap of a partly open door, the dark door edges blocking both sides of the foreground` |

Describe peeking through its geometry, such as a gap, an edge, or an obstruction, rather than with a mood word like `voyeuristic`. The mood word gives the model nothing to draw.

## 7. Crops, occlusion, and frame-within-frame

Describe a crop as a deliberate framing choice, never as something missing. `missing head` reads as a headless body.

| Technique (中文) | Write it as |
|---|---|
| Head out of frame (頭部出框) | `the top of her head is intentionally cropped by the upper edge of the frame` |
| Limb out of frame (肢體出框) | `her right arm continues naturally beyond the right edge of the frame` |
| Extreme crop (極端裁切) | `extreme crop, the frame cuts through her face so only her lips and chin remain visible` |
| Foreground occlusion (前景遮擋) | `a sheer curtain in the near foreground partly covers the left edge of the frame` |
| Frame within a frame (框中框) | `she stands inside the doorway, the dark doorframe enclosing her on all four sides` |

Always say *where*: which edge, which side, and which part is kept. Open space, diagonals, and other layouts are in `composition.md` section 2.

## 8. Two-person and intimate framing

For two people, state in order: the count, the framing, who is on which side, their orientation, the interaction, the gaze, the overlap, and the crop. Always make it clear whose hand is whose (`her left hand rests on his forearm`).

| Priority | Framing |
|---|---|
| Both faces and expressions | Two-person medium close-up, framed from mid-chest up |
| Expressions plus hand contact | Two-shot framed from the waist up (the safest default) |
| Hands, waists, and body distance | Two-shot cowboy framing, from mid-thigh up |
| Whole poses and the space between them | Full-body two-shot |
| The room or bed is part of the story | Wide two-shot |
| Only the girl should be the visible subject | POV from the boy's eyes |

**POV centered on the girl.** POV fits the minimal-male convention in `SKILL.md`, because the boy becomes the camera instead of a second described figure. Write four things: the camera owner, the only fully visible person, her framing, and which of his parts may enter:

`first-person POV from the boy's eye position; the girl is the only fully visible person, framed from mid-chest up in the center; only his hands and forearms enter from the lower foreground`

Never write `POV of two people`. It leaves the camera owner undefined.

## 9. Camera and emotion

These are common associations, not fixed formulas. The same emotion can be reached in several ways, so choose what fits this scene.

| Choice | Typical effect |
|---|---|
| Extreme close-up | Intense intimacy, obsession, one detail becomes the event |
| Close-up / medium close-up | Emotion and expression first, environment suppressed |
| Upper body / cowboy | Expression and action balanced, stance and presence readable |
| Full body | Pose, outfit, and silhouette take over from expression |
| Wide / extreme wide | Person versus space: distance, isolation, scale, being swallowed by the place |
| Eye level | Neutral, everyday, equal |
| Low angle / worm's-eye | Power, confidence, threat, grandeur |
| High angle / bird's-eye | Vulnerability, smallness, being watched, fate |
| Dutch angle | Unease, imbalance, crisis |
| Profile / side | Contemplation, distance, attention toward something else |
| Back / three-quarter back | Leaving, anonymity, following her, something not yet revealed |
| POV | Presence and participation: the viewer is in the scene |
| Over-the-shoulder | Conversation and relationship between two people |
| Peeking / foreground occlusion | Secrecy, the forbidden, being hidden |
| Frame within a frame | Focus, confinement, inside versus outside |

## 10. Real-camera terms are filtered out

The prompt never contains real-camera hardware or exposure language. That includes focal lengths (`85mm`), apertures (`f/1.4`), ISO, shutter speed, lens types (`telephoto lens`, `fisheye lens`, `macro lens`, `anamorphic`), camera or film brands, film stock, and phrases like `shot on`, `DSLR`, `bokeh`, `shallow depth of field`, or `lens flare`. They describe photographic equipment rather than what is in the frame, and they pull the model toward a photo style the LoRA is meant to control.

When the user asks for one of these, translate the visible intent and drop the spec:

- `85mm portrait` → `medium close-up, framed from mid-chest up, the background softly blurred behind her`
- `fisheye` → `an extremely wide view whose edges curve strongly outward`
- `telephoto compression` → `the distant buildings appear stacked close behind her`
- `shallow depth of field` or `bokeh` → `the background softly blurred` or `the lights behind her blurred into soft circles`

Plain visible descriptions of blur or focus are allowed, because they describe what the image looks like.

## 11. Conflicts and lint rules

- **One value per slot.** Watch for `close-up` with `full body`, `bird's-eye` with `eye level`, and `front view` with `from behind`.
- **Placement is stated.** Every prompt says where she sits in the frame and what fills the rest. Even in a close-up, say which side her face takes and what shows beside it. A prompt without placement usually comes out centered.
- **Visibility gate: write only what this frame, angle, and pose actually show.** Settle the camera first, then check every element against three questions. Is it inside the frame? Does it face the camera from this angle? Does something block it, such as her own limbs, hair, a prop, or another person? If any answer is no, leave the element out. Examples of what the angle hides:
  - From behind: her face, nipples, and pussy are hidden unless she turns or bends to show them. Her back, buttocks, and the nape of her neck are what the camera sees.
  - Side or profile view: only the near breast shows in profile, and a kneeling, sitting, or crossed-leg pose usually hides her pussy behind her thigh.
  - Legs together, a raised knee, or a hand resting in her lap hides her pussy even from the front.
  - Overhead: the top of her head and her shoulders dominate, while her face shows only when she looks up.
  When the user wants something visible that the chosen angle or pose hides, change the angle or pose so it shows (a front view, her knees apart, her torso turned toward the camera). Don't name the part and hope.
- **Nothing visible is left unwritten.** Also check the reverse. Anything the chosen frame clearly shows and the scene depends on, such as her hands, the state of her clothing, or the prop she holds, should be described rather than left to chance.
- **Clothing, body, and action descriptions imply visibility.** Describing her shoes, boots, or legwear pulls the camera out to show them. So does an action that happens outside the frame, such as rising onto her toes in a cowboy shot. Either one breaks a cowboy shot or a close-up. Describe only the outfit parts and actions inside the chosen frame. The rest of the designed look stays in the SceneSpec for other shots.
- **Detail needs scale.** A detailed facial expression doesn't fit an extreme wide shot. Decide which one wins.
- **Resolve conflicts by visibility.** When camera instructions conflict, keep them in this priority: explicit visible boundary → body parts that must be visible → viewpoint owner → camera position → jargon term → mood words.
