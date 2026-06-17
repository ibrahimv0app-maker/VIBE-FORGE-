---
name: image-upscale-restorer
description: Use when the user wants to upscale, enhance, restore, or denoise an existing image — including old photos, low-res AI outputs, compressed images. Always preserves the original identity while improving fidelity.
---

# Image Upscale & Restore

Upscaling is not "make it bigger". It is "recover detail that should exist".

## Workflow
1. Inspect the input image: is it blurry? compressed? noisy? low-res? scratched? all of the above?
2. Pick the right tool path:
   - Pure upscale (clean image, just bigger) → ESRGAN / Real-ESRGAN
   - Detail recovery (AI art that needs more crispness) → High-res fix + img2img at 0.35 strength
   - Photo restoration (scratches, dust, fading) → GFPGAN / CodeFormer for faces + restore pass
   - Denoise (high-ISO photo) → img2img at 0.25 with denoise strength
   - Face recovery (blurry face) → GFPGAN 1.4 with strength 0.5
3. Always run face recovery separately from body upscaling — face artifacts are catastrophic
4. Verify the upscaled output preserves:
   - [ ] Subject identity (face matches)
   - [ ] Original color palette
   - [ ] Original composition
   - [ ] No new artifacts (especially around hands, eyes, text)

## Upscale Factors
- 2x: safe for any image
- 4x: requires clean source; AI art preferred
- 8x+: only for very clean sources; expect some softness

## Restoration-Specific Rules
- For vintage photos with damage: scan at the highest DPI available, restore faces with GFPGAN, then inpaint damaged regions manually
- For old film: keep the grain character — do not "clean" film grain away, that destroys the film look
- For compressed JPEGs: run a deblock pass before upscaling

## Forbidden Behaviors
- Upscaling without face recovery when faces are present
- Over-sharpening (creates halos)
- Removing film grain from film photos
- Changing color palette during restoration

## Output Format
1. Diagnosis of the input image
2. Tool path selected
3. Upscale factor
4. The upscaled image
5. Side-by-side comparison note

