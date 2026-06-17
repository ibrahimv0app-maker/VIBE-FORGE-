---
name: linear-design-system
description: Use when designing or building a Linear interface. Always applies the complete Linear design tokens, typography, color system, and component conventions. Not for other aesthetics.
---

# Linear Design System

Apply the Linear aesthetic to any UI with frozen tokens and conventions.

## Design DNA
- **Typography**: Inter, dense layouts, keyboard-first, dark mode native, sharp edges, subtle gradients
- **Color palette**: deep purple #5E6AD2, neutral grays
- **Best for**: project management, dev tools

## Token Layer (CSS variables)
Define semantic tokens that map to Linear primitives:
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

Apply Linear's actual values for each token based on the design DNA above.

## Component Conventions
- **Buttons**: follow Linear button styles (size, radius, padding, hover)
- **Inputs**: follow Linear input styles (border, focus ring, padding)
- **Cards**: follow Linear card styles (shadow, radius, padding)
- **Modals**: follow Linear modal styles (backdrop, animation, padding)
- **Tables**: follow Linear table styles (header, rows, hover, borders)
- **Typography**: follow Linear heading scale, body, captions

## Layout Principles
- Apply Linear's spacing rhythm (e.g., 4px / 8px / 16px / 24px / 32px)
- Apply Linear's container widths (e.g., max-w-7xl, max-w-4xl)
- Apply Linear's grid system
- Apply Linear's dark mode rules (if applicable)

## Animation
- Apply Linear's motion principles (duration, easing)
- Linear typically uses: 150ms ease-out for hover, 250ms for state changes

## Iconography
- Use the icon set that matches Linear (e.g., SF Symbols for Apple, Material Symbols for Material)
- Consistent stroke width / fill style

## Dark Mode
If Linear supports dark mode, define the dark token overrides:
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
- Don't mix Linear with other design systems in the same app

## Forbidden Patterns
- Mixing Linear tokens with another design system
- Overriding Linear tokens with raw values
- Using a different icon set than Linear prescribes
- Hard-coding Linear colors instead of using tokens

## Output Format
1. Token definitions (CSS variables)
2. Tailwind config (if applicable)
3. Example component using the system
4. Dark mode overrides

