---
name: style-preset-library
description: Use when the user asks for a specific visual style — photoreal, cinematic, anime, oil painting, watercolor, 3D render, low-poly, pixel art, vaporwave, cyberpunk, art-deco, etc. Always applies the complete frozen style preset for that aesthetic.
---

# Style Preset Library

A library of frozen style presets. When the user names a style, apply the FULL preset — do not improvise.

## How to Use
1. Identify the requested style from the user's prompt
2. Look up the matching preset below
3. Append the preset's prompt block to the user's content prompt
4. Apply the recommended negative prompt and CFG / steps

## Presets

### photoreal-cinematic
Positive: `cinematic photograph, shot on ARRI Alexa, 35mm lens, anamorphic, shallow depth of field, natural color grade, film grain, atmospheric, golden hour rim light, ultra-detailed, 8k`
Negative: `cartoon, anime, illustration, painting, 3d render, plastic skin, oversaturated, hdr`
CFG: 7, Steps: 40, Sampler: DPM++ 2M Karras

### anime-modern
Positive: `modern anime style, Kyoto Animation, sharp clean lineart, vibrant cel shading, detailed eyes, soft gradient hair highlights, atmospheric background, bokeh, ultra-detailed`
Negative: `photoreal, 3d render, western cartoon, muddy colors, blurry`
CFG: 7, Steps: 30

### oil-painting-classical
Positive: `classical oil painting, Rembrandt lighting, rich impasto brushwork, deep chiaroscuro, warm earth palette, canvas texture, museum quality, old master`
Negative: `photograph, digital, anime, flat colors, sharp edges`
CFG: 9, Steps: 50

### watercolor-traditional
Positive: `traditional watercolor painting, wet-on-wet, soft pigment bleed, paper texture visible, limited palette, loose brushwork, light washes, atmospheric`
Negative: `digital, photoreal, sharp lines, opaque, poster paint`
CFG: 8, Steps: 35

### 3d-render-pbr
Positive: `3D render, PBR materials, physically based, Octane render, soft global illumination, ray-traced reflections, subsurface scattering, ultra-detailed, 8k`
Negative: `painting, sketch, 2d, flat, anime`
CFG: 7, Steps: 40

### low-poly-stylized
Positive: `low-poly 3d, flat shaded, limited color palette, geometric facets, stylized, isometric, clean, minimalist`
Negative: `photoreal, high-poly, detailed texture, realistic`
CFG: 7, Steps: 25

### pixel-art-16bit
Positive: `16-bit pixel art, SNES era, limited palette, dithering, clean pixels, sprite sheet aesthetic, retro game`
Negative: `high resolution, photoreal, anti-aliased, smooth gradients`
CFG: 7, Steps: 20

### cyberpunk-neon
Positive: `cyberpunk, neon-soaked, rain-slicked streets, holographic signage, blade-runner aesthetic, teal and magenta palette, volumetric fog, anamorphic flares`
Negative: `daytime, rural, pastel, soft, vintage`
CFG: 8, Steps: 40

### vaporwave-aesthetic
Positive: `vaporwave aesthetic, pink and cyan gradient, retro 80s, VHS scan lines, palm trees, Greek statues, grid floor, chrome`
Negative: `modern, photoreal, muted colors`
CFG: 8, Steps: 35

### art-deco-luxury
Positive: `art deco, 1920s, geometric gold and black, sunburst motifs, symmetrical, luxurious, The Great Gatsby, foil stamping`
Negative: `modern, minimal, organic shapes, pastel`
CFG: 8, Steps: 40

### studio-ghibli
Positive: `Studio Ghibli style, hand-painted background, soft watercolor washes, expressive characters, Hayao Miyazaki, warm natural light, whimsical`
Negative: `dark, gritty, photoreal, 3d, cyberpunk`
CFG: 7, Steps: 35

### isometric-illustration
Positive: `isometric illustration, flat design, soft shadows, limited palette, vector style, infographic aesthetic, clean`
Negative: `perspective, photoreal, painterly`
CFG: 7, Steps: 30

### dark-fantasy
Positive: `dark fantasy, grimdark, Frank Frazetta, moody chiaroscuro, desaturated palette, dramatic rim light, atmospheric mist, painterly`
Negative: `bright, cheerful, anime, flat colors`
CFG: 9, Steps: 45

### minimalist-line-art
Positive: `minimalist line art, single continuous line, monochrome, elegant, lots of negative space, Picasso line drawing`
Negative: `color, shading, detail, background`
CFG: 6, Steps: 25

## Forbidden Behaviors
- Mixing style presets ("cyberpunk watercolor")
- Trimming the preset's negative prompt
- Changing CFG / steps from the preset

## Output Format
1. The style preset you applied (name)
2. The full positive prompt
3. The full negative prompt
4. CFG and steps
5. The image

