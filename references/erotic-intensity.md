# Erotic Intensity

This pass sets the SceneSpec `EROTIC_LEVEL` field and adjusts only the visible information that level requires. It controls one dimension: **how directly sexual information participates in the visible image.** The adult-by-default rule, the `girl` convention, and the level aliases live in `SKILL.md`.

## Contents

1. The core idea
2. Levels E0–E5
3. What E-level does not control
4. Same-scene transformation
5. Hierarchy: erotic as primary or secondary
6. Bodies, contact, and reaction
7. Hands, clothing, surfaces, and materials
8. Bodily fluids and physical consequence
9. Light and framing
10. Keeping the image a composition
11. Erotic-specific check

## 1. The core idea

Explicitness and artistic quality are separate axes. Lowering explicitness does not add story, and raising it does not remove story. What makes an explicit image strong is that the intimacy is the scene's verb: it expresses a relationship, a moment in time, trust, vulnerability, power, departure, or memory. It is never just a pose on display.

So the same scene can be rendered at any level while its story, composition, camera, environment, lighting, and relationships stay the same. Only the directness of sexual information changes.

A useful internal test: mentally replace the explicit content with plain body shapes. If the image still has a clear relationship, light, space, and tension, the explicit version will be strong too. If nothing is left, strengthen the scene before adding explicitness.

## 2. Levels E0–E5

| Level | Goal | Main visual tools |
|---|---|---|
| **E0 SFW** | Attraction or closeness exists, but the scene reads as ordinary. The primary event can be conversation, travel, waiting, rest, reunion, or conflict. | Expression, eye contact, ordinary touch, distance, shared activity. Example: `a girl rests her head against the other figure's shoulder as they watch the same window` |
| **E1 Suggestive** | Tension is communicated through implication: *something may happen* or *has almost happened*. Works best with anticipation. | Prolonged gaze, faces close while bodies stay apart, restrained touch, clothing arrangement, interrupted gestures, partial visual access through a doorway or reflection |
| **E2 Sensual** | Physical intimacy becomes a principal subject, with selective restraint. | Meaningful skin contact, close overlap, touch that visibly changes the other's posture, clothing responding to gesture, tactile material relationships |
| **E3 Erotic nudity** | Nudity with no sexual activity, either full or half-covered (see "Exposure style" in `SKILL.md`). Exposed nipples and pussy are named plainly when the frame shows them. Nudity becomes a deliberate compositional element: silhouette, exposure, vulnerability, trust. | The body as part of the shape language: direction, limb arrangement, overlap, negative space, directional light. Remaining clothing becomes narrative (transition, interruption, aftermath). Environment matters more here because it keeps nudity from flattening into a generic pose. |
| **E4 Explicit** | Sexual activity becomes a clearly readable event and can hold the primary layer. | Build it as `action → contact → reaction → consequence`, not a list of body parts. Relative orientation, balance, weight support, meaningful hand placement, expression, environment. |
| **E5 Fully explicit** | Explicit anatomy, activity, and relevant bodily-fluid information can appear directly as parts of the event. | Sort explicit information into event-defining (what is happening), event-supporting (clarifies contact or consequence), and incidental (stays subordinate). Give prompt detail in that order. |

At E3 and above, ask what the visible body or explicit detail tells the viewer that the rest of the scene does not: the exact event, its consequence, the chronology, a reaction, trust, or exposure. A detail that adds nothing new gets lower priority.

## 3. What E-level does not control

These are separate variables, so an E-level change leaves them where they are:

- **Camera distance.** A higher level does not mean a closer camera. E5 can be full-body, environmental, or seen through a doorway. E2 can be a close-up. Choose framing for story and readability.
- **Prompt length.** A simple E5 scene may need fewer words than a complex E1 scene with several characters and layers. Length follows scene complexity.
- **Style.** Moving E2 → E5 adds no terms like cinematic, glamour, or photographic. Style stays with the user's LoRA.
- **Emotional tone.** Any level can be affectionate, playful, tense, melancholic, awkward, or calm. Infer tone from the request.
- **Narrative moment.** Anticipation, active event, interruption, and aftermath all exist at every level. Choose the moment for the story, not for explicitness.

## 4. Same-scene transformation

For `same scene, E[n]`, lock character count and identity, environment, major props, primary and secondary story, narrative moment, camera position, framing, perspective, lighting direction, and hierarchy. Then change only what the new level requires. This is what makes E-level comparisons meaningful. The result should look like one information channel turned up or down.

