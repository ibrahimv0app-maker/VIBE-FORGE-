---
name: scene-consistency-locker
description: Use when generating multiple scenes that must share the same location — same room, same city street, same forest — so the environment looks identical across shots (film storyboards, graphic novels, game level concepts).
---

# Scene Consistency Locker

Same skill pattern as character consistency, but for PLACES. A coffee shop in shot 1 must be the same coffee shop in shot 12 — same counter, same windows, same wall art, same lighting fixtures.

## Step 1 — Establish the Master Establishing Shot
Before any close-up or detail shot, generate one wide establishing shot of the location. This becomes the canonical scene reference.

## Step 2 — Build the Scene DNA
```
SCENE DNA: [LOCATION NAME]
- Architecture: style, era, materials
- Walls: color (hex), texture, trim
- Floor: material, color, pattern
- Ceiling: height, color, fixtures
- Windows: count, shape, position, treatment
- Doors: count, style, color, hardware
- Key furniture: each piece with color and position
- Lighting fixtures: type, count, position
- Decorative items: wall art, plants, rugs (with positions)
- Time of day: lighting condition
- Weather (if exterior): sky, precipitation
- Distinguishing features: anything unique
```

## Step 3 — Lock the Scene
For every new shot of this location:
- Use the establishing shot as reference image (strength 0.55–0.70)
- Reuse the Scene DNA verbatim in the prompt
- Only change: camera angle, focal length, subject action in the scene

## Step 4 — Camera Coverage Map
Maintain a mental map of the room's layout. Every new shot must be physically possible FROM that layout. If the user asks for "shot from the back corner", confirm that corner exists in the Scene DNA.

## Step 5 — Continuity Verification
For every new shot, verify:
- [ ] Wall color matches
- [ ] Floor matches
- [ ] Key furniture is present and correctly placed
- [ ] Windows / doors are in the right relative position
- [ ] Lighting direction is consistent with the established time of day
- [ ] Decorative items (wall art, plants) are present and consistent

## Forbidden Behaviors
- Generating a new shot without consulting the establishing shot
- Changing wall colors or furniture between shots
- Inventing new windows / doors that contradict the Scene DNA

## Output Format
1. Scene DNA (when first establishing)
2. Camera coverage map (which shots have been generated from which angles)
3. For each new shot: the prompt + continuity checklist result

