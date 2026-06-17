---
name: product-photography-generator
description: Use when generating product photography — for e-commerce, marketing, packaging, advertising. Always produces professional, brand-safe product images with correct lighting, composition, and context.
---

# Product Photography Generator

Product photography has strict rules. Follow them.

## Shot Types
1. **Hero shot**: product centered, dramatic lighting, simple background, premium feel
2. **Catalog shot**: product on white seamless, even soft lighting, true colors
3. **Lifestyle shot**: product in use, environmental context, human element optional
4. **Detail shot**: macro close-up of texture, material, mechanism
5. **Group shot**: multiple SKUs arranged with hierarchy
6. **Flat lay**: top-down on textured surface, styled props

## Lighting Rules
- Catalog: softbox key light + fill, 1:2 ratio, no harsh shadows, white card reflections
- Hero: single hard key + rim light + subtle fill, dramatic but product still readable
- Lifestyle: motivated by the environment (window light, lamp, sun)
- Always preserve true product colors — color accuracy is non-negotiable

## Background Rules
- Catalog: pure white #FFFFFF seamless, soft shadow under product
- Hero: solid color or gradient that complements the product's palette
- Lifestyle: contextual environment that doesn't compete with product
- Never use a background that clashes with the product

## Composition Rules
- Product occupies 60-75% of the frame
- Rule of thirds for hero; centered for catalog
- Negative space around the product for text overlays in marketing
- Camera at product eye-level for hero, slightly above for catalog

## Material Fidelity
- Glossy materials: show controlled reflections, not blown-out highlights
- Matte materials: show subtle texture, no shine
- Transparent materials: show what's behind, with edge highlights to define form
- Metallic materials: show specular highlights that define the form

## Prompt Template
```
Professional product photography of [PRODUCT NAME + DESCRIPTION],
[shot type], on [background], [lighting setup],
[color accuracy: true to life], shot on Phase One IQ4, 80mm macro lens,
f/11, ISO 100, tethered capture, ultra-detailed, 8k, commercial quality
```

## Forbidden Behaviors
- Stylized backgrounds on catalog shots
- Dramatic lighting on catalog shots
- Distorted product proportions
- Color shifts from the true product color
- Visible watermarks or stock-photo artifacts

## Output Format
1. Shot type selected
2. Full prompt
3. The image
4. Color accuracy check (palette matches the product description)