**Going up**, implication becomes direct visible information step by step: relationship (E0) → sexual implication (E1) → sensual interaction (E2) → nudity within the interaction (E3) → directly readable sexual activity (E4) → directly visible explicit detail (E5).

**Going down**, the same meaning moves into less direct evidence: posture, proximity, gaze, clothing state, overlap, occlusion, partial visibility, anticipation, aftermath, or reaction. The lower version should feel like another take of the same scene, not a replacement.

Make the smallest compositional adjustment needed for the new level to read naturally, such as a slight shift in a pose or in how clothing falls.

The level applies to the scene as a whole, not only the primary subject. Name the girl's new state once, plainly (`nude`), and let visible evidence carry the rest. Male participants follow the minimal male convention in `SKILL.md`: their change shows only through position, contact, and, at the levels that need it, their genitals, never through added description of their clothing or body. Discarded clothing that stays in the room is useful because it shows the transition.

## 5. Hierarchy: erotic as primary or secondary

**Erotic as primary.** The physical interaction is the central event, and the environment and secondary objects explain or intensify it. A non-erotic secondary concern gives story density without adding explicitness:

- intimacy + packed luggage → departure
- intimacy + incoming daylight → time passing
- intimacy + half-open door → exposure or interruption
- intimacy + unfinished work → competing priorities

**Erotic as secondary.** Another event is primary (waiting, reunion, secrecy, aftermath, memory) and intimacy changes how it reads. The erotic information stays subordinate even when the level would allow more. A level sets what *may* be visible, not how much emphasis it gets. Follow the user's hierarchy.

For explicit scenes, a three-layer structure keeps the 1/3/10-second reading order from `composition.md`: the central interaction (primary), a reaction or meaningful environmental element (secondary), and story evidence found on closer inspection (tertiary).

## 6. Bodies, contact, and reaction

**Large geometry first.** For complex interaction, settle: torso orientation → pelvis and weight when relevant → limb support → major contact → head direction → gaze and expression → hands → local surface detail. Describing many local details before the bodies connect produces an unreadable pose.

**Connected shapes.** Interacting bodies form one silhouette with internal rhythm, not two equal character cards. Overlap communicates intimacy, dependence, control, or concealment. Negative space between bodies communicates separation, anticipation, or tension.

**Action and reaction in pairs.** Describe the response, not only the action: touch → response, weight → support, approach → acceptance, hesitation, or retreat, gaze → returned or avoided. The reaction can show through shoulders, hips, balance, distance, or hands as well as the face.

**Several participants.** Map `A → action → B`, `B → reaction → A`, and `C → relationship to the central event`, then group the bodies so the viewer can tell who interacts with whom.

## 7. Hands, clothing, surfaces, and materials

**Hands** carry intention, pressure, hesitation, support, and reaction. Describe what they do: `one hand grips the edge of the sheet`, `both hands brace her weight against the table`.

**Clothing** is visible state and consequence: still orderly, partly displaced by movement, gathered around the body, lying elsewhere in the room, compressed between bodies, or stretched by posture. It should respond to pose, gravity, and contact.

**Revealing outfits have to be written as exposure, not as garment design.** A garment noun like `maid dress`, `uniform`, or `bodice` carries a strong prior for full coverage. A phrase such as `a cut-away bodice` leaves the model to decide how much it cuts away, and it usually draws the covered version. So, when the user asks for a revealing or exposing outfit (穿著裸露, 暴露):

- State the nudity first, right after the subject: `a nude girl`, or `a girl, bare-breasted`.
- Then list only the pieces she wears, framed with `only`: `wearing only a white frilled apron tied at her waist, a lace maid headband, a black choker, and white thigh-high stockings`. Every piece not listed reads as absent.
- Name the exposed body parts plainly and early. Don't imply them through the cut of a garment: `her breasts and hips are bare`, `the apron hangs open at the sides, leaving her hips and the curve of her waist uncovered`.
- Keep the costume's identity (maid, bunny, nurse) in accessories and small pieces, such as the headband, cuffs, collar, apron, and stockings, rather than in a full garment that would cover her.

The level still decides how much is shown. At E1 and E2 the same method describes partial exposure (`a sheer apron over bare skin`, `shoulders and back bare`). At E3 and above it describes nudity.

**Name anatomy plainly from E3 up.** Words like `bare breasts` or `nude` alone let the model smooth the body over, so write the visible anatomy directly: `her nipples`, `her pussy`, and at E4 and above, `his penis` when it takes part in the event. Two things to check:

