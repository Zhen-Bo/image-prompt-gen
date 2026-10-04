# Composition and Narrative

This pass fills the `PRIMARY`, `SECONDARY`, `RELATIONSHIP`, `MOMENT`, `COMPOSITION`, `LIGHTING`, and `EVIDENCE` fields of the SceneSpec defined in `SKILL.md`. It turns narrative meaning into visible organization. Language, subject, and style rules live in `SKILL.md` and are not repeated here.

## Contents

1. Reading order: 1 / 3 / 10 seconds
2. Layout: placement, open space, and the eye's path
3. Primary and secondary themes
4. Choosing the moment
5. Characters and bodies
6. Depth, occlusion, and framing
7. Hierarchy controls: scale, light, color, shape, negative space
8. Environment as evidence
9. Compressing stories and emotions
10. Repairing a weak composition

## 1. Reading order: 1 / 3 / 10 seconds

A brief is not an object list. It is an order of discovery: what the viewer understands first, what next, and what changes the meaning after a closer look.

- **1 second: what is happening?** Carried by silhouette, scale, contrast, placement, body gesture, large directional shapes, and dominant light. The basic event must never depend on a small background prop.
- **3 seconds: why does it matter?** Carried by gaze, touch, action and reaction, expression, body orientation, a secondary light, a meaningful prop, or another character.
- **10 seconds: what happened before, or what comes next?** Carried by aftermath traces, reflections, shadows, displaced objects, clothing state, a partly hidden figure, open or closed boundaries, and repeated motifs.

Use all three layers only when they strengthen the requested story. A simple scene can stop at the first. Section 2 decides where each layer sits in the frame.

## 2. Layout: placement, open space, and the eye's path

The reading order says what the viewer understands first. The layout says where that thing sits in the frame and how the eye travels to it. Image models default to a centered subject that fills the frame, so a prompt that never states a layout gets that default. Every prompt decides three things and writes them in visible terms.

**Placement and share.** Where the focal point sits, usually her face or the point of contact, and how much of the frame she takes up. Name a region of the frame rather than a rule: `her face sits in the upper left third`, `she takes up only the lower right quarter of the frame`, `her standing figure sits near the right edge, from head to knees`. Off-center is the default. Center her only when the scene calls for it: a frontal confrontation, a ceremony, strict symmetry, or a direct address to the viewer.

**Open space.** The area where nothing competes with her. Name what fills it and which side it is on: `the bare pale wall fills the right two-thirds of the frame`, `open evening sky takes up the upper half`. Put it on the side she looks or moves toward, so her gaze has room to travel. Open space is a wall, sky, floor, water, a dark room, or soft light, never an unfinished area. Keep props, highlights, and strong color out of it, because each one spends attention the focal point needs.

**Path.** One or two devices that carry the eye to her, on to the secondary information, and back. Prefer things the scene already contains:

- **A line in the environment**: a table edge, a railing, a window frame, a corridor, the length of a bed or sofa, a road. Say where it starts and where it points: `the edge of the long table runs from the lower right corner toward her hands`.
- **Light**: a band of light, a lit patch, or a gradient that ends on her: `window light falls in a long band across the floor and ends at her feet`.
- **Her gaze or reach**: what she looks at or reaches toward becomes the next stop, so give it a place in the frame. When it is off-frame, leave open space on that side.
- **Her body line**: the diagonal or curve her body makes.

Point every device the same way. A line that leads out of the frame before it reaches her lets the eye leave the image, and a gaze that runs against the main line splits the focus.

**Choosing a layout.** Pick the pattern that carries the scene's feeling, then fit the camera to it (`camera.md` section 1). Vary it across versions.

