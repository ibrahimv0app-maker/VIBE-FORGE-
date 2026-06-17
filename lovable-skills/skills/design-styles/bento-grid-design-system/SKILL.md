---
name: bento-grid-design-system
description: Use when designing or building a Bento Grid interface. Always applies the complete Bento Grid design tokens, typography, color system, and component conventions. Not for other aesthetics.
---

# Bento Grid Design System

Apply the Bento Grid aesthetic to any UI with frozen tokens and conventions.

## Design DNA
- **Typography**: Inter, asymmetric grid of cards, varied sizes, subtle shadows
- **Color palette**: neutral + accent per card
- **Best for**: modern marketing, dashboards

## Token Layer (CSS variables)
Define semantic tokens that map to Bento Grid primitives:
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

Apply Bento Grid's actual values for each token based on the design DNA above.

## Component Conventions
- **Buttons**: follow Bento Grid button styles (size, radius, padding, hover)
- **Inputs**: follow Bento Grid input styles (border, focus ring, padding)
- **Cards**: follow Bento Grid card styles (shadow, radius, padding)
- **Modals**: follow Bento Grid modal styles (backdrop, animation, padding)
- **Tables**: follow Bento Grid table styles (header, rows, hover, borders)
- **Typography**: follow Bento Grid heading scale, body, captions

## Layout Principles
- Apply Bento Grid's spacing rhythm (e.g., 4px / 8px / 16px / 24px / 32px)
- Apply Bento Grid's container widths (e.g., max-w-7xl, max-w-4xl)
- Apply Bento Grid's grid system
- Apply Bento Grid's dark mode rules (if applicable)

## Animation
- Apply Bento Grid's motion principles (duration, easing)
- Bento Grid typically uses: 150ms ease-out for hover, 250ms for state changes

## Iconography
- Use the icon set that matches Bento Grid (e.g., SF Symbols for Apple, Material Symbols for Material)
- Consistent stroke width / fill style

## Dark Mode
If Bento Grid supports dark mode, define the dark token overrides:
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
- Don't mix Bento Grid with other design systems in the same app

## Forbidden Patterns
- Mixing Bento Grid tokens with another design system
- Overriding Bento Grid tokens with raw values
- Using a different icon set than Bento Grid prescribes
- Hard-coding Bento Grid colors instead of using tokens

## Output Format
1. Token definitions (CSS variables)
2. Tailwind config (if applicable)
3. Example component using the system
4. Dark mode overrides

