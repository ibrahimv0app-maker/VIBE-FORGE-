---
name: stripe-design-system
description: Use when designing or building a Stripe Dashboard interface. Always applies the complete Stripe Dashboard design tokens, typography, color system, and component conventions. Not for other aesthetics.
---

# Stripe Dashboard Design System

Apply the Stripe Dashboard aesthetic to any UI with frozen tokens and conventions.

## Design DNA
- **Typography**: Camphor, generous spacing, subtle gradients, soft shadows, blue/purple accents
- **Color palette**: #635BFF primary, subtle gradient meshes
- **Best for**: fintech, dashboards

## Token Layer (CSS variables)
Define semantic tokens that map to Stripe Dashboard primitives:
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

Apply Stripe Dashboard's actual values for each token based on the design DNA above.

## Component Conventions
- **Buttons**: follow Stripe Dashboard button styles (size, radius, padding, hover)
- **Inputs**: follow Stripe Dashboard input styles (border, focus ring, padding)
- **Cards**: follow Stripe Dashboard card styles (shadow, radius, padding)
- **Modals**: follow Stripe Dashboard modal styles (backdrop, animation, padding)
- **Tables**: follow Stripe Dashboard table styles (header, rows, hover, borders)
- **Typography**: follow Stripe Dashboard heading scale, body, captions

## Layout Principles
- Apply Stripe Dashboard's spacing rhythm (e.g., 4px / 8px / 16px / 24px / 32px)
- Apply Stripe Dashboard's container widths (e.g., max-w-7xl, max-w-4xl)
- Apply Stripe Dashboard's grid system
- Apply Stripe Dashboard's dark mode rules (if applicable)

## Animation
- Apply Stripe Dashboard's motion principles (duration, easing)
- Stripe Dashboard typically uses: 150ms ease-out for hover, 250ms for state changes

## Iconography
- Use the icon set that matches Stripe Dashboard (e.g., SF Symbols for Apple, Material Symbols for Material)
- Consistent stroke width / fill style

## Dark Mode
If Stripe Dashboard supports dark mode, define the dark token overrides:
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
- Don't mix Stripe Dashboard with other design systems in the same app

## Forbidden Patterns
- Mixing Stripe Dashboard tokens with another design system
- Overriding Stripe Dashboard tokens with raw values
- Using a different icon set than Stripe Dashboard prescribes
- Hard-coding Stripe Dashboard colors instead of using tokens

## Output Format
1. Token definitions (CSS variables)
2. Tailwind config (if applicable)
3. Example component using the system
4. Dark mode overrides