- **Coverage follows the exposure style.** In full style, no apron, sash, garter, hand, or prop sits over her nipples or pussy. In half-covered style, state exactly which parts the clothing still covers and which are bare. Either way, no accidental prop covers what should show. Place accessories elsewhere, for example `a short apron tied at the back of her waist, its ties trailing behind her hips`.
- **The frame, angle, and pose show it.** Name only anatomy that the chosen shot, camera angle, and pose actually reveal. A close-up has no pussy to name, a back view hides her nipples, and a side-kneeling pose tucks her pussy behind her thigh. If the level calls for it to be seen, choose a camera and pose that show it. See the visibility gate in `camera.md`.


**Surfaces** make the scene physically coherent. Ask what supports the weight, what compresses, folds, or stretches, what reflects light, and what keeps traces of contact.

**Materials** are described by behavior, and only when relevant:

- **Skin**: soft compression at contact points, highlights following curvature, subtle pressure marks, moisture catching the light
- **Fabric**: folds following gravity, stretched or compressed weave, wet fabric darker and more reflective
- **Bedding**: compression under weight, pulled edges, directional creasing, displaced pillows
- **Glass**: reflection, condensation, fingerprints, distorted background shapes

## 8. Bodily fluids and physical consequence

Sweat, tears, water, and other bodily fluids are most effective as evidence of the event: time, exertion, the aftermath, contact between subjects. Decide the function first (an ongoing event, an immediate consequence, aftermath, contact with clothing or the room). Then describe only the visible properties the image needs:

`event → physical consequence → location and surface → visible behavior`

Show the fluid on her body and surroundings, not its container. Bottles, pumps, tubes, and packaging stay out of the image unless the user asks for them. They add a prop that competes with her and turns the scene into a product shot. Its presence alone tells the story: glossy streaks, drips, a sheen on the skin.

Relevant properties include direction, gravity, accumulation, absorption, translucency, viscosity, and how the scene's light catches it. When every surface is equally wet and glossy, the image turns to noise. Only the places tied to the light source, the story, or the contact deserve emphasis. Keep fluids subordinate to the whole composition unless the user makes them the principal subject.

## 9. Light and framing

Erotic lighting is not a separate genre. Choose light for what it has to do in this scene:

- **Reveal**: make the main body relationship readable
- **Separate**: distinguish overlapping silhouettes
- **Conceal**: let shadow quiet secondary information
- **Direct**: guide the eye from primary to secondary
- **Integrate**: put bodies and environment in the same space
- **Reveal traces**: small highlights make wet, translucent, or textured surfaces legible

Warm side light, silk, and classical props do not make a scene artful by themselves. Each formal choice should have a reason in the story.

**Cropping** is a compositional decision. It can concentrate attention, create intimacy or ambiguity, or imply something off-frame. It is not a way to raise intensity. When the story depends on the environment or on several characters, keep enough space for those relationships to stay readable.

## 10. Keeping the image a composition

At E4 and E5, explicit information can easily become the only readable thing. The *event* usually has more narrative value than the *anatomical evidence of the event*. The viewer should first understand who is interacting, how the bodies relate, what the reaction is, where it happens, and what clue changes the interpretation. Local explicit detail comes after.

When the user deliberately asks for a detail-focused composition, the detail may become primary. Keep enough spatial context that the viewer understands what it belongs to and why it is there.

**When a scene feels flat**, look for a missing relationship rather than adding explicitness: stronger foreground and background separation, clearer body direction, readable action and reaction, a secondary narrative clue, asymmetry, meaningful negative space, a stronger moment, clearer light hierarchy, or a framing element.

**Information budget.** When the prompt gets crowded, protect in this order: primary event → relationship → body interaction → composition → framing → key reaction → explicit information required by the level → lighting → story-bearing environment → materials → decoration. Remove from the bottom. Repeated erotic adjectives and restated intensity carry no visible information, so they go first.

## 11. Erotic-specific check

Alongside the final check in `SKILL.md`:

- The level matches the request and is expressed through visible information, not adjectives.
- Action and reaction are connected, and contact is spatially clear.
- Weight is supported, and surfaces, clothing, and any fluids respond plausibly to contact and gravity.
- Explicit details are physically part of the event. The main event still outweighs incidental detail.
- A same-scene change kept the scene and moved only the explicitness channel.
