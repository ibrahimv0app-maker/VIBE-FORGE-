---
name: image-batch-pipeline
description: Use when the user needs to generate a batch of related images — a series, a set, variations — that must share style, subject, or theme. Always produces a coherent batch using shared references and prompts.
---

        # Image Batch Pipeline

        Batches must look like they belong together — same style, same palette, same quality. Random prompts produce random-looking batches.

        ## Batch Setup
        Before generating any image, define the batch:
        ```
        BATCH: [name]
        - Shared style: ...
        - Shared palette: 5 hex codes
        - Shared lighting: ...
        - Shared camera: ...
        - Shared negative prompt: ...
        - Shared seed prefix: 42 (variation per item: 4201, 4202, ...)
        - Items: [
            { name: ..., subject: ..., environment: ..., pose: ... },
            { name: ..., subject: ..., environment: ..., pose: ... },
            ...
          ]
        ```

## Per-Item Generation
        For each item, the prompt is:
        ```
        [item.subject], [item.environment], [item.pose],
        [shared style], [shared lighting], [shared camera],
        color palette dominated by [shared palette hex codes],
        [shared negative prompt as negative], ultra-detailed, 8k
        ```
        - Seed: shared prefix + item index
        - Same sampler, same steps, same CFG for every item

        ## Batch QC
        After generating all items, verify:
        - [ ] All items share the same visual style
        - [ ] All items share the same color palette
        - [ ] All items share the same lighting direction
        - [ ] All items have consistent quality (no one item looks lower quality)
        - [ ] All items have correct anatomy / no artifacts

        ## Common Batch Types
        - **Character expression sheet**: same character, 6-8 expressions
        - **Product catalog**: same product, multiple angles or colorways
        - **Story illustration set**: same style, multiple scenes
        - **Tarot / card deck**: same style, 22+ unique cards
        - **Social media batch**: same style, 5-10 posts

        ## Forbidden Behaviors
        - Different prompts per item (creates incoherent batch)
        - Different seeds entirely (creates incoherent batch)
        - Skipping batch QC

        ## Output Format
        1. Batch spec (shared + items)
        2. All images
        3. Batch QC result

