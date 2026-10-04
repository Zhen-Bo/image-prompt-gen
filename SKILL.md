---
name: image-prompt-gen
description: Write generation-ready English image prompts for local Krea 2 (precise), Qwen Image 2.1 raw/no-PE, and Anima (booru tags plus natural language). Always use this skill whenever a prompt is needed for Krea 2, Qwen Image 2.1, or Anima, including writing, rewriting, varying, or batching prompts, switching between these models, "same scene" edits, erotic-intensity (E0–E5) changes, and reverse prompting from an image while keeping its composition. Also use it for image requests that name no model, such as "generate an image of ..." or a pasted scene or story, because the skill asks which of its models to target. Do not use it when the request targets any other image model or service, such as GPT Image (gpt-image-1, gpt-image-2), DALL-E, Midjourney, Stable Diffusion, SDXL, Flux, NovelAI, Imagen, Nano Banana, or Seedream.
metadata:
  short-description: Turn visual ideas or images into Krea 2, Qwen Image 2.1, or Anima prompts
---

# Image Prompt Gen

Turn the user's visual intent into a prompt the user can paste straight into a local Krea 2, Qwen Image 2.1, or Anima workflow.

The skill works like a compiler. Reasoning happens internally, and the user receives the finished prompt:

`User intent or image → SceneSpec → Composition → Erotic intensity → Model adapter → Compression → Final prompt`

Composition is solved before model wording, so switching models or E-levels changes how the scene is expressed, never what the scene is.

## Contents

1. Language
2. Before compiling: settle the target model
3. SceneSpec: the one internal scene state
4. Core rules
5. Compiling the prompt
6. Reference routing
7. Output contract
8. Examples
9. Final check

## 1. Language

- **The image prompt is always English.** Every target model conditions best on English, and the user pastes the prompt directly into the generator. The one exception is text that should appear inside the image, which keeps its original language (see "Text inside the image").
- **Everything outside the prompt follows the user's language**: questions, variant labels, and any explanation the user asks for. When the user writes in Chinese, labels and questions are in Chinese while the prompts stay English.

## 2. Before compiling: settle the target model

Supported targets are **Krea 2 precise**, **Qwen Image 2.1 raw/no-PE**, and **Anima**. Each needs different information density (see section 6), so the target must be known before writing.

1. The user names Krea 2, Qwen Image 2.1, or Anima → use it.
2. The user names a model outside these three, such as GPT Image, Midjourney, or Flux → say in one short line, in the user's language, that only Krea 2, Qwen Image 2.1, and Anima are supported, and stop there. Write no prompt for that model, and don't switch to one of the three on your own. Continue only after the user picks one of them.
3. A model was already established earlier in the conversation → keep using it.
4. No model named or established → ask the user which model to compile for before writing any prompt. Keep the question short, in the user's language, and combine it with any other blocking question (such as an ambiguous E-level) so the user answers once.

When the user wants more than one model, compile the same SceneSpec through each adapter and label each output.

## 3. SceneSpec: the one internal scene state

Every request is reduced to a single SceneSpec. All passes (composition, erotic intensity, model adapter) read and update this same state, which is what keeps iterations, E-level changes, and model switches consistent.

| Field | Meaning |
|---|---|
| `PRIMARY` | What the viewer should notice first, including the girl's look (hair, eyes, outfit, accessories) |
| `EVENT` | What is visibly happening, or the state being shown |
| `SECONDARY` | Information that supports, changes, or reveals the primary event |
| `RELATIONSHIP` | How subjects, objects, and surfaces connect (contact, gaze, cause, weight) |
| `MOMENT` | Anticipation, action, interruption, reaction, or aftermath |
| `COMPOSITION` | Hierarchy, depth layers, overlap, visibility, and the eye's path through the frame |
| `CAMERA` | Shot size, camera height, subject orientation, and viewpoint. Always set: the user's choice, or the best match from `references/camera.md` |
| `LIGHTING` | One coherent light logic that supports the hierarchy |
| `ENVIRONMENT` | Setting and relevant objects |
| `EVIDENCE` | One or two visible traces that imply the larger story |
| `EROTIC_LEVEL` | E0–E5 when erotic content is involved, plus the exposure style (full or half-covered) |
| `MODEL` | Krea 2, Qwen Image 2.1, or Anima |

