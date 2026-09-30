# Qwen Image 2.1 Raw/No-PE Adapter

Compiles a finished SceneSpec into a Qwen Image 2.1 prompt for use without the official prompt expander (PE). The adapter changes wording and density only. Composition and explicitness are already decided upstream. The shared compilation rules (prose, ordering, hierarchy in wording, compression) are in `SKILL.md` section 5.

## Contents

1. Why raw Qwen needs more explicit conditioning
2. Information strategy and length
3. Prompt shape
4. Spatial and relational language
5. Composition, camera, and light
6. Bodies, hands, and gaze
7. Environment, evidence, materials, and transparent background
8. Erotic scenes
9. Examples
10. Compression pass

## 1. Why raw Qwen needs more explicit conditioning

Qwen Image 2.1 is designed around a PE step that rewrites short input into a long, detailed English description. In the user's raw workflow nothing does that rewrite, so the prompt itself has to carry the conditioning the expander would have added. The model should be able to reconstruct:

- what is primary, and what the subject is doing
- how multiple subjects relate, and where the important elements sit
- how foreground and background are organized
- what the camera includes
- how the light sets the hierarchy
- which environmental and physical details carry meaning

The same scene should stay recognizable next to its Krea version. The Qwen version states the spatial and relational facts more explicitly. It does not add decoration, and it does not imitate an expander by inflating a short idea into a long ornamental paragraph. Add information when it resolves ambiguity.

## 2. Information strategy and length

For a substantial scene, consider in order: primary subject → action or state → secondary subject → physical or narrative relationship → relative position → composition and hierarchy → camera and framing → lighting → environment → important material behavior → story-bearing evidence → key target states. Select only the dimensions that improve the requested image.

**Length follows the scene.** There is no word limit. The official PE turns short input into long, paragraph-level descriptions, and Qwen was trained toward that kind of text. So a raw prompt that stands in for the expander is usually a full paragraph, and a complex scene can run longer. Length never justifies equal emphasis, and compression removes repetition, never needed information.

## 3. Prompt shape

A conceptual form, not a template:

`[Primary subject, pose and action]. [Secondary subject and relationship]. [Composition, spatial hierarchy and framing]. [Lighting and environment]. [Key physical, material or narrative evidence].`

## 4. Spatial and relational language

Raw Qwen benefits from explicit spatial phrases wherever placement is ambiguous: `in the foreground`, `deeper in the room`, `partially hidden behind the doorway`, `to the left of the girl`, `between the two figures`, `near the lower edge of the frame`, `smaller in the background`, `occupying the right side of the composition`. Use them to clarify hierarchy or interaction. Objects that don't need a placement don't get one.

Prefer relational clauses over isolated labels. The relationship carries more conditioning than either object alone:

| Label | Relational clause |
|---|---|
| `hand, table` | `Her left hand presses against the tabletop to support her weight.` |
| `second figure, behind` | `The second figure stands behind her and reaches across her right shoulder.` |
| `coat, floor` | `A coat lies crumpled on the floor beside the open suitcase.` |

## 5. Composition, camera, and light

**Composition.** State organization when it matters to the request: `The girl forms the largest shape in the foreground while the doorway figure remains smaller and deeper in the room.` `The bed creates a diagonal from the lower foreground toward the open doorway.` When the scene depends on delayed discovery, say so: `She is the brightest and largest subject in the foreground, while the reflected figure stays smaller and darker in the mirror behind her.` When two subjects are equally important, describe their shared relationship instead of forcing one to be secondary.

**Framing** comes from `camera.md`: always a term plus its visible boundary. Raw Qwen also benefits from placing her on screen (`centered in the upper half of the frame`, `her feet near the lower edge`). Framing keeps important relationships in view: `A medium-wide view keeps both figures and the doorway inside the composition.` `A full-figure composition includes both feet and visible floor space beneath them.` Choose framing because of what the viewer needs to understand.

**Camera position** in visible terms: `The camera stays near eye level, facing her at a slight angle.` `The camera looks down from above, keeping both figures and the disturbed bedding visible as one composition.`

**Lighting** as `source → direction → lit subject → shadow relationship`: `Soft light enters from the window on the left, illuminating the girl's face, hands and the nearest folds of the bed while the doorway stays in softer shadow.` Light can also encode hierarchy: `Her face and hands receive the strongest light, while the suitcase and coat stay visible at lower contrast deeper in the room.` Use several sources only when their relationship matters.

## 6. Bodies, hands, and gaze

**Body interaction** encodes physical logic: what supports weight, what touches, what overlaps, what bends or compresses. `The girl braces one hand against the table as her upper body leans backward, while the second figure stands close enough for their shoulders and arms to overlap.` Describe the interaction as one event rather than two complete character descriptions.

