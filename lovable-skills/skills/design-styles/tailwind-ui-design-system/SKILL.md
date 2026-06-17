---
name: tailwind-ui-design-system
description: Use when designing or building a Tailwind UI interface. Always applies the complete Tailwind UI design tokens, typography, color system, and component conventions. Not for other aesthetics.
---

# Tailwind UI Design System

Apply the Tailwind UI aesthetic to any UI with frozen tokens and conventions.

## Design DNA
- **Typography**: Inter, application templates, Tailwind native
- **Color palette**: Tailwind palette, customizable
- **Best for**: SaaS, marketing, admin

## Token Layer (CSS variables)
Define semantic tokens that map to Tailwind UI primitives:
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

Apply Tailwind UI's actual values for each token based on the design DNA above.

## Component Conventions
- **Buttons**: follow Tailwind UI button styles (size, radius, padding, hover)
- **Inputs**: follow Tailwind UI input styles (border, focus ring, padding)
- **Cards**: follow Tailwind UI card styles (shadow, radius, padding)
- **Modals**: follow Tailwind UI modal styles (backdrop, animation, padding)
- **Tables**: follow Tailwind UI table styles (header, rows, hover, borders)
- **Typography**: follow Tailwind UI heading scale, body, captions

## Layout Principles
- Apply Tailwind UI's spacing rhythm (e.g., 4px / 8px / 16px / 24px / 32px)
- Apply Tailwind UI's container widths (e.g., max-w-7xl, max-w-4xl)
- Apply Tailwind UI's grid system
- Apply Tailwind UI's dark mode rules (if applicable)

## Animation
- Apply Tailwind UI's motion principles (duration, easing)
- Tailwind UI typically uses: 150ms ease-out for hover, 250ms for state changes

## Iconography
- Use the icon set that matches Tailwind UI (e.g., SF Symbols for Apple, Material Symbols for Material)
- Consistent stroke width / fill style

## Dark Mode
If Tailwind UI supports dark mode, define the dark token overrides:
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
- Don't mix Tailwind UI with other design systems in the same app

## Forbidden Patterns
- Mixing Tailwind UI tokens with another design system
- Overriding Tailwind UI tokens with raw values
- Using a different icon set than Tailwind UI prescribes
- Hard-coding Tailwind UI colors instead of using tokens

## Output Format
1. Token definitions (CSS variables)
2. Tailwind config (if applicable)
3. Example component using the system
4. Dark mode overrides