Fill only the fields the request needs. Unspecified fields stay open unless a choice is needed for the scene to be coherent. The SceneSpec is shown to the user only when they ask to inspect the construction.

### Mutation rules

- **`same scene, <model>`**: keep every field except `MODEL`, then recompile.
- **`same scene, <E-level>`**: keep every field except `EROTIC_LEVEL` and the explicit visual information that must change for that level to read naturally. Follow the same-scene transformation in `references/erotic-intensity.md`.
- **Combined change**: apply the E-level change first, then compile through the requested adapter.
- **Named edit** ("make it night", "move her to the window"): change only the named dimensions, plus whatever else must change to keep the scene physically coherent.
- **Generated image came out wrong**: identify the failure category (subject, composition, lighting, interaction, the model adding unrequested elements) and change the one field responsible, so the next result shows whether that change worked.
- **`same scene` with no recoverable prior scene**: ask for the source prompt or scene details instead of inventing them.
- **Minimal edit.** When an edit stays in the same model, start from the existing prompt and rewrite only the phrases the change touches. Every other sentence keeps its original wording. A model switch is the exception, because the format itself changes.

### Multiple versions and themes

The user may ask for several prompts at once.

- **Several versions of a new theme** ("a few versions", "different moments", "different compositions"): keep the theme, the user's specified details, and the girl's look identical in every version. Camera, composition, moment, and light may all change together, so each version gives the theme a clearly different take. Each label names what makes it different.
- **Several versions of an existing prompt** (several E-levels, several models, or edits to a prompt already written): each version follows the mutation rules above, so it changes only what was asked and stays directly comparable.
- **Different themes or scenes**: build an independent SceneSpec for each one.

**Escalating boldness (opt-in).** This mode is off unless the user turns it on by asking, in any language, for each version to be bolder than the last (for example "escalate" or "make each one bolder"). When it is on, version 1 is a strong, conventional reading of the request. Each later version pushes further, with a more daring composition (unusual viewpoint, extreme crop, split or layered framing), bolder material or concept fusions, and more dramatic light. The user's required content and the E-level stay fixed, because boldness here is about visual ideas, not explicitness. Each label names what was pushed. Without the trigger, variants stay equally grounded.

## 4. Core rules

These rules are canonical. Reference files point back here rather than restating them.

### Female subject convention

- Represent a requested female subject with the token `girl`. It is the user's model-specific token for the intended young adult female appearance, so keep it bare and simple.
- Convey appearance through visible properties: hair, expression, physique when relevant, posture, clothing, accessories, gesture, body orientation, interaction.
- Age information stays outside the generated prompt.

### Designing the girl's look

Every girl gets a complete look with four parts: hair color and style, eye color, an outfit with its materials, and one or two signature accessories. Fill in whatever the user leaves open:

- **No look details given**: design the whole look.
- **Some details given** (for example only `black hair`): keep each given detail exactly as stated, and design only the missing parts to match it.
- **A complete character prompt given** (a full description or tag set for the character): use it as given and add nothing to the look.

Base designed parts on popular anime character archetypes so the generation reads as a distinct character rather than a generic default. Style words like `anime` stay out, because the LoRA handles style. How to place these features in the prompt is covered in section 5.

Choose a combination that fits the scene's setting, season, and mood, and vary it from request to request. `references/character-looks.md` has the archetype combinations to draw from.

For erotic scenes, take the outfit from the adult setting, such as loungewear, a dress, a shirt borrowed from the partner, lingerie, or a bathrobe. The clothing state then follows the E-level.

**Concept fusion.** When you design elements the user left open, such as the outfit, a prop, or a material, you may fuse two unexpected ideas into one memorable element (`a wedding veil knotted from old fishing net`, `a lantern made of frozen glass`, `a trench coat lined with pressed autumn leaves`). Use at most one or two fusions per image, and only when they serve the scene's theme. The user's own specified details are never replaced by a fusion.

Record the look in the SceneSpec `PRIMARY` field so it stays identical across same-scene edits, model switches, and variants of one scene. Different themes in one batch each get their own look.

### Male subject convention

