---
name: figma-design-system
description: Use when designing or building a Figma interface. Always applies the complete Figma design tokens, typography, color system, and component conventions. Not for other aesthetics.
---

# Figma Design System

Apply the Figma aesthetic to any UI with frozen tokens and conventions.

## Design DNA
- **Typography**: Inter, dense, multi-canvas, purple accent, subtle shadows, segmented controls
- **Color palette**: #0D99FF primary, neutral grays
- **Best for**: design tools, creative apps

## Token Layer (CSS variables)
Define semantic tokens that map to Figma primitives:
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

Apply Figma's actual values for each token based on the design DNA above.

## Component Conventions
- **Buttons**: follow Figma button styles (size, radius, padding, hover)
- **Inputs**: follow Figma input styles (border, focus ring, padding)
- **Cards**: follow Figma card styles (shadow, radius, padding)
- **Modals**: follow Figma modal styles (backdrop, animation, padding)
- **Tables**: follow Figma table styles (header, rows, hover, borders)
- **Typography**: follow Figma heading scale, body, captions

## Layout Principles
- Apply Figma's spacing rhythm (e.g., 4px / 8px / 16px / 24px / 32px)
- Apply Figma's container widths (e.g., max-w-7xl, max-w-4xl)
- Apply Figma's grid system
- Apply Figma's dark mode rules (if applicable)

## Animation
- Apply Figma's motion principles (duration, easing)
- Figma typically uses: 150ms ease-out for hover, 250ms for state changes

## Iconography
- Use the icon set that matches Figma (e.g., SF Symbols for Apple, Material Symbols for Material)
- Consistent stroke width / fill style

## Dark Mode
If Figma supports dark mode, define the dark token overrides:
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
- Don't mix Figma with other design systems in the same app

## Forbidden Patterns
- Mixing Figma tokens with another design system
- Overriding Figma tokens with raw values
- Using a different icon set than Figma prescribes
- Hard-coding Figma colors instead of using tokens

## Output Format
1. Token definitions (CSS variables)
2. Tailwind config (if applicable)
3. Example component using the system
4. Dark mode overrides

