---
name: fluent-2-design-system
description: Use when designing or building a Fluent Design 2 (Microsoft) interface. Always applies the complete Fluent Design 2 (Microsoft) design tokens, typography, color system, and component conventions. Not for other aesthetics.
---

# Fluent Design 2 (Microsoft) Design System

Apply the Fluent Design 2 (Microsoft) aesthetic to any UI with frozen tokens and conventions.

## Design DNA
- **Typography**: Segoe UI, acrylic / mica materials, subtle reveal effects, corner radius 4-8px
- **Color palette**: accent #0078D4, system colors
- **Best for**: Windows apps + Microsoft 365

## Token Layer (CSS variables)
Define semantic tokens that map to Fluent Design 2 (Microsoft) primitives:
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

Apply Fluent Design 2 (Microsoft)'s actual values for each token based on the design DNA above.

## Component Conventions
- **Buttons**: follow Fluent Design 2 (Microsoft) button styles (size, radius, padding, hover)
- **Inputs**: follow Fluent Design 2 (Microsoft) input styles (border, focus ring, padding)
- **Cards**: follow Fluent Design 2 (Microsoft) card styles (shadow, radius, padding)
- **Modals**: follow Fluent Design 2 (Microsoft) modal styles (backdrop, animation, padding)
- **Tables**: follow Fluent Design 2 (Microsoft) table styles (header, rows, hover, borders)
- **Typography**: follow Fluent Design 2 (Microsoft) heading scale, body, captions

## Layout Principles
- Apply Fluent Design 2 (Microsoft)'s spacing rhythm (e.g., 4px / 8px / 16px / 24px / 32px)
- Apply Fluent Design 2 (Microsoft)'s container widths (e.g., max-w-7xl, max-w-4xl)
- Apply Fluent Design 2 (Microsoft)'s grid system
- Apply Fluent Design 2 (Microsoft)'s dark mode rules (if applicable)

## Animation
- Apply Fluent Design 2 (Microsoft)'s motion principles (duration, easing)
- Fluent Design 2 (Microsoft) typically uses: 150ms ease-out for hover, 250ms for state changes

## Iconography
- Use the icon set that matches Fluent Design 2 (Microsoft) (e.g., SF Symbols for Apple, Material Symbols for Material)
- Consistent stroke width / fill style

## Dark Mode
If Fluent Design 2 (Microsoft) supports dark mode, define the dark token overrides:
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
- Don't mix Fluent Design 2 (Microsoft) with other design systems in the same app

## Forbidden Patterns
- Mixing Fluent Design 2 (Microsoft) tokens with another design system
- Overriding Fluent Design 2 (Microsoft) tokens with raw values
- Using a different icon set than Fluent Design 2 (Microsoft) prescribes
- Hard-coding Fluent Design 2 (Microsoft) colors instead of using tokens

## Output Format
1. Token definitions (CSS variables)
2. Tailwind config (if applicable)
3. Example component using the system
4. Dark mode overrides