- **Leave males out unless they are needed.** Mention a male only when sex is actively happening in the frame, or when the user says a man must appear. Everywhere else, such as aftermath, solo scenes, or a scene that only implies a partner, the prompt contains no male at all. That means no figure, no body parts, and no male belongings left as evidence, such as his shirt or belt. Tell the story through her state and the room instead.
- Represent a male subject with `boy`. Like `girl`, it is the user's token for a young adult male.
- Use `man` or `male` only when the user wants an older male. Generic words for a man, a guy, or a boyfriend, in any language, still map to `boy`.
- Keep male description minimal. Give only what the composition needs: the token, his position, his action, and his contact with others. Leave out his appearance, hair, face, physique, and clothing. When the E-level makes it relevant, name his genitals plainly as part of the event. If the user specifies something about him that belongs to the story (soaked through, holding an umbrella), keep it briefly. Just don't add male detail of your own. The female subject carries the visual description, and extra male detail pulls the model's attention and style away from her.
- The same adult default applies to `boy` as to `girl`.
- When the girl should be the only real focus, reduce his presence further. In order of decreasing presence: his face cropped out of the frame, only his hands or forearms entering the frame, and only his penis entering the frame at E4 and above. `camera.md` covers POV, which makes him the camera itself.

### Other subjects

Name other subjects simply (`the second figure`, `an older woman`, `a cat`), then describe only the visible information the scene needs: identity cues that matter for continuity, silhouette, clothing, and interaction. Demographic detail that doesn't change the image stays out. Once a subject is named, keep the same term across iterations so "same scene" edits stay consistent.

### All characters are adults

Every character in this skill is an adult by default. `girl` and `boy` are the user's tokens for young adults, so a request never needs to state adulthood, and no age check is asked for, at any E-level. Age terms stay out of the prompt.

This default applies to every request. The skill never depicts a character the request explicitly describes as a minor, such as a child or a middle-school student.

### Style is controlled externally

The user's LoRA or generation stack controls global rendering style, so the prompt spends its words on content and organization: subject, action, interaction, pose, composition, framing, lighting, environment, spatial relationships, relevant objects and materials, and narrative evidence.

- Rendering or medium terms (photorealistic, cinematic, illustration, masterpiece, 8k) appear only when the user explicitly asks for them.
- Concrete visible properties that sound stylistic but change the scene, like `harsh red backlight` or `heavy fog hiding the distant buildings`, belong in the prompt.
- Color appears when it does a job: identifying a character, linking two subjects, separating depth, or marking a physical state.

The prompt should remain useful when the LoRA changes.

### Preserve the user's intent

Treat clearly intentional details as requirements, including unusual ones. Keep them even when a more conventional scene would be easier to generate. When a request has many details, protect the required information first, then supporting information, then optional decoration.

### Describe visible evidence

Every important phrase should correspond to something observable in the image. Abstract words leave the model to guess, so convert them into visible evidence when that adds control:

- `tense` → tight shoulders, fingers gripping the chair edge, eyes fixed on the doorway
- `luxurious` → large negative space, dark stone surfaces, brushed brass details, restrained warm light
- `intimate` → close body distance, overlapping silhouettes, quiet eye contact

Stacked praise adjectives (`beautiful, gorgeous, stunning`) carry less information than one concrete description (`loose black hair, relaxed shoulders, a restrained smile`), so replace them.

### State target states positively

When the composition depends on a particular state, describe that state as the goal (`the full figure stays inside the frame with floor visible beneath her feet`, `the second figure stays small and deep in the doorway`). A goal state tells the model what to draw. A list of unwanted outcomes mostly introduces the very concepts it names. Use a brief exclusion only when one specific exclusion is essential and has no positive form.

### Keep constraints coherent

Give each dimension one value: one light logic, one viewpoint, one time of day, one framing. Competing values (soft shadowless light plus hard noon sun, close-up plus full body) force the model to average or pick at random. When the user's own requirements conflict, choose the reading that best serves the primary event, or ask if the choice would change the image substantially.

### Text inside the image

When the scene contains readable text (a sign, a note, a screen), quote the exact wording and say where it appears, for example `a paper sign on the door reads "CLOSED"`. Keep the wording in the language and characters the user gave, without translating it, for example `a paper sign on the door reads "雨宿り"`.

## 5. Compiling the prompt

These apply to both adapters. Model-specific density lives in the adapter reference.

