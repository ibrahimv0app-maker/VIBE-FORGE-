---
name: ai-pixel-art-sprite-generator
description: Use when generating pixel art sprites, tiles, or scenes for games. Always respects the chosen pixel resolution, color palette, and animation frame conventions.
---

        # AI Pixel Art Sprite Generator

        Pixel art is a discipline of constraints. Respect the constraints or it's not pixel art.

        ## Constraints
        - Resolution: 16×16, 32×32, 64×64, 128×128 (pick one, stick to it)
        - Palette: limited (8, 16, or 32 colors max)
        - No anti-aliasing
        - No gradients (use dithering instead)
        - Pixel-perfect edges
        - Consistent light source (usually top-left or top)

        ## Prompt Template
        ```
        Pixel art sprite of [SUBJECT], [resolution] resolution, [palette size] color palette,
        [palette description: earth tones / neon / pastel],
        dithering for shading, no anti-aliasing, pixel-perfect,
        SNES / NES / Game Boy aesthetic, sprite sheet
        ```

## Animation Frames
        For animated sprites, generate a sheet:
        ```
        Pixel art sprite sheet of [SUBJECT], [N] frames of [ANIMATION: idle / walk / attack / jump],
        arranged horizontally, [resolution] per frame,
        consistent silhouette across frames, [palette], no anti-aliasing
        ```

        ## Tiles
        For tileable game tiles:
        ```
        Pixel art tileable [MATERIAL: grass / stone / water / sand],
        16×16 tile, [palette], seamless tileable edges, no anti-aliasing, NES / SNES style
        ```

        ## Quality Checks
        - [ ] Every pixel is on the palette (no off-palette colors)
        - [ ] No anti-aliasing artifacts
        - [ ] No blurry edges
        - [ ] Light source consistent
        - [ ] Tileable (if a tile): seamless when repeated
        - [ ] Animation: silhouette readable in every frame

        ## Forbidden Behaviors
        - High-res output (defeats the point)
        - Anti-aliased edges
        - Off-palette colors
        - Gradients

        ## Output Format
        1. Resolution + palette
        2. The sprite / sheet
        3. Palette verification

