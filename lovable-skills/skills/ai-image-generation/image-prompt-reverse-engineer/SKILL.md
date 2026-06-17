---
name: image-prompt-reverse-engineer
description: Use when the user uploads an image and wants to know the prompt that would generate something similar, OR wants to extract style/subject/lighting descriptors from it. Always produces a structured, reusable prompt spec.
---

# Image Prompt Reverse Engineer

Given an image, produce a structured prompt that would reproduce it (or its key characteristics) in any image model.

## Extraction Process
Walk through these dimensions in order:

1. **Subject** — who or what is the focus? people, objects, scenes
2. **Identity** (if people) — age, gender, ethnicity, hair, eyes, build, distinguishing marks
3. **Outfit** — every garment, color, material, accessory
4. **Pose / Action** — what is the subject doing? posture, expression
5. **Environment** — where? interior / exterior, style, era, specific objects
6. **Composition** — rule of thirds? centered? leading lines? framing?
7. **Camera** — angle, distance, focal length implied
8. **Lens** — wide / normal / telephoto / macro; depth of field
9. **Lighting** — key light direction, hardness, color temp, ratio, source
10. **Color palette** — 5 dominant hex codes
11. **Style** — medium (photo / painting / 3D), substyle, art movement references
12. **Mood** — 3 adjectives
13. **Texture / Grain** — film stock, noise, sharpness
14. **Post-processing** — color grade, contrast, saturation level

## Output Format
```
REVERSE-ENGINEERED PROMPT SPEC

Subject: ...
Identity: ...
Outfit: ...
Pose/Action: ...
Environment: ...
Composition: ...
Camera: ...
Lens: ...
Lighting: ...
Color palette: #..., #..., #..., #..., #...
Style: ...
Mood: ...
Texture/Grain: ...
Post-processing: ...

RECONSTRUCTION PROMPT (SD/FLUX):
[single comma-separated prompt using all the above]

RECONSTRUCTION PROMPT (Midjourney v7):
[natural prose + --ar ... --style raw --v 7]

RECONSTRUCTION PROMPT (DALL-E 3):
[conversational full sentences]
```

## Verification
Mentally simulate running the reconstruction prompt. Does it produce something close? If not, adjust the descriptors and try again.

## Forbidden Behaviors
- Vague descriptors ("a nice photo of a person")
- Missing lighting or camera specs
- Not providing all three model-specific variants