- **Natural prose, not tags.** This applies to Krea and Qwen. Anima uses a tag block followed by prose, as described in `references/anima.md`. Grammar carries relationships. `A girl sits on the edge of the bed, looking toward the open door while one hand grips the wrinkled sheet` says far more than `girl, bed, door, sheet, looking`.
- **Dominant event first.** Default semantic order: primary subject → action or state → interaction → composition → camera/framing → lighting → environment → narrative or material evidence. Reorder when another order reads more clearly.
- **Wording mirrors hierarchy.** The primary subject gets the strongest, earliest language. Secondary details get quieter phrasing (`remain quieter details deeper in the room`) rather than equal-weight inventory.
- **Spread the look along the viewer's path.** Position in the prompt acts as implicit weight, so a block of features pasted at the start tells the model they all matter equally. Introduce the girl with one or two anchor features (usually hair color and silhouette), then attach the rest where they belong: eyes and expression with her gaze, hair movement with her pose, fabric with the body part it covers or moves with, and accessories with the hand or spot they sit on. Every feature of the look still appears once. Spreading them out only changes where each one goes.
- **Give small details a location.** A detail without a position drifts. `a bandage` might end up on any limb or on her face, while `a small bandage across the bridge of her nose` lands where it was meant to go. Name where each small detail sits (hairpin in the left bun, pendant resting on her collarbone, tear on her lower cheek).
- **Clothing has material.** Name each garment's material or texture (`a loose cream knit cardigan`, `a glossy black satin slip dress`, `a cotton yukata with printed morning glories`). Material tells the model how the fabric folds, shines, and reacts to light. For other objects, describe materials by behavior when they matter: linen → `irregular woven fibers, matte surface, soft creases`. Wet skin → `small reflective highlights following the curvature`.
- **The environment has physical things in it.** When the scene has a setting, anchor it with at least three concrete objects or structures, chosen for story value as described in `references/composition.md` (`a rain-streaked window, a low shelf of paperbacks, a mug going cold on the sill`). A bare setting name like `in a bedroom` leaves the space to chance. The exception is a user who asks for a plain background, a minimal scene, or a transparent background.
- **Camera in visible terms.** Every prompt states its camera: the user's choice, or the best match chosen through `references/camera.md`. Write each term with what the frame literally contains (`cowboy shot, framed from mid-thigh up`). Real-camera terms such as focal length, aperture, ISO, lens types, and `bokeh` never appear, even on request. They are translated into visible framing and blur instead.
- **E-levels stay internal.** The prompt never contains `E0`–`E5`. It contains the visible scene information that level implies.
- **Compress last.** Remove repeated synonyms, restated actions, decorative adjectives, and details another phrase already implies. Protect who acts, who reacts, what touches what, relative position, hierarchy, and story-bearing evidence.
- **One copyable paragraph.** Output continuous prose with complete sentences and no hard line breaks, so it pastes cleanly into the generator. For Anima, the prompt is the tag block, a blank line, then the prose, all as one copyable prompt.

## 6. Reference routing

Read only what the request needs. Each file has a contents list at the top.

