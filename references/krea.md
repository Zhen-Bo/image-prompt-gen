# Krea 2 Precise Adapter

Compiles a finished SceneSpec into a Krea 2 prompt. The adapter changes wording and density only. Composition and explicitness are already decided upstream. The shared compilation rules (prose, ordering, hierarchy in wording, compression) are in `SKILL.md` section 5.

## Contents

1. How Krea 2 reads the prompt
2. Information strategy and length
3. Prompt shape
4. Density by dimension
5. Examples
6. Compression pass

## 1. How Krea 2 reads the prompt

The user runs Krea 2 as a precise local model: the prompt is taken close to literally and no expander invents art direction. So the user supplies the important decisions, and the prompt should hold the highest-value visible information in compact form. Anything left unsaid stays open to the model's defaults, which is fine for dimensions the user does not care about.

## 2. Information strategy and length

A Krea prompt normally establishes, in this order of importance:

1. primary subject
2. primary action or state
3. the key interaction
4. composition
5. framing or viewpoint, when it matters
6. lighting
7. environment
8. story-bearing evidence, when needed

Leave a dimension out when the user did not specify it and the image stays coherent without it.

**Length follows the scene.** There is no word limit. In precise mode nothing expands the prompt, and Krea's own research found that richer descriptions produce better generations. So every visible decision the scene depends on belongs in the prompt: pose, contact, placement, light, and evidence. A simple scene may need two sentences, while a layered multi-character scene may need a full paragraph. Compression removes repetition and decoration. It never removes information the image needs.

Put the most important relationship early (`main event → interaction → composition → secondary evidence → environment`) so environmental description never delays the primary event.

## 3. Prompt shape

A conceptual form, not a template:

`[Primary subject and action], [interaction or secondary subject]. [Composition and framing]. [Lighting and environment]. [Key narrative or physical evidence].`

The result reads as one paragraph of natural prose.

## 4. Density by dimension

- **Camera.** Always include the camera from `camera.md`, written as a term plus its visible boundary: `cowboy shot, framed from mid-thigh up, low camera looking slightly upward`. Add spatial detail when a relationship depends on it: `a wide view keeps both figures and the doorway visible, with the girl dominant in the foreground`.
- **Lighting.** One coherent logic that supports hierarchy: `Soft side light from the window catches her face and hands while the room stays dimmer.`
- **Environment.** Keep objects by narrative value. `an open suitcase beside the doorway` earns its place when it implies departure. A decorative vase with no role does not.
- **Materials.** Include behavior only when it affects contact, light, or consequence: `The wrinkled sheet compresses beneath her supporting hand` when the hand's weight matters.
- **Multiple characters.** Describe the group as one composition through relative position, body direction, contact, overlap, support, and silhouette. Describe each character head to toe only when identity continuity requires it.
- **Erotic scenes.** Same grammar: `event → body relationship → composition → reaction → relevant physical evidence → environment and light`. Higher explicitness does not mean more adjectives. Protect the whole body relationship from being displaced by local detail.

## 5. Examples

**Simple scene.** Input: `girl beside an open window, looking at the rainy street`

A girl sits sideways beside an open window with one knee drawn up, looking down toward the rain-covered street, seen in an eye-level side view framed from the knees up, soft window light outlining her face and hands against the dim room.

**Narrative scene.** SceneSpec: girl on the bed edge (primary), turning toward the doorway, open suitcase and coat on the floor (evidence), side window light.

A girl sits on the edge of an unmade bed, turning toward the half-open door while one hand grips the wrinkled sheet. A wide shot at eye level shows her full body dominating the foreground, while an open suitcase and a coat on the floor remain quieter details deeper in the room. Soft side light catches her face and hands while the doorway falls into shadow.

**Multiple characters.**

A girl leans backward against the edge of a table as the second figure moves close from her left, their bodies forming one diagonal shape across the foreground in a two-shot framed from mid-thigh up. One hand braces against the tabletop while her head turns toward the other figure. A narrow side light separates their overlapping silhouettes from the darker room.

## 6. Compression pass

Before returning, ask of each phrase:

- Can it go without losing a requested property, relationship, or story information? Remove it.
- Does another phrase already say the same thing? Keep the clearer one.
- Did a secondary detail get as many words as the primary event? Restore the hierarchy.
- Would the model have to guess something the scene depends on, such as where a hand rests, what the light reveals, or where the second figure stands? Add it.

The finished Krea prompt should be fully specified where it matters and free of filler.
