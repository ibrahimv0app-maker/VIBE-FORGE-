---
name: logo-and-brand-asset-generator
description: Use when generating logos, brand marks, icons, and identity assets. Always produces vector-clean, scalable, brand-appropriate designs with proper simplification.
---

# Logo & Brand Asset Generator

Logos must be simple, scalable, and conceptually tight. AI image models tend to over-detail — fight that.

## Logo Types
1. **Wordmark**: type-only (Coca-Cola, Google)
2. **Lettermark**: abbreviation (IBM, HBO)
3. **Pictorial mark**: icon (Apple, Twitter bird)
4. **Abstract mark**: geometric (Nike swoosh, Pepsi circle)
5. **Mascot**: character (KFC colonel, Michelin man)
6. **Emblem**: text inside a shape (Starbucks, Harley-Davidson)
7. **Combination mark**: icon + text (Burger King, Lacoste)

## Generation Rules
- Maximum 2-3 colors in the mark itself (full brand palette can be wider)
- Solid shapes only — no gradients in the core mark (gradient variants are separate)
- Works in pure black and pure white (test both)
- No fine detail that disappears at small sizes
- No realistic imagery (no photographs, no complex illustrations)
- Symmetry is intentional or absent — never accidental

## Prompt Template
```
Minimalist logo design for [BRAND NAME], [industry / vibe descriptor],
[logo type: wordmark / pictorial / abstract / emblem / combination],
[1-2 core colors], solid shapes, flat vector, clean geometric forms,
scalable, works at 32px, on white background, professional, timeless
```

## Style Anchors
- Tech / SaaS: geometric sans-serif, single accent color, abstract mark
- Luxury: serif wordmark, monochrome or gold-on-black, refined spacing
- Playful / kids: rounded sans, bright primary palette, mascot-friendly
- Eco / wellness: organic shapes, earth tones, leaf / curve motifs
- Editorial / fashion: high-contrast serif, generous negative space

## Post-Generation Cleanup
- Verify the logo reads at 32×32px (no detail lost)
- Verify it works in pure black and pure white
- Remove any "AI artifacts" — random squiggles, nonsensical text, fake letters
- For wordmarks: confirm the letters are correct (AI often invents fake glyphs)

## Deliverables
- Primary logo (full color, on white)
- Primary logo (on dark)
- Monochrome (black on white)
- Monochrome (white on black)
- Favicon / app icon (simplified if needed)

## Forbidden Behaviors
- Photorealistic logos
- Logos with fake / illegible text
- Logos that only work in color (must work in monochrome)
- More than 3 colors in the core mark

## Output Format
1. Logo concept statement (one sentence)
2. The primary logo
3. Monochrome variants
4. Scalability check note

