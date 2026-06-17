---
name: style-transfer-master
description: Use when the user wants to apply the visual style of one image to the content of another, or to convert existing art into a target style (e.g., photo → oil painting, sketch → 3D render). Always preserves content fidelity while transforming style.
---

# Style Transfer Master

Style transfer has two inputs: a CONTENT reference and a STYLE reference. Treat them as orthogonal.

## Inputs
- Content image: defines what the picture IS (subject, composition, identity)
- Style image: defines how the picture LOOKS (brushwork, palette, texture, grain)

## Weights
- Content weight: 0.65–0.80 (high = preserve subject, low = let style warp subject)
- Style weight: 0.50–0.75 (high = strong style, low = subtle style)
- Identity weight (if a person is in the content): 0.80+ to keep the face recognizable

## Workflow
1. Confirm which image is content and which is style
2. Extract style descriptors from the style image: medium, brushwork, palette, grain, lighting style
3. Extract content descriptors from the content image: subject, pose, composition, identity
4. Compose a prompt that describes the CONTENT in the STYLE
5. Run with content image as img2img reference (strength 0.6) and style image as style reference
6. Verify the content subject is still recognizable; if not, raise content weight and regenerate

## Edge Cases
- Photoreal face in painterly style: keep identity weight at 0.9, style weight at 0.55 — face stays sharp, surroundings go painterly
- Architecture content with abstract style: lower content weight to 0.55 — let the abstraction reshape forms
- Photo to anime: explicitly request anime face proportions; pure transfer often produces "uncanny" faces

## Forbidden Behaviors
- Blending content and style weights at 50/50
- Forgetting to set identity weight when a person is in the content
- Letting the style image's SUBJECT bleed into the output

## Output Format
1. Style descriptors extracted
2. Content descriptors extracted
3. Weights used
4. The image
5. One-line note on content fidelity check

