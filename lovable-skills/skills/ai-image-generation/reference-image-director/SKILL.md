---
name: reference-image-director
description: Use whenever the user uploads or references an existing image and wants new images that must respect that reference — composition, lighting, color palette, subject, style, or all of the above. Always honors the reference image as the highest-priority input.
---

# Reference Image Director

You treat the user's reference image as a NON-NEGOTIABLE creative brief. Your job is to extract every salient signal from that reference and reproduce or extend it in the new generation.

## Decision Tree — What to Lock from the Reference
Walk this tree BEFORE writing any prompt.

| User intent | Lock from reference | Vary |
|-------------|----------------------|------|
| "Same vibe, new subject" | Color palette, lighting, composition, lens, mood | Subject |
| "Same subject, new scene" | Subject identity, outfit, hair | Scene, lighting |
| "Same style, different content" | Style descriptor, post-processing, grain, color grade | Subject, scene |
| "Same composition, different theme" | Composition, camera angle, framing | Subject, palette |
| "Extend / outpaint" | Everything inside the original frame | New regions only |
| "Variation / remix" | Subject identity + core palette | Pose, scene, secondary details |

## Reference Extraction Protocol
Before generating, write a structured "Reference Spec" with these blocks:
```
REFERENCE SPEC
- Subject: ...
- Composition: rule-of-thirds / centered / leading-lines / ...
- Camera: focal length, angle, distance
- Lighting: key light direction, hardness, color temp, ratio
- Color palette: 5 dominant hex codes
- Style: photographic / painterly / 3D / illustration; substyle
- Mood: 3 adjectives
- Texture / grain: film stock, noise level, sharpness
- Negative cues: things explicitly NOT in the reference
```

## Reference-Locked Prompt Template
```
[Subject per intent], [composition], [camera], [lighting],
color palette dominated by [hex codes],
[style descriptor], [mood adjectives],
[texture / grain], reference-image weight: 0.65,
composition-lock: 0.55
```
Always set reference-image weight ≥ 0.55. If the user says "loosely inspired by", you may lower to 0.45 — but never below.

## Outpainting / Inpainting Rules
- Outpaint: extend the canvas, keep all original pixels at strength 1.0.
- Inpaint: mask only the region to change, keep everything else at strength 1.0.
- Never run a global img2img pass when only a region needs to change — that destroys locked pixels.

## Multi-Reference Fusion
When the user supplies 2+ references:
- Subject reference → identity lock (weight 0.7)
- Style reference → style lock (weight 0.5)
- Composition reference → layout lock (weight 0.4)
- Never blend weights 50/50 — always pick a primary reference per dimension.

## Forbidden Behaviors
- Ignoring the uploaded reference and free-prompting
- Lowering reference weight below 0.45 without explicit user permission
- Inventing a color palette that contradicts the reference
- Changing camera angle when the user said "same composition"

## Output Format
1. Show the Reference Spec you extracted
2. Show the prompt you used
3. Show the reference weights per dimension
4. Show the image
5. One-line diff: "What I locked from the reference vs. what I changed"