| Layout (中文) | Use it for | Write it as |
|---|---|---|
| Off-center with open space (偏心留白) | The everyday default: waiting, thinking, calm, looking at something | `she sits in the left third of the frame, her face near the upper left, while the bare wall fills the right two-thirds in the direction she looks` |
| Centered and symmetrical (置中對稱) | Confrontation, ceremony, authority, direct gaze at the viewer | `she sits exactly in the center, the doorway framing her evenly on both sides` |
| Diagonal (對角線) | Movement, tension, imbalance, a sprawling body | `her body runs diagonally from the lower left corner toward the upper right` |
| Curve (S 形) | Ease, grace, a winding path | `her body curves in a loose S from her tilted head through her hip to her crossed ankles` |
| Horizontal bands (水平分層) | Rest, stillness, calm | `she sits along the bottom third, the shoreline, the sea, and the pale sky stacked above her in level bands` |
| Dark foreground shape (前景暗塊) | Depth, intimacy, the sense of looking in | `the dark back of an armchair fills the lower left foreground, and she sits beyond it in the lit middle ground` |
| Small figure in a large space (小人物大空間) | Isolation, scale, being swallowed by the place | `she is small in the lower right, the high empty room rising around her` |
| Frame within a frame (框中框) | Focus, privacy, confinement, peeking | Written as in `camera.md` section 7, plus where the inner frame sits |
| Deliberate crop (刻意裁切) | Closeness, the sense that the scene continues past the edges | Written as in `camera.md` section 7, for example the right edge cutting through her shoulder |

**Canvas shape.** The aspect ratio is set in the user's workflow, not in the prompt. When the user mentions it, fit the layout to it: a wide canvas suits open space beside her, and a tall canvas suits open space above her or a standing full figure.

## 3. Primary and secondary themes

The primary theme says what the image is about. The secondary theme should make the viewer realize it is about more than that. So the secondary element works as a modifier of the primary event, not as a second poster sharing the frame:

`primary event + secondary evidence = richer interpretation`

Ways to connect them:

| Integration | Primary | Secondary |
|---|---|---|
| Cause and consequence | A character reacting | What caused the reaction |
| Action and aftermath | The present action | Evidence of what just preceded it |
| Foreground and revelation | Foreground event | Background information that changes its meaning |
| Person and environment | Character | Setting that shows social, emotional, or physical context |
| Present and absent | Visible character | Evidence of someone not visible |
| Physical or symbolic echo | Gesture or object | A shape, reflection, shadow, or prop that repeats its meaning |

A secondary element can be spatially small and semantically large. A packed suitcase deep in the room can turn an intimate scene into a farewell without competing for first attention.

**Integration test.** For each important secondary element, ask what it tells the viewer about the primary event: why the character reacts, what just happened, who controls the situation, what may happen next, where or when this is. If the only answer is "the user mentioned it", keep it but find a stronger spatial or narrative link. For example, put it in the character's line of sight, in her hand, or in the doorway she is turning toward.

**One object serving both themes.** The strongest link is often a single object or space that belongs to both themes at once. A window is both the boundary of a private room and the view of the outside world waiting for one of the characters. An unfinished cup is both a shared moment and a sign that it was cut short. A uniform on the chair is both an ordinary piece of clothing and the duty that will take someone away. To find one, list the primary theme's actions, the traces left behind, the markers of time, and the objects. Then look for the item that can also carry the secondary theme. One such object usually does more than several separate props, so it earns a clear spot near the primary subject or in its line of sight.

**Keep one dominant.** Two themes that each take half the visual power fight each other. Give most of the contrast, size, sharpness, and light to the primary, a clear second share to the secondary, and let fine details stay quiet.

## 4. Choosing the moment

A story holds more than one image can show, so pick the instant that communicates the request with the least explanatory text. The climax is not always the most story-rich moment. Leaving the viewer something to infer often reads better.

| Moment | What it shows | Useful tools |
|---|---|---|
| Anticipation | The event has not happened yet | Gaze toward something off-frame, a reaching hand, an open doorway, an object prepared for use, tense posture |
| Action | The event is occurring | Contact, weight transfer, directional movement, visible reaction, displaced objects |
| Interruption | The event has been disrupted | A sudden gaze shift, a frozen gesture, a dropped object, an opening door |
| Reaction | The effect on a character matters more than the mechanics | Expression, hands, posture, distance |
| Aftermath | The event has just ended | Altered clothing, disturbed surfaces, physical traces, exhausted or relaxed posture, changed light |

