---
name: ai-3d-texture-pbr-generator
description: Use when generating PBR textures (albedo, normal, roughness, metallic, AO) for 3D rendering. Always produces tileable, physically plausible texture sets.
---

# AI 3D Texture / PBR Generator

PBR textures are not "pictures of materials" — they are physically-based data maps that drive a 3D shader.

## PBR Map Set
A complete PBR set includes:
- **Albedo / Base Color**: pure color, no lighting baked in
- **Normal**: surface micro-relief (RGB encodes surface normal)
- **Roughness**: how glossy (0 = mirror, 1 = matte)
- **Metallic**: 0 or 1 (mostly),” ish metal mask
- **AO (Ambient Occlusion)**: contact shadows
- **Height**: optional, displacement
- **Opacity**: optional, for transparent materials

## Generation Rules
- All maps MUST be tileable (seamless when repeated)
- All maps MUST align (same UV layout)
- Resolution: 2048×2048 or 4096×4096 standard
- Albedo: no baked shadows, no specular highlights
- Normal: standard tangent-space (RGB)
- Roughness: grayscale, 8-bit
- Metallic: grayscale, mostly 0 or 255 with anti-aliased edges

## Prompt Template (Albedo)
```
Seamless tileable [MATERIAL] albedo texture, [color description],
no lighting, no shadows, no highlights, flatlit, orthographic top-down view,
physically based, 4k texture, ultra-detailed
```

## Prompt Template (Normal)
```
Seamless tileable [MATERIAL] normal map, tangent space,
[surface relief description], RGB normal map, no color information,
4k texture, ultra-detailed
```

## Workflow
1. Generate the albedo first (defines color and pattern)
2. Generate the normal from the same material description (so they align)
3. Generate the roughness based on the material (metal = low roughness, fabric = high)
4. Generate the metallic (1 for metals, 0 for non-metals)
5. Generate AO from the albedo or as a separate pass
6. Verify tileability by inspecting edges

## Material-Specific Notes
- Wood: grain direction consistent, plank seams if applicable
- Metal: scratches follow usage patterns, rust in low spots
- Fabric: weave pattern visible, no folds
- Stone: natural variation, no repeats visible
- Concrete: cracks natural, stains plausible

## Forbidden Behaviors
- Non-tileable textures (visible seams)
- Baked lighting in albedo
- Mismatched alignment between maps
- Wrong color space (sRGB vs linear)

## Output Format
1. Material description
2. All PBR maps
3. Tileability verification
4. Recommended use (asset type, render engine)