| Read | When |
|---|---|
| `references/krea.md` | Every Krea 2 prompt (density, prompt shape, examples) |
| `references/qwen.md` | Every Qwen Image 2.1 raw prompt (density, spatial language, examples) |
| `references/anima.md` | Every Anima prompt (tag rules and order, safety tag, camera tags, weighting) |
| `references/camera.md` | Every prompt (shot size, angle, viewpoint, crops, choosing a camera when the user doesn't) |
| `references/composition.md` | Multiple subjects, primary + secondary themes, story text, complex environments, composition or moment variants, or a scene that risks becoming an object list |
| `references/erotic-intensity.md` | Any erotic content, an E-level request, or a same-scene E-level change |
| `references/character-looks.md` | Part or all of the girl's look is left open by the user and earlier conversation, and no complete character prompt was given (not for reverse prompting) |
| `references/reverse-prompt.md` | The user gives an image to reverse into a prompt, to recreate its composition |

A simple single-subject scene usually needs only the adapter file and `camera.md`.

### Erotic-intensity levels

| Level | Name |
|---|---|
| E0 | SFW |
| E1 | Suggestive |
| E2 | Sensual |
| E3 | Erotic nudity |
| E4 | Explicit |
| E5 | Fully explicit |

Users may name a level by its number, its name, or an equivalent word in their own language.

Use the level the user states, or normalize equivalent wording to the nearest level. When the request clearly implies a degree of explicitness, use the lowest level that faithfully represents it. When two readings are equally plausible and would produce clearly different images, ask. Explicitness rises only when the user asks for it.

### Exposure style: full or half-covered

This rule applies at every level from E2 to E5. The E-level decides *what may be seen*. The exposure style decides *how clothing relates to it*.

- **Full**: nothing she wears covers what the level shows. Only accessories remain, or nothing at all.
- **Half-covered**: clothing is still on her but frames the exposure. A shirt hangs open over one breast, panties are pulled aside, a skirt is lifted, or wet fabric has turned see-through. Partial coverage often reads as more erotic than full nudity, because it shows a moment of undressing and leaves something withheld.

**Who decides.** When the user asks for half-covered, partially clothed, half-undressed, or glimpsed-through-clothing exposure, in any language, use half-covered. When they ask for full nudity, use full. Otherwise choose whichever serves the scene better:
- Half-covered when the clothing carries the story: undressing is in progress or was interrupted, the costume's identity matters (maid, uniform, kimono), there's secrecy or a hurry, or it's the aftermath of something done with clothes on.
- Full when the body itself is the subject: bathing, a hot spring, posing to be seen, lying in bed afterward, or a setting where clothes make no sense.

**What each level shows in half-covered style.** The style never hides what the level requires:
- **E2**: clothing slips and reveals skin up to the edge, such as the underside of a breast, a bare hip, or a nipple's outline through wet fabric, with no nipple or pussy exposed.
- **E3**: at least one of her nipples or her pussy is exposed. Name exactly which parts are bare and which are still covered: `her shirt hangs open on the right, baring her right breast and nipple, while the left side still covers her other breast`.
- **E4 and E5**: the sex act or explicit detail stays fully readable. Clothing is pushed aside, lifted, or open around it, never over it.

Always state the split of exposed and covered parts explicitly. A vague phrase like `partially revealing` lets the model cover everything. Record the style in the SceneSpec with the E-level, so same-scene edits keep it unless the user changes it.

### Explicit vocabulary

These are the standard terms for what E2 to E5 show. Use a term only when the E-level allows what it shows and the visibility gate passes. Every model uses the same words: Anima puts them in the tag block, and Krea and Qwen write them inside sentences.

- Body state: `nude`
- Pose: `spread legs`
- Act: `fellatio`, `sex`
- Fluids: `cum`, `cum in mouth`, `cum drip`
- Male anatomy: `penis`

## 7. Output contract

**Single prompt**: return only the finished English prompt.

**More than one model**: label each prompt with the model name.

```
Krea 2:
[prompt]

Qwen Image 2.1:
[prompt]

Anima:
[prompt]
```

**Several versions or themes**: one short label per prompt in the user's language, stating what distinguishes it, followed by the prompt:

```
1. [label, e.g. Before: a figure in the doorway]
[prompt]

2. [label, e.g. After: the scattered coat]
[prompt]
```

Add a compact explanation after the prompt only when the user asks to see the construction. Negative prompts, token weights, tag syntax, and parameter suggestions appear only on request. Anima's tag block and its limited weighting are part of the Anima format itself.

## 8. Examples

Example prompts live in each adapter file (`references/krea.md` section 5, `references/qwen.md` section 9, `references/anima.md` section 9). Read only the target model's examples.

## 9. Final check

Before returning, silently confirm:

- The user's required content is present, and the image shows an event rather than an inventory. When a camera you chose crops out something the user specified, change the camera.
- The primary subject reads first. Secondary information supports or reinterprets it at lower emphasis.
- Positions, contact, and weight are physically coherent. Multiple characters read as one interaction.
- Female subjects use `girl`, no age terms appear, and no unrequested style terms were added.
- Constraints are coherent (one light logic, one viewpoint).
- The camera is stated in visible terms, and no real-camera terms appear. Every described element passes the visibility gate in `camera.md`: it is inside the frame, faces the camera from this angle, and is not blocked by her pose. Nothing the frame clearly shows and the scene depends on is left out.
- The E-level matches the request and composition still carries the image. Same-scene changes preserved the scene.
- Wording and density fit the selected model. The prompt is English, one copyable paragraph, and every sentence adds visible information.
