---
name: shadcn-design-system
description: Use when designing or building a shadcn/ui interface. Always applies the complete shadcn/ui design tokens, typography, color system, and component conventions. Not for other aesthetics.
---

# shadcn/ui Design System

Apply the shadcn/ui aesthetic to any UI with frozen tokens and conventions.

## Design DNA
- **Typography**: Geist / Inter, Radix primitives, Tailwind tokens, customizable
- **Color palette**: HSL CSS variables, semantic
- **Best for**: modern React apps

## Token Layer (CSS variables)
Define semantic tokens that map to shadcn/ui primitives:
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

Apply shadcn/ui's actual values for each token based on the design DNA above.

## Component Conventions
- **Buttons**: follow shadcn/ui button styles (size, radius, padding, hover)
- **Inputs**: follow shadcn/ui input styles (border, focus ring, padding)
- **Cards**: follow shadcn/ui card styles (shadow, radius, padding)
- **Modals**: follow shadcn/ui modal styles (backdrop, animation, padding)
- **Tables**: follow shadcn/ui table styles (header, rows, hover, borders)
- **Typography**: follow shadcn/ui heading scale, body, captions

## Layout Principles
- Apply shadcn/ui's spacing rhythm (e.g., 4px / 8px / 16px / 24px / 32px)
- Apply shadcn/ui's container widths (e.g., max-w-7xl, max-w-4xl)
- Apply shadcn/ui's grid system
- Apply shadcn/ui's dark mode rules (if applicable)

## Animation
- Apply shadcn/ui's motion principles (duration, easing)
- shadcn/ui typically uses: 150ms ease-out for hover, 250ms for state changes

## Iconography
- Use the icon set that matches shadcn/ui (e.g., SF Symbols for Apple, Material Symbols for Material)
- Consistent stroke width / fill style

## Dark Mode
If shadcn/ui supports dark mode, define the dark token overrides:
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
- Don't mix shadcn/ui with other design systems in the same app

## Forbidden Patterns
- Mixing shadcn/ui tokens with another design system
- Overriding shadcn/ui tokens with raw values
- Using a different icon set than shadcn/ui prescribes
- Hard-coding shadcn/ui colors instead of using tokens

## Output Format
1. Token definitions (CSS variables)
2. Tailwind config (if applicable)
3. Example component using the system
4. Dark mode overrides

