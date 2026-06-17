---
name: brutalist-design-system
description: Use when designing or building a Neo-Brutalism interface. Always applies the complete Neo-Brutalism design tokens, typography, color system, and component conventions. Not for other aesthetics.
---

# Neo-Brutalism Design System

Apply the Neo-Brutalism aesthetic to any UI with frozen tokens and conventions.

## Design DNA
- **Typography**: system mono / sans, sharp edges, thick black borders, hard shadows, clashing colors
- **Color palette**: pure primaries + black + white
- **Best for**: creative, indie, web3

## Token Layer (CSS variables)
Define semantic tokens that map to Neo-Brutalism primitives:
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

Apply Neo-Brutalism's actual values for each token based on the design DNA above.

## Component Conventions
- **Buttons**: follow Neo-Brutalism button styles (size, radius, padding, hover)
- **Inputs**: follow Neo-Brutalism input styles (border, focus ring, padding)
- **Cards**: follow Neo-Brutalism card styles (shadow, radius, padding)
- **Modals**: follow Neo-Brutalism modal styles (backdrop, animation, padding)
- **Tables**: follow Neo-Brutalism table styles (header, rows, hover, borders)
- **Typography**: follow Neo-Brutalism heading scale, body, captions

## Layout Principles
- Apply Neo-Brutalism's spacing rhythm (e.g., 4px / 8px / 16px / 24px / 32px)
- Apply Neo-Brutalism's container widths (e.g., max-w-7xl, max-w-4xl)
- Apply Neo-Brutalism's grid system
- Apply Neo-Brutalism's dark mode rules (if applicable)

## Animation
- Apply Neo-Brutalism's motion principles (duration, easing)
- Neo-Brutalism typically uses: 150ms ease-out for hover, 250ms for state changes

## Iconography
- Use the icon set that matches Neo-Brutalism (e.g., SF Symbols for Apple, Material Symbols for Material)
- Consistent stroke width / fill style

## Dark Mode
If Neo-Brutalism supports dark mode, define the dark token overrides:
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
- Don't mix Neo-Brutalism with other design systems in the same app

## Forbidden Patterns
- Mixing Neo-Brutalism tokens with another design system
- Overriding Neo-Brutalism tokens with raw values
- Using a different icon set than Neo-Brutalism prescribes
- Hard-coding Neo-Brutalism colors instead of using tokens

## Output Format
1. Token definitions (CSS variables)
2. Tailwind config (if applicable)
3. Example component using the system
4. Dark mode overrides

