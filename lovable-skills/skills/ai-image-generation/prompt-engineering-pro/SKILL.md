---
name: prompt-engineering-pro
description: Use when the user asks for help crafting or refining an AI image generation prompt — for any model (Midjourney, DALL-E 3, Stable Diffusion, FLUX, Ideogram). Always produces structured, model-specific prompts following best practices.
---

     # Prompt Engineering Pro

     A great image prompt is structured, specific, and model-aware. Avoid vibe-only prompts.

     ## Universal Prompt Skeleton
     ```
     [SUBJECT] + [ACTION/POSE] + [ENVIRONMENT] + [CAMERA] + [LENS] + [LIGHTING] +
     [COLOR PALETTE] + [STYLE] + [MOOD] + [TECHNICAL: resolution, detail, render]
     ```

     ## Subject Block
     - Be specific: "a 30-year-old woman with auburn hair and freckles" not "a woman"
     - Include posture / action: "leaning on a windowsill, reading a paperback"
     - Include expression: "with a soft, distracted smile"

     ## Environment Block
     - Name the place: "a Parisian café at dusk"
ing layer
     - Add at least 3 specific objects to anchor the scene

     ## Camera Block
     - Camera body (ARRI Alexa, Hasselblad, Sony A7)
     - Lens (35mm, 85mm, 14mm ultra-wide, 200mm telephoto)
     - Angle (eye-level, low-angle, top-down, Dutch tilt)
     - Distance (extreme close-up, medium shot, wide shot)

     ## Lighting Block
     - Quality: hard / soft / diffused / dappled
     - Direction: front / side / back / top / bottom
     - Color temperature: warm 3200K / neutral 5500K / cool 7500K
     - Source: natural window light, golden hour, neon, candlelight, strobe

     ## Color Palette Block
     - Name 3-5 dominant colors (or hex codes)
     - Specify palette mood: muted, vibrant, monochrome, complementary

     ## Style Block
     - Medium: photograph, oil painting, watercolor, 3D render, illustration
     - Substyle: cinematic, editorial, documentary, fashion, fine-art
     - Influences (optional): name an artist or movement as a flavor anchor

     ## Mood Block
     - 3 adjectives that describe the feeling

     ## Technical Block
     - Resolution: 4k, 8k
     - Detail: ultra-detailed, sharp focus, intricate detail
     - Render: ray-traced, subsurface scattering (for 3D)

     ## Model-Specific Notes
     - **Midjourney v6**: prefer natural prose, parameters at end `--ar 16:9 --style raw --v 6`
     - **DALL-E 3**: conversational, full sentences, no parameters
     - **Stable Diffusion / FLUX**: comma-separated tags, can use LoRA / negative prompts
     - **Ideogram**: explicit text rendering instructions, use `""` for any text in image

     ## Negative Prompt (SD/FLUX only)
     Always include:
     `lowres, blurry, deformed, extra limbs, bad anatomy, watermark, signature, jpeg artifacts, oversaturated, plastic skin, mutated hands, extra fingers, missing fingers`

     ## Workflow with User
     1. Clarify subject, environment, mood if missing
     2. Draft prompt using the skeleton
     3. Show the structured prompt to user
     4. Generate the image
     5. Offer one variation prompt (e.g., different lighting) without regenerating

     ## Forbidden Behaviors
     - One-line "a woman in a cafe" prompts
     - Forgetting lighting
     - Forgetting camera
     - Stacking every adjective you know

     ## Output Format
     1. Structured prompt (show all blocks)
     2. Negative prompt (if applicable)
     3. Model parameters (if applicable)
     4. The image
     5. One alternative-prompt suggestion

