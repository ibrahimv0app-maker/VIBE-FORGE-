---
name: radix-themes-design-system
description: Use when designing or building a Radix Themes interface. Always applies the complete Radix Themes design tokens, typography, color system, and component conventions. Not for other aesthetics.
---

# Radix Themes Design System

Apply the Radix Themes aesthetic to any UI with frozen tokens and conventions.

## Design DNA
- **Typography**: Inter, vanilla-extract, no runtime, themeable
- **Color palette**: HSL CSS variables
- **Best for**: accessible React apps

## Token Layer (CSS variables)
Define semantic tokens that map to Radix Themes primitives:
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

Apply Radix Themes's actual values for each token based on the design DNA above.

## Component Conventions
- **Buttons**: follow Radix Themes button styles (size, radius, padding, hover)
- **Inputs**: follow Radix Themes input styles (border, focus ring, padding)
- **Cards**: follow Radix Themes card styles (shadow, radius, padding)
- **Modals**: follow Radix Themes modal styles (backdrop, animation, padding)
- **Tables**: follow Radix Themes table styles (header, rows, hover, borders)
- **Typography**: follow Radix Themes heading scale, body, captions

## Layout Principles
- Apply Radix Themes's spacing rhythm (e.g., 4px / 8px / 16px / 24px / 32px)
- Apply Radix Themes's container widths (e.g., max-w-7xl, max-w-4xl)
- Apply Radix Themes's grid system
- Apply Radix Themes's dark mode rules (if applicable)

## Animation
- Apply Radix Themes's motion principles (duration, easing)
- Radix Themes typically uses: 150ms ease-out for hover, 250ms for state changes

## Iconography
- Use the icon set that matches Radix Themes (e.g., SF Symbols for Apple, Material Symbols for Material)
- Consistent stroke width / fill style

## Dark Mode
If Radix Themes supports dark mode, define the dark token overrides:
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
- Don't mix Radix Themes with other design systems in the same app

## Forbidden Patterns
- Mixing Radix Themes tokens with another design system
- Overriding Radix Themes tokens with raw values
- Using a different icon set than Radix Themes prescribes
- Hard-coding Radix Themes colors instead of using tokens

## Output Format
1. Token definitions (CSS variables)
2. Tailwind config (if applicable)
3. Example component using the system
4. Dark mode overrides

