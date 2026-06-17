---
name: inpainting-outpainting-expert
description: Use when the user wants to modify part of an image (inpaint) or extend an image beyond its original borders (outpaint). Always preserves the unmodified regions at 100% fidelity.
---

# Inpainting & Outpainting Expert

Local edits only. Never run a global img2img pass when only a region needs to change.

## Inpainting Rules
1. Mask ONLY the region to change
2. Set mask blur to 4-8 pixels for soft seams
3. Set inpaint strength to 0.85-1.0 for full replacement, 0.5-0.7 for partial edits
4. Keep the unmasked regions at strength 0 (locked pixels)
5. The prompt should describe the FULL final image, not just the masked region — context matters

## Outpainting Rules
1. Extend the canvas in the requested direction
2. Use the original image as img2img reference at strength 1.0 in the original region
3. The prompt should describe what should appear in the new region, consistent with the original
4. Match lighting, color palette, focal length, style of the original
5. Blend the seam: lightly inpaint a 20-30px band along the original edge

## Common Tasks
- Remove object: mask the object, prompt for the background that should be there
- Replace clothing: mask clothing, prompt for new outfit
- Change expression: mask face, prompt for new expression with face-lock reference
- Extend background: outpaint left/right/up/down with scene-consistent prompt
- Add object: mask empty area, prompt for the new object with appropriate lighting

## Continuity Checklist (After Every Edit)
- [ ] Lighting on the edited region matches the original
- [ ] Color temperature matches
- [ ] Sharpness matches (no over-sharpened edit)
- [ ] No visible seam
- [ ] Shadows and reflections updated if needed

## Forbidden Behaviors
- Running a global img2img pass when only a region changed
- Forgetting to set mask blur (creates hard seams)
- Editing the face without a face-lock reference

## Output Format
1. Mask description (what region was edited)
2. Strength used
3. The edited image
4. Continuity checklist result

