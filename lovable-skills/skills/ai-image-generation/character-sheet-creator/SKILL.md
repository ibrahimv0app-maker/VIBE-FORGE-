---
name: character-sheet-creator
description: Use when the user needs a character sheet / turnaround / model sheet — front, side, back, three-quarter views — to lock a character's identity before using them in scenes. Always produces a multi-view reference that downstream generations can use.
---

# Character Sheet Creator

A character sheet is the single source of truth for a character's visual identity. Generate it ONCE, then reuse it forever.

## Sheet Layout
Produce a single image with a clean neutral background containing:
- Front view (centered, full body, neutral pose)
- Three-quarter front view (slight turn)
- Side profile view (90°)
- Three-quarter back view
- Back view
- Close-up face front
- Close-up face profile
- Optional: expression sheet (neutral, smile, anger, surprise, sad)

## Prompt Template
```
character sheet of [CHARACTER NAME], [full identity description],
multiple views: front, 3/4 front, side profile, 3/4 back, back,
plus facial close-ups front and profile,
neutral gray background, flat studio lighting, full body,
T-pose / A-pose for clarity, no shadows on background,
reference illustration style, ultra-detailed, 8k
```

## Identity Block (frozen)
The identity block in the sheet prompt is the CANONICAL identity. Save it. Every downstream generation of this character must reuse it verbatim.

## Technical Locks
- Background: pure neutral gray (#9B9B9B) so it doubles as a chroma reference
- Lighting: flat, even, no dramatic shadows (shadows hide features)
- Pose: A-pose preferred (arms slightly away from body) — T-pose acceptable
- Crop: full body, head to toe, with margin
- Resolution: highest available, at least 1024×1024 per view

## Post-Generation
- Verify all views show the same identity (face, hair, outfit)
- Save the sheet as the canonical reference
- When the user later says "now put [character] in [scene]", invoke the ultra-consistent-character-generator skill and pass this sheet as the reference

## Output Format
1. The character sheet image
2. The frozen identity block (plain text, copy-pasteable)
3. Recommended reference weights for downstream use