A strong single image implies a before and an after: `visible present + trace of the past + hint of the future`. For example, a girl stands at an open door (present), her suitcase is already packed (past), and her hand stays on the handle (future). The prompt never needs to explain the chronology. The evidence lets the viewer infer it.

## 5. Characters and bodies

### Visual verbs

Relationships expressed as verbs carry subject, direction, and flow at once. `girl, chair, rope, window` is an inventory. `a girl leans back against the chair while the rope pulls diagonally toward the window` is a composition. Useful verbs: lean, reach, pull, press, turn, recoil, support, surround, cross, overlap, frame, divide, conceal, reveal, interrupt, follow, anchor. Choose them from the requested event, and keep static scenes static.

### Interaction as one physical system

Two characters should read as one event, not two portraits placed side by side. Think in terms of:

- `A acts → B responds`
- `A's weight or position → changes B's posture`
- `A and B → form one combined silhouette`

For contact, name the relationship (support, resistance, embrace, guidance, leaning into, pulling away) rather than listing body parts. The viewer should understand who interacts with whom without any explanation.

### Weight before detail

Bodies should look affected by gravity and each other. Settle large relationships first: torso direction, what supports the weight, the main contact points. Then add head direction, gaze, and hands. Visible consequences such as compressed fabric, a shifted center of gravity, or pressure against a surface make the interaction believable. Include them when they clarify the event.

### Gesture and gaze hierarchy

Not every limb needs an instruction. Find the gesture carrying the most narrative weight and describe that. Order of importance: primary body action → supporting hand or arm → head direction → gaze and expression → minor gestures.

Gaze is a connector. Subject to subject builds a relationship. Subject to object makes the object important. Subject to off-frame suggests unseen information. Subject to viewer changes the viewer's role. An averted gaze can show distance, hesitation, or discomfort. Assign gaze only where it serves the story. Whatever gaze you assign also moves the viewer's eye, so give it room or a target placed in the frame (section 2).

## 6. Depth, occlusion, and framing

**Depth distributes information.** The immediate event sits in the foreground or the middle ground, relationship or context around it, and revelation or consequence deeper. Background information that matters should stay legible but lower in contrast than the primary subject. The primary subject doesn't have to be the nearest, largest shape: placing her in the lit middle ground behind a darker foreground shape, such as a chair back, a curtain edge, or the corner of a bed, adds depth and frames her.

**Occlusion creates discovery.** A figure partly behind a doorway, cut by the frame, seen in a mirror, or hidden behind furniture becomes something to find rather than something that competes. It also builds intimacy, secrecy, and depth. Keep enough visible that the hidden part can be inferred.

**The frame is a tool.** A figure pressed against the edge feels confined, while one surrounded by empty space feels isolated or expectant. A doorway can act as a second frame around a background figure. Where the frame edge cuts her also matters: an edge through her shoulder or thigh brings the viewer close and implies the scene continues past the frame. She doesn't need to fit entirely inside the frame unless the event depends on her whole body.

**Reflection and shadow** can bring in secondary information (another person, an off-frame event, a repeated pose) without adding a competing focal point. Use them when they are spatially plausible and carry meaning.

## 7. Hierarchy controls

The primary subject needs the clearest combined hierarchy, not maximum intensity on every axis. Balance these controls together:

