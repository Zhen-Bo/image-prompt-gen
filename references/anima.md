# Anima Adapter

Compiles a finished SceneSpec into a prompt for CircleStone Labs' Anima. Anima was trained on booru-style tags, natural-language captions, and mixes of the two, so its prompt is a hybrid: a tag block that anchors *what is in the image*, followed by natural language that explains *how the pieces relate*. Composition, camera, explicitness, and the visibility gate are decided upstream exactly as for the other adapters.

## Contents

1. Prompt shape
2. Tag rules
3. Tag block order
4. What goes in tags and what goes in sentences
5. Subject tokens
6. Camera tags
7. Weighting
8. What stays out
9. Example

## 1. Prompt shape

```
[tag block, comma-separated, ending with a period]

[natural language: one paragraph in four parts]
```

The tag block comes first and the sentences follow. Anima accepts any order, but this split keeps the anchors and the relationships apart. The natural-language part is exactly one paragraph with no blank lines inside it, so the whole prompt is one tag block plus one paragraph. Write the paragraph in four parts, in this order, giving each part one or two sentences:

1. **Her and the action**: her hair, eyes, and expression, and what she is doing.
2. **Clothing and contact**: each garment with its material and current state, each accessory where it sits, and what her hands and body hold or press against.
3. **Camera and layout**: the shot and camera position, where she sits in the frame, the open area, and what leads the eye to her. Booru tags have no reliable way to place a subject, so the layout lives here.
4. **Light and evidence**: where the light comes from and what it falls on, the environment objects that matter, and the traces that tell the story.

There is no word limit, and length follows the scene. Never drop visible information to make the paragraph shorter. A part with nothing to say for this image may be brief, but keep the order.

## 2. Tag rules

- Lowercase, with spaces instead of underscores: `long hair`, `looking at viewer`, `hand on another's head`.
- Use booru-style tags that actually exist. When Danbooru and Gelbooru name the same concept differently, prefer the Gelbooru form.
- A concept with no real tag goes in the sentences. Don't invent tag-shaped phrases like `gold flecked iris` or `head bowed slightly`.
- Anima was trained with random tag dropout, so the block doesn't need every visible concept. Aim for roughly 15 to 35 tags that anchor the image.

## 3. Tag block order

Follow Anima's section order. Order within a section doesn't matter, so a tag's position is not a way to emphasize it.

1. Subject count: `1girl`, `solo`, `1boy`, `2girls`
2. Character and series, only if the user names an existing character
3. General tags: appearance, clothing, pose, action, anatomy, environment, camera, light

## 4. What goes in tags and what goes in sentences

**Tags carry discrete visual anchors:** hair color and style, eye color, named garments and accessories, body state (`sweat`, `blush`, `tears`), anatomy the visibility gate allows, pose (`kneeling`, `seiza`), the explicit terms under "Explicit vocabulary" in `SKILL.md`, setting objects (`tatami`, `paper lantern`), camera (section 6), and simple light (`backlighting`, `sunlight`).

**Sentences carry everything relational or fine-grained:** who does what to whom, what covers what, where she looks, where each person or object sits in the frame, the exposed and covered split for a half-covered style, materials and how they behave, the narrative evidence, and how the light falls.

The sentences may mention a tagged feature again, and when they do, they add what the tag can't say: its material, color, position, and state. Don't copy the tag block into the sentences as a bare list. A tag like `seiza` plus a sentence like `She kneels in seiza beside the low table, pouring tea with her gaze lowered` is the right division.

**Multiple people:** attribute appearance in the sentences (`the girl with [her hair] stands on the left`), because a flat tag list can't say which trait belongs to whom.

## 5. Subject tokens

- The tag block uses booru subject tags: `1girl` for the female subject, and `1boy` only when the male convention in `SKILL.md` allows a male to appear.
- The sentences follow `SKILL.md`: `girl` for her, `boy` for him, and the same minimal male description.
- A reduced male uses tags that match his reduced presence: `pov`, `faceless male`, `out of frame`, `pov hands`, or just the male anatomy tag from "Explicit vocabulary" in `SKILL.md` for the anatomy that enters the frame.

## 6. Camera tags

Translate the SceneSpec camera into booru tags, and keep the visible definition in the sentences:

| Camera | Tags |
|---|---|
| Close-up | `close-up` |
| Bust or medium close-up | `portrait` or `upper body` |
| Upper body | `upper body` |
| Cowboy shot | `cowboy shot` |
| Knee shot | `feet out of frame` |
| Full body | `full body` |
| Wide / very wide | `wide shot` / `very wide shot` |
| Low angle | `from below` |
| High angle / bird's-eye | `from above` |
| Dutch angle | `dutch angle` |
| Front / side / profile / back | `facing viewer` / `from side` / `profile` / `from behind` |
| POV | `pov` |
| Head cropped | `head out of frame` |

Real-camera terms stay filtered out, as in `camera.md`.

## 7. Weighting

Anima supports numeric weights in ComfyUI, `(concept:1.6)`, and needs larger values than SDXL to show an effect. Use a weight only for the one or two concepts the image depends on most and the model is most likely to drop, such as the key act, an unusual pose, or a camera angle. Use values between 1.4 and 2. Weight the tag where it already sits in the block, for example `fireworks` becomes `(fireworks:1.5)` in place, so no tag appears both plain and weighted. Everything else stays unweighted. A steep contrast between one weighted anchor and plain tags works better than weighting many things.

## 8. What stays out

- Safety tags (`safe`, `sensitive`, `nsfw`, `explicit`).
- Quality and score tags (`masterpiece`, `best quality`, `score_7`), year tags, and meta tags. The user's workflow injects these at its own fixed points. Add them only on request.
- Artist tags (`@artist`) and style tags. The LoRA and the workflow control style. Add them only on request.
- Negative prompts, unless asked.

## 9. Example

SceneSpec: a girl kneels in seiza pouring tea in a lantern-lit tatami room, E0, eye-level front view, framed from the waist up. Identity line: a tea-house apprentice serving the last guest of the night, wearing her late grandmother's jade earrings. Layout: she sits in the right third, the table edge leads from the lower left corner to her hands, and the dim room stays open on the left.

```
1girl, solo, black hair, hime cut, blunt bangs, sidelocks, green eyes, jade earrings, kimono, obi, seiza, holding teapot, cup, tatami, low table, paper lantern, indoors, upper body, facing viewer, warm lighting.

A girl with straight black hair cut in a neat hime style kneels in seiza behind a low lacquered table, tilting a ceramic teapot as a thin stream of tea fills the cup in front of her, her green eyes lowered to the pour with quiet concentration. Her deep indigo silk kimono is tied with a pale gold obi, her left hand holds the wide sleeve back so it clears the cup, and a pair of old jade drop earrings hang still beside her jaw. An eye-level front view framed from the waist up places her in the right third of the frame, the long edge of the table running from the lower left corner to her hands, while the left side of the frame stays dim and open. A paper lantern on the tatami near the right edge casts warm amber light across her face, her hands, and the steam that curls into the dark open space, and a second cup waits untouched at the far end of the table.
```

The four parts appear in order: her and the pour, the kimono and earrings with her sleeve-holding hand, the camera and layout, then the lantern light and the waiting cup.
