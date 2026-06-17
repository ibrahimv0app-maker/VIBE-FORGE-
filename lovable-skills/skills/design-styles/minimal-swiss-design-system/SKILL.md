---
name: minimal-swiss-design-system
description: Use when designing or building a Swiss Minimal interface. Always applies the complete Swiss Minimal design tokens, typography, color system, and component conventions. Not for other aesthetics.
---

# Swiss Minimal Design System

Apply the Swiss Minimal aesthetic to any UI with frozen tokens and conventions.

## Design DNA
- **Typography**: Helvetica / Inter, grid-based, generous whitespace, red accent
- **Color palette**: near-black on white + one accent
- **Best for**: design studios, portfolios

## Token Layer (CSS variables)
Define semantic tokens that map to Swiss Minimal primitives:
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

Apply Swiss Minimal's actual values for each token based on the design DNA above.

## Component Conventions
- **Buttons**: follow Swiss Minimal button styles (size, radius, padding, hover)
- **Inputs**: follow Swiss Minimal input styles (border, focus ring, padding)
- **Cards**: follow Swiss Minimal card styles (shadow, radius, padding)
- **Modals**: follow Swiss Minimal modal styles (backdrop, animation, padding)
- **Tables**: follow Swiss Minimal table styles (header, rows, hover, borders)
- **Typography**: follow Swiss Minimal heading scale, body, captions

## Layout Principles
- Apply Swiss Minimal's spacing rhythm (e.g., 4px / 8px / 16px / 24px / 32px)
- Apply Swiss Minimal's container widths (e.g., max-w-7xl, max-w-4xl)
- Apply Swiss Minimal's grid system
- Apply Swiss Minimal's dark mode rules (if applicable)

## Animation
- Apply Swiss Minimal's motion principles (duration, easing)
- Swiss Minimal typically uses: 150ms ease-out for hover, 250ms for state changes

## Iconography
- Use the icon set that matches Swiss Minimal (e.g., SF Symbols for Apple, Material Symbols for Material)
- Consistent stroke width / fill style

## Dark Mode
If Swiss Minimal supports dark mode, define the dark token overrides:
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
- Don't mix Swiss Minimal with other design systems in the same app

## Forbidden Patterns
- Mixing Swiss Minimal tokens with another design system
- Overriding Swiss Minimal tokens with raw values
- Using a different icon set than Swiss Minimal prescribes
- Hard-coding Swiss Minimal colors instead of using tokens

## Output Format
1. Token definitions (CSS variables)
2. Tailwind config (if applicable)
3. Example component using the system
4. Dark mode overrides