- **Scale.** A secondary subject can stay subordinate through lower contrast, greater depth, softer light, peripheral placement, less saturation, or partial occlusion, not only through small size. A small object becomes important through isolation, contrast, someone's gaze, or a local highlight.
- **Light.** Decide what must be understood immediately, then let the main light reveal it. A secondary light separates or reveals supporting information, the background stays restrained, and one local highlight can pick out a single story-bearing object. One coherent light logic beats several atmospheric light adjectives.
- **Color.** Use it when it does a job: identifying a character, linking two subjects, separating foreground from background, isolating an object, or marking temperature or physical state.
- **Shape and flow.** Large shapes organize the image before details are noticed: diagonal, triangle, arc, vertical division, enclosure, converging lines. Use them when the subjects support them naturally, for example `their bodies form one diagonal from the lower left toward the window`.
- **Negative space.** Empty space communicates isolation, anticipation, vulnerability, absence, ease, or room for implied movement. A subject looking into empty space suggests expectation. Section 2 covers where to put it.

**Spectacle check.** A dramatic secondary element (fire, neon, a storm, a vivid fluid) can steal the image. Compare size, contrast, sharpness, placement, light, color, and semantic intensity. If the secondary element wins most of them, lower some.

## 8. Environment as evidence

The environment answers questions about the event. It is not a catalogue. Choose details by what they reveal:

- **Previous action**: displaced furniture, disturbed bedding, a wet floor, an unfinished drink, a discarded object
- **Another person**: a second cup, a coat, shoes, a recently moved chair, an open door
- **Time**: light direction, cooling food, candle length, condensation, lamps against darkness, changing weather
- **Intention**: a packed bag, a prepared tool, a waiting vehicle, a half-finished task

Props become meaningful through relationships. `the girl's hand rests beside a half-finished cup` implies waiting. `an open suitcase sits in the darker background behind her` implies departure. Describe the relationship that makes the object useful.

**Physical traces** (wetness, marks, fluids, footprints) should belong to the event: consider their source, the surface they touch, gravity, direction, absorption, and how the light catches them. Give them descriptive weight in proportion to their narrative importance.

## 9. Compressing stories and emotions

**Stories.** A prompt cannot hold a whole story. Compress prose into `event + relationship + evidence`. A long story might reduce to: `A girl pauses halfway through packing, looking toward the open bedroom door while another person's coat remains draped over the chair behind her.` That single sentence holds the protagonist, an interrupted action, gaze, an absent second person, the setting, and narrative uncertainty.

**Many required elements.** Find the element that defines the image, attach the other requirements to it through relationships, group compatible information, spread supporting information across depth, and leave fine details for the last reading layer. Give each requirement its own region only when the user asks for a collage, lineup, or multi-panel layout.

**Emotions** become visible consequences. These are options to adapt, not formulas:

| Emotion | Visible evidence |
|---|---|
| Unease | Guarded posture, uneven distance, attention toward an exit, a tight grip, asymmetric composition |
| Intimacy | Reduced distance, shared gaze, overlapping silhouettes, relaxed contact, shared light |
| Isolation | Large negative space, distant secondary figures, separate pools of light, closed posture |
| Urgency | Forward weight, displaced objects, directional movement, a reaction from another figure |
| Calm | Stable balance, relaxed hands, horizontal organization, breathing room, soft coherent light |

## 10. Repairing a weak composition

Identify the failure category, then apply the matching fix:

| Symptom | Fix |
|---|---|
| Everything equally important | Rebuild the hierarchy as dominant, supporting, discoverable |
| Subject centered and filling the frame | Rebuild the layout (section 2): place her off-center, name the open area, and let the frame cut what the event doesn't need |
| The eye has no route | Add one path device that ends on her: an environment line, a band of light, or a gaze target placed in the frame |
| Characters feel disconnected | Add contact, gaze, a shared object, action and reaction, or an overlapping silhouette |
| Background feels decorative | Replace decoration with evidence tied to the event |
| Secondary subject steals attention | Lower its contrast, size, light, saturation, or centrality, or move it deeper |
| Scene has no story | Add one temporal clue: anticipation, interruption, consequence, aftermath, or evidence of absence |
| Scene feels staged | Add physical consequences: weight, fabric response, contact with surfaces, coherent gaze |
| Prompt feels crowded | Keep only what affects the event, hierarchy, relationships, setting, required identity, or interpretation |
