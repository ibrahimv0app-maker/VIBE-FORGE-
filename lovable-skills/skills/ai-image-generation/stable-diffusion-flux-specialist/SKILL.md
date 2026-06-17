---
name: stable-diffusion-flux-specialist
description: Use when the user is generating images with Stable Diffusion (SDXL, SD3) or FLUX.1. Always uses correct syntax, LoRA loading, sampler/step choices, and ControlNet/IP-Adapter when appropriate.
---

# Stable Diffusion & FLUX Specialist

SD/FLUX is the most flexible stack — but only if you use every lever correctly.

## Prompt Style
SD/FLUX accepts comma-separated tag-style prompts. Natural prose also works on FLUX.1.

## Standard Parameters
- **Sampler**: DPM++ 2M Karras (most reliable), Euler a (fast), DDIM (precise)
- **Steps**: 25-35 for SDXL, 25-40 for FLUX.1, 40-50 for high-detail
- **CFG**: 6-8 typical, 9-12 for stronger prompt adherence, 4-5 with FLUX.1 dev
- **Resolution**: 1024×1024 native for SDXL/FLUX, 512×512 for SD1.5
- **Hi-res fix**: required when going above native resolution, strength 0.4-0.6

## Negative Prompt (SDXL)
```
lowres, bad anatomy, bad hands, extra fingers, missing fingers,
extra limbs, mutated, deformed, blurry, watermark, signature,
text, jpeg artifacts, ugly, duplicate, morbid, mutilated,
out of frame, extra arms, extra legs, fused fingers, too many fingers
```

## LoRA Loading
- `<lora:lora_name:weight>` — 0.6-1.0 typical, 0.3-0.5 for subtle
- Multiple LoRAs stack: `<lora:style:0.7> <lora:character:0.9>`
- Always note which LoRAs are active in the output

## ControlNet
- **Canny**: edge detection, locks composition
- **Depth**: depth map, locks spatial layout
- **OpenPose**: body pose skeleton
- **Tile**: locks overall structure while allowing style changes
- **IP-Adapter**: image prompt (use for style or identity transfer)
- **Reference-only**: feed a reference image without ControlNet model

## IP-Adapter (Reference Image)
- `IP-Adapter weight 0.6-0.8` for identity
- `IP-Adapter Plus` for stronger structural fidelity
- `IP-Adapter FaceID` for face locking
- Combine with `--weight 0.9` on the FaceID model for tight face match

## FLUX.1 Specifics
- FLUX.1 [pro]: best quality, API-only
- FLUX.1 [dev]: open weights, great quality, lower CFG (3.5-4.5)
- FLUX.1 [schnell]: 1-4 steps, fast but lower quality
- FLUX understands natural language well — full sentences preferred
- LoRAs for FLUX use different format (.safetensors specific to FLUX)

## Inpainting
- Use dedicated inpainting model (SDXL inpaint) or Inpaint Anything
- Mask blur 4-8px
- Inpaint strength 0.85-1.0 for full replacement
- Use "Only masked" mode for speed

## Upscaling
- Latent upscale + Hi-res fix: standard
- Ultimate SD Upscale script: tile-based, best quality
- ESRGAN / Real-ESRGAN: post-process pass

## Forbidden Behaviors
- Skipping the negative prompt on SDXL
- Using CFG above 12 (causes artifacts)
- Stacking more than 4 LoRAs (causes coherence collapse)
- Forgetting Hi-res fix at 2048px+ (causes duplication)

## Output Format
1. Full prompt (positive)
2. Full negative prompt
3. Sampler, steps, CFG, resolution
4. LoRAs / ControlNets / IP-Adapters active
5. The image

