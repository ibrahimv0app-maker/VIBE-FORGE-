---
name: chakra-ui-design-system
description: Use when designing or building a Chakra UI interface. Always applies the complete Chakra UI design tokens, typography, color system, and component conventions. Not for other aesthetics.
---

# Chakra UI Design System

Apply the Chakra UI aesthetic to any UI with frozen tokens and conventions.

## Design DNA
- **Typography**: Inter, accessible, component-driven, purple accent
- **Color palette**: #805AD5 primary, semantic colors
- **Best for**: general React apps

## Token Layer (CSS variables)
Define semantic tokens that map to Chakra UI primitives:
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

Apply Chakra UI's actual values for each token based on the design DNA above.

## Component Conventions
- **Buttons**: follow Chakra UI button styles (size, radius, padding, hover)
- **Inputs**: follow Chakra UI input styles (border, focus ring, padding)
- **Cards**: follow Chakra UI card styles (shadow, radius, padding)
- **Modals**: follow Chakra UI modal styles (backdrop, animation, padding)
- **Tables**: follow Chakra UI table styles (header, rows, hover, borders)
- **Typography**: follow Chakra UI heading scale, body, captions

## Layout Principles
- Apply Chakra UI's spacing rhythm (e.g., 4px / 8px / 16px / 24px / 32px)
- Apply Chakra UI's container widths (e.g., max-w-7xl, max-w-4xl)
- Apply Chakra UI's grid system
- Apply Chakra UI's dark mode rules (if applicable)

## Animation
- Apply Chakra UI's motion principles (duration, easing)
- Chakra UI typically uses: 150ms ease-out for hover, 250ms for state changes

## Iconography
- Use the icon set that matches Chakra UI (e.g., SF Symbols for Apple, Material Symbols for Material)
- Consistent stroke width / fill style

## Dark Mode
If Chakra UI supports dark mode, define the dark token overrides:
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
- Don't mix Chakra UI with other design systems in the same app

## Forbidden Patterns
- Mixing Chakra UI tokens with another design system
- Overriding Chakra UI tokens with raw values
- Using a different icon set than Chakra UI prescribes
- Hard-coding Chakra UI colors instead of using tokens

## Output Format
1. Token definitions (CSS variables)
2. Tailwind config (if applicable)
3. Example component using the system
4. Dark mode overrides

