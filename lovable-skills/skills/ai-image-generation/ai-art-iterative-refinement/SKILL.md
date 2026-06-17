---
name: ai-art-iterative-refinement
description: Use when the user wants to refine an AI image over multiple turns — fixing one thing at a time without losing what already works. Always preserves the user-approved elements and only changes what was requested.
---

# AI Art Iterative Refinement

Iteration is the hardest part of AI art. The model has no memory — every change risks losing what already worked.

## Golden Rules
1. **Never regenerate from scratch** once the user is happy with parts of the image
2. **Use inpainting** for localized changes (face, hand, single object)
3. **Use img2img at low strength (0.25-0.40)** for global tweaks (lighting, color grade)
4. **Keep the seed** — same seed + same prompt + small change = minimal drift
5. **Save every approved version** so you can roll back

## Refinement Workflow
When the user asks for a change:
1. Identify the scope of the change: local (one region) or global (whole image)
2. If local → inpaint the region only
3. If global but minor (color, lighting) → img2img at 0.25-0.35
4. If global and major (style change) → full regenerate but keep the seed
5. After the change, verify the user-approved elements are still intact

## Change Tracker
Maintain a running list:
```
VERSION 1: initial generation
  - approved: composition, color palette, environment
  - to fix: face slightly off

VERSION 2: inpainted face
  - approved: composition, color palette, environment, face
  - to fix: hand has 6 fingers

VERSION 3: inpainted hand
  - approved: everything
```

## Common Refinement Tasks
- "Fix the face" → inpaint face region with face-lock reference
- "Make it warmer" → img2img at 0.30 with "warm color grade" added
- "Change the background" → inpaint background, keep subject at strength 1.0
- "More cinematic" → img2img at 0.35 with "cinematic lighting, anamorphic, teal-orange grade"
- "Different pose" → ControlNet OpenPose + img2img at 0.55
- "Same character, new scene" → use saved character reference (cref or IP-Adapter)

## Forbidden Behaviors
- Regenerating from scratch when a local change would do
- Forgetting the seed between iterations
- Not tracking what's been approved vs. still being fixed
- Changing multiple things at once (makes it impossible to debug)

## Output Format
1. What the user requested to change
2. Scope: local / global minor / global major
3. Method: inpaint / img2img / regenerate
4. Strength used
5. Updated change tracker
6. The new image
7. Verification: approved elements preserved?

