# Character Looks

Read this before every prompt except reverse prompting. The rules for when to design a look are in `SKILL.md` ("Designing the girl's look"). This file holds the method for inventing a look and the way to describe any outfit, including one the user specified.

## Contents

1. Inventing a look
2. Describing an outfit

## 1. Inventing a look

There is deliberately no list of looks, hairstyles, or accessories to pick from. A list gets copied, and the same kind of scene would get the same character every time. Invent the look for this scene in four steps.

**1. Who is she?** Write one line, for yourself, about who she is in this scene: what she does, what she cares about, a habit, or where she has just come from. Build it from the scene's details, then give her one trait the scene doesn't predict. The gap between who she is and what she is doing turns a mood into a character. Record the line in the SceneSpec `PRIMARY` field. The prompt carries only its visible results.

**2. Derive the four parts from that line.**

- **Hair.** Decide the silhouette first: length, volume, and how it is worn. Then choose a color against the scene's main colors, so her head stands out where the layout puts the focal point.
- **Eyes.** A color that echoes her hair or an accent in the scene, or one that deliberately contrasts with both.
- **Outfit.** What this person would actually wear in this place at this moment. For erotic scenes, also follow `SKILL.md`.
- **Signature accessory.** One or two things that come from her life and hint at the story outside the frame. An object with a reason to be on her beats pure decoration.

**3. Set the first idea aside.** The first look that comes to mind is the most common one, and it returns for every similar scene. Develop a different one. Within one conversation, don't reuse a hair color or accessory already given to another character.

**4. Check that she reads as one character.** She should look like a named anime character: one clear silhouette and one detail people would remember her by. Every part should trace back to the line from step 1. Replace any part that connects to nothing.

In the prompt, spread the features along the viewer's path as described in `SKILL.md` section 5, rather than pasting them as one block.

## 2. Describing an outfit

Build an outfit description in three passes, from what the eye reads at a distance to what it notices up close. The patterns below show the shape of each pass. Fill them with this character's own pieces.

**Shape.** Start with what the outfit is and the outline it gives her body: `a [garment] that [falls to / fits / swallows] [part of her body]`. If there are layers, say which piece is on the outside, because the outer piece sets the silhouette.

**Surface.** Then give each visible piece its color, fabric, and any pattern or trim: `a [color] [fabric] [garment] with [trim or print]`. Fabric matters more than it seems, because it decides how the piece folds and catches light.

**State.** Finish with how the clothes are worn right now: `[the piece] [pushed / hanging open / slipping / lifted] at [where]`. This is where clothing joins the pose and the story, so attach it to the body part or action involved.

Accessories come after the outfit, each tied to where it sits (see "Give small details a location" in `SKILL.md`).

Say everything about a piece in the one place it first appears, rather than naming it early and returning later to add its color or fabric. Naming a coat early and adding `the coat is wool` near the end splits one piece across the prompt.

When the user has specified an outfit, keep every detail they gave. The three passes only decide the order to write those details in, not what to change.
