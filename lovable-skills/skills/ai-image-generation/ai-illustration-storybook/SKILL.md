---
name: ai-illustration-storybook
description: Use when generating illustrations for children's books, storybooks, comics, or sequential art. Always maintains character and style consistency across all pages of the book.
---

# AI Illustration — Storybook

Storybooks require consistency across many pages. Treat each spread as a scene in a film where the character must look identical.

## Pre-Production
1. Generate the character sheet first (use character-sheet-creator skill)
2. Define the visual style preset (use style-preset-library skill) and lock it for the whole book
3. Define the color palette for the book (3-5 colors)
4. Define the aspect ratio (typically 11×8.5 landscape or 8.5×11 portrait for picture books)

## Per-Page Workflow
For every page:
1. Read the manuscript text for that page
2. Identify: who's in the scene, what's happening, where, what emotion
3. Compose a scene description that fits the book's established world
4. Use the canonical character reference (from the character sheet) with weight 0.7-0.85
5. Use the style preset verbatim
6. Generate, then QC for character consistency

## Composition Variety
- Vary camera angle: wide establishing, medium, close-up
- Vary composition: full-page illustration, vignette, panel
- Vary pacing: full bleed for dramatic moments, smaller illustration for calm moments
- Keep the same style + character identity across all variations

## Spread Layout
- For a 2-page spread: generate as a single wide image (e.g., 22×8.5)
- Or generate two pages separately with consistent horizon line / palette
- Leave space for text — don't put critical illustration details where text will overlay

## Color Storytelling
- Warm palette for happy / safe scenes
- Cool palette for sad / tense scenes
- Saturated for exciting moments
- Desaturated for calm moments
- All within the book's locked palette

## Forbidden Behaviors
- Inventing new character details between pages
- Drifting style between pages
- Forgetting the canonical character reference
- Crowded compositions that don't leave text space

## Output Format
For each page:
1. The manuscript text for that page
2. Scene description
3. Character consistency verification
4. The illustration

