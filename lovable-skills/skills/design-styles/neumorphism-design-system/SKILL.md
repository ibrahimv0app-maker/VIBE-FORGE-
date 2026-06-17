---
name: neumorphism-design-system
description: Use when designing or building a Neumorphism interface. Always applies the complete Neumorphism design tokens, typography, color system, and component conventions. Not for other aesthetics.
---

# Neumorphism Design System

Apply the Neumorphism aesthetic to any UI with frozen tokens and conventions.

## Design DNA
- **Typography**: system soft, extruded soft shadows, monochromatic
- **Color palette**: single hue with light/dark shadows
- **Best for**: creative, niche UIs

## Token Layer (CSS variables)
Define semantic tokens that map to Neumorphism primitives:
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

Apply Neumorphism's actual values for each token based on the design DNA above.

## Component Conventions
- **Buttons**: follow Neumorphism button styles (size, radius, padding, hover)
- **Inputs**: follow Neumorphism input styles (border, focus ring, padding)
- **Cards**: follow Neumorphism card styles (shadow, radius, padding)
- **Modals**: follow Neumorphism modal styles (backdrop, animation, padding)
- **Tables**: follow Neumorphism table styles (header, rows, hover, borders)
- **Typography**: follow Neumorphism heading scale, body, captions

## Layout Principles
- Apply Neumorphism's spacing rhythm (e.g., 4px / 8px / 16px / 24px / 32px)
- Apply Neumorphism's container widths (e.g., max-w-7xl, max-w-4xl)
- Apply Neumorphism's grid system
- Apply Neumorphism's dark mode rules (if applicable)

## Animation
- Apply Neumorphism's motion principles (duration, easing)
- Neumorphism typically uses: 150ms ease-out for hover, 250ms for state changes

## Iconography
- Use the icon set that matches Neumorphism (e.g., SF Symbols for Apple, Material Symbols for Material)
- Consistent stroke width / fill style

## Dark Mode
If Neumorphism supports dark mode, define the dark token overrides:
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
- Don't mix Neumorphism with other design systems in the same app

## Forbidden Patterns
- Mixing Neumorphism tokens with another design system
- Overriding Neumorphism tokens with raw values
- Using a different icon set than Neumorphism prescribes
- Hard-coding Neumorphism colors instead of using tokens

## Output Format
1. Token definitions (CSS variables)
2. Tailwind config (if applicable)
3. Example component using the system
4. Dark mode overrides