**Hands**, when they carry action, get their function stated: `Her right hand grips the edge of the sheet while her left hand supports her weight against the mattress.`

**Gaze**, when it connects information: `She looks toward the figure in the doorway.` `The two figures look at each other while their bodies stay angled apart.`

**Target states** protect a key requirement: `Both figures remain fully visible inside the composition.` `The open suitcase stays a secondary background detail.` Use them when a real risk exists, not as a fixed suffix.

## 7. Environment, evidence, and materials

**Environment** is a spatial system, not a prop list. Instead of `bedroom, bed, table, chair, suitcase, window`, write `The bed fills the foreground beside the window, while a small table and chair sit against the far wall and an open suitcase rests near the doorway.` That gives location, depth, grouping, and relative position.

**Narrative evidence** is stated directly, because no expander will add it: `Wet footprints cross the floor from the open doorway toward the bed.` The visible evidence usually beats an explanatory clause such as `suggesting someone just came in from the rain`.

**Materials** participate in the scene: `The wet fabric turns darker where it clings to the body and catches small highlights along the folds.` `Condensation beads across the glass and reflects the window light.`

### Transparent background

When the user wants a transparent background or a cut-out asset, wrap the scene description in Qwen Image 2.1's official RGBA phrasing. It is plain natural language, not a special token:

`This is an RGBA image with transparency. [scene description]. The image has alpha channel and the background is transparent.`

In this case, describe only the subject and whatever touches it. An environment would contradict the empty background.

## 8. Erotic scenes

The structure stays the same: `primary event → body relationship → spatial arrangement → composition → reaction → explicit information the level requires → environment → lighting and material consequence`. The E-level decides what is visible. This adapter decides how explicitly the spatial and physical relationships are stated. Physical relationships do the work that repeated erotic adjectives cannot. At high explicitness, settle interaction and spatial logic before local detail. Visible physical consequences follow `event → consequence → location or surface → visible behavior`.

## 9. Examples

**Simple scene.** Input: `girl beside an open window, looking at the rainy street`

A girl sits sideways beside an open window with one knee drawn up, looking down toward the rain-covered street. An eye-level side view framed from the knees up places her on the right side of the frame, with the window and distant street visible behind her. Soft light from the window illuminates her face and hands while the interior stays subdued.

**Narrative scene** (same SceneSpec as the Krea narrative example):

A girl sits on the edge of an unmade bed and turns toward a half-open door, gripping the wrinkled sheet with one hand. A wide shot at eye level shows her full body as the dominant foreground subject on the left side of the frame. The doorway recedes into the background on the right, with an open suitcase beside it and a coat lying on the floor. Soft side light from the window illuminates her face, hand and the nearest folds of the bedding while the doorway stays darker.

Compared with Krea, this states the foreground and background, the left and right placement, depth, and the lighting hierarchy explicitly, because no expander will infer them.

**Multiple characters.**

A girl leans backward against the edge of a table while the second figure approaches closely from her left. Their bodies overlap across the foreground and form a single diagonal composition. Her right hand supports her weight against the tabletop while her head turns toward the other figure. A two-shot framed from mid-thigh up at eye level keeps their body interaction and the edge of the table visible. A narrow side light defines their overlapping silhouettes against the darker room.

**Same scene, model switch.** The designed-look scene from the Krea examples, recompiled with `same scene, Qwen`:

A girl with a short platinum-blonde bob sits sideways on a wide wooden windowsill, one knee drawn up and her chin resting on it, the hem of her oversized gray fleece hoodie bunched around her hips. An eye-level three-quarter front view, framed from the waist up, places her in the right half of the frame, with the tall rain-streaked window and the blurred street lights behind her on the left. Her blue eyes follow the street below. Her phone lies face-up and dark on the sill beside her right hand, half hidden under the long hoodie sleeve, within reach but untouched. Over-ear headphones rest silent around her neck. A white mug sits near the far end of the sill, and a low shelf of paperbacks stands against the dim wall behind her. Cool light from the window illuminates her face, hair and fingers, while the room stays dim and soft. Raindrops streak down the glass beside her shoulder.

The scene and the look are identical. Qwen raw receives more explicit spatial conditioning because no prompt expander fills it in.

## 10. Compression pass

Raw does not mean uncompressed. After adding the needed conditioning, remove duplicated spatial descriptions, restated actions, redundant adjectives, style padding, generic quality terms, materials that do not affect the scene, and explanations the evidence already shows. When the prompt is overloaded, cut from the bottom of this order: event → relationship → composition → action and reaction → explicit information the level requires → lighting → environment → evidence → materials. The result should be detailed enough to rebuild the scene, yet compact enough that the key relationships are not buried.
