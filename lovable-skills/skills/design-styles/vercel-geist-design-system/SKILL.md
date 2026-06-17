---
name: vercel-geist-design-system
description: Use when designing or building a Vercel Geist interface. Always applies the complete Vercel Geist design tokens, typography, color system, and component conventions. Not for other aesthetics.
---

# Vercel Geist Design System

Apply the Vercel Geist aesthetic to any UI with frozen tokens and conventions.

## Design DNA
- **Typography**: Geist Sans / Mono, tight spacing, monochrome with one accent, sharp corners, subtle gradients
- **Color palette**: pure white/black + 1 accent
- **Best for**: developer tools, SaaS

## Token Layer (CSS variables)
Define semantic tokens that map to Vercel Geist primitives:
```css
:root {
  --font-sans: ...;
  --font-mono: ...;
  --color-background: ...;
  --color-foreground: ...;
  --color-primary: ...;
  --color-primary-foreground: ...;
  --color-muted: ...;
  --color-muted-foreground: ...;
  --color-border: ...;
  --color-success: ...;
  --color-warning: ...;
  --color-error: ...;
  --radius-sm: ...;
  --radius-md: ...;
  --radius-lg: ...;
  --shadow-sm: ...;
  --shadow-md: ...;
  --space-1: ...;
  --space-2: ...;
  --space-4: ...;
  --space-6: ...;
  --space-8: ...;
}
```

Apply Vercel Geist's actual values for each token based on the design DNA above.

## Component Conventions
- **Buttons**: follow Vercel Geist button styles (size, radius, padding, hover)
- **Inputs**: follow Vercel Geist input styles (border, focus ring, padding)
- **Cards**: follow Vercel Geist card styles (shadow, radius, padding)
- **Modals**: follow Vercel Geist modal styles (backdrop, animation, padding)
- **Tables**: follow Vercel Geist table styles (header, rows, hover, borders)
- **Typography**: follow Vercel Geist heading scale, body, captions

## Layout Principles
- Apply Vercel Geist's spacing rhythm (e.g., 4px / 8px / 16px / 24px / 32px)
- Apply Vercel Geist's container widths (e.g., max-w-7xl, max-w-4xl)
- Apply Vercel Geist's grid system
- Apply Vercel Geist's dark mode rules (if applicable)

## Animation
- Apply Vercel Geist's motion principles (duration, easing)
- Vercel Geist typically uses: 150ms ease-out for hover, 250ms for state changes

## Iconography
- Use the icon set that matches Vercel Geist (e.g., SF Symbols for Apple, Material Symbols for Material)
- Consistent stroke width / fill style

## Dark Mode
If Vercel Geist supports dark mode, define the dark token overrides:
```css
.dark {
  --color-background: ...;
  --color-foreground: ...;
  /* ... */
}
```

## Implementation Notes
- Use Tailwind tokens mapped to these CSS variables
- Or use a CSS-first approach with the variables directly
- Don't mix Vercel Geist with other design systems in the same app

## Forbidden Patterns
- Mixing Vercel Geist tokens with another design system
- Overriding Vercel Geist tokens with raw values
- Using a different icon set than Vercel Geist prescribes
- Hard-coding Vercel Geist colors instead of using tokens

## Output Format
1. Token definitions (CSS variables)
2. Tailwind config (if applicable)
3. Example component using the system
4. Dark mode overrides

