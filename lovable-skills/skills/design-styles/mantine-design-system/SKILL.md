---
name: mantine-design-system
description: Use when designing or building a Mantine interface. Always applies the complete Mantine design tokens, typography, color system, and component conventions. Not for other aesthetics.
---

# Mantine Design System

Apply the Mantine aesthetic to any UI with frozen tokens and conventions.

## Design DNA
- **Typography**: Inter, dense, hooks-first, dark mode native
- **Color palette**: #228BE6 primary, neutral grays
- **Best for**: general React apps

## Token Layer (CSS variables)
Define semantic tokens that map to Mantine primitives:
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

Apply Mantine's actual values for each token based on the design DNA above.

## Component Conventions
- **Buttons**: follow Mantine button styles (size, radius, padding, hover)
- **Inputs**: follow Mantine input styles (border, focus ring, padding)
- **Cards**: follow Mantine card styles (shadow, radius, padding)
- **Modals**: follow Mantine modal styles (backdrop, animation, padding)
- **Tables**: follow Mantine table styles (header, rows, hover, borders)
- **Typography**: follow Mantine heading scale, body, captions

## Layout Principles
- Apply Mantine's spacing rhythm (e.g., 4px / 8px / 16px / 24px / 32px)
- Apply Mantine's container widths (e.g., max-w-7xl, max-w-4xl)
- Apply Mantine's grid system
- Apply Mantine's dark mode rules (if applicable)

## Animation
- Apply Mantine's motion principles (duration, easing)
- Mantine typically uses: 150ms ease-out for hover, 250ms for state changes

## Iconography
- Use the icon set that matches Mantine (e.g., SF Symbols for Apple, Material Symbols for Material)
- Consistent stroke width / fill style

## Dark Mode
If Mantine supports dark mode, define the dark token overrides:
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
- Don't mix Mantine with other design systems in the same app

## Forbidden Patterns
- Mixing Mantine tokens with another design system
- Overriding Mantine tokens with raw values
- Using a different icon set than Mantine prescribes
- Hard-coding Mantine colors instead of using tokens

## Output Format
1. Token definitions (CSS variables)
2. Tailwind config (if applicable)
3. Example component using the system
4. Dark mode overrides

