---
name: material-3-design-system
description: Use when designing or building a Material Design 3 (Material You) interface. Always applies the complete Material Design 3 (Material You) design tokens, typography, color system, and component conventions. Not for other aesthetics.
---

# Material Design 3 (Material You) Design System

Apply the Material Design 3 (Material You) aesthetic to any UI with frozen tokens and conventions.

## Design DNA
- **Typography**: Roboto Flex, dynamic color from wallpaper, elevation tonal, large rounded corners, FAB
- **Color palette**: primary, on-primary, primary-container, surface, surface-variant
- **Best for**: Android apps + Material web

## Token Layer (CSS variables)
Define semantic tokens that map to Material Design 3 (Material You) primitives:
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

Apply Material Design 3 (Material You)'s actual values for each token based on the design DNA above.

## Component Conventions
- **Buttons**: follow Material Design 3 (Material You) button styles (size, radius, padding, hover)
- **Inputs**: follow Material Design 3 (Material You) input styles (border, focus ring, padding)
- **Cards**: follow Material Design 3 (Material You) card styles (shadow, radius, padding)
- **Modals**: follow Material Design 3 (Material You) modal styles (backdrop, animation, padding)
- **Tables**: follow Material Design 3 (Material You) table styles (header, rows, hover, borders)
- **Typography**: follow Material Design 3 (Material You) heading scale, body, captions

## Layout Principles
- Apply Material Design 3 (Material You)'s spacing rhythm (e.g., 4px / 8px / 16px / 24px / 32px)
- Apply Material Design 3 (Material You)'s container widths (e.g., max-w-7xl, max-w-4xl)
- Apply Material Design 3 (Material You)'s grid system
- Apply Material Design 3 (Material You)'s dark mode rules (if applicable)

## Animation
- Apply Material Design 3 (Material You)'s motion principles (duration, easing)
- Material Design 3 (Material You) typically uses: 150ms ease-out for hover, 250ms for state changes

## Iconography
- Use the icon set that matches Material Design 3 (Material You) (e.g., SF Symbols for Apple, Material Symbols for Material)
- Consistent stroke width / fill style

## Dark Mode
If Material Design 3 (Material You) supports dark mode, define the dark token overrides:
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
- Don't mix Material Design 3 (Material You) with other design systems in the same app

## Forbidden Patterns
- Mixing Material Design 3 (Material You) tokens with another design system
- Overriding Material Design 3 (Material You) tokens with raw values
- Using a different icon set than Material Design 3 (Material You) prescribes
- Hard-coding Material Design 3 (Material You) colors instead of using tokens

## Output Format
1. Token definitions (CSS variables)
2. Tailwind config (if applicable)
3. Example component using the system
4. Dark mode overrides

