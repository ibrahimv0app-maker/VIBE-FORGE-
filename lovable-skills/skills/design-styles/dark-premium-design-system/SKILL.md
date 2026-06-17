---
name: dark-premium-design-system
description: Use when designing or building a Dark Premium interface. Always applies the complete Dark Premium design tokens, typography, color system, and component conventions. Not for other aesthetics.
---

# Dark Premium Design System

Apply the Dark Premium aesthetic to any UI with frozen tokens and conventions.

## Design DNA
- **Typography**: Inter, near-black backgrounds, gold accents, fine serif headlines
- **Color palette**: #0A0A0A bg, #D4AF37 accent
- **Best for**: luxury, premium SaaS

## Token Layer (CSS variables)
Define semantic tokens that map to Dark Premium primitives:
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

Apply Dark Premium's actual values for each token based on the design DNA above.

## Component Conventions
- **Buttons**: follow Dark Premium button styles (size, radius, padding, hover)
- **Inputs**: follow Dark Premium input styles (border, focus ring, padding)
- **Cards**: follow Dark Premium card styles (shadow, radius, padding)
- **Modals**: follow Dark Premium modal styles (backdrop, animation, padding)
- **Tables**: follow Dark Premium table styles (header, rows, hover, borders)
- **Typography**: follow Dark Premium heading scale, body, captions

## Layout Principles
- Apply Dark Premium's spacing rhythm (e.g., 4px / 8px / 16px / 24px / 32px)
- Apply Dark Premium's container widths (e.g., max-w-7xl, max-w-4xl)
- Apply Dark Premium's grid system
- Apply Dark Premium's dark mode rules (if applicable)

## Animation
- Apply Dark Premium's motion principles (duration, easing)
- Dark Premium typically uses: 150ms ease-out for hover, 250ms for state changes

## Iconography
- Use the icon set that matches Dark Premium (e.g., SF Symbols for Apple, Material Symbols for Material)
- Consistent stroke width / fill style

## Dark Mode
If Dark Premium supports dark mode, define the dark token overrides:
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
- Don't mix Dark Premium with other design systems in the same app

## Forbidden Patterns
- Mixing Dark Premium tokens with another design system
- Overriding Dark Premium tokens with raw values
- Using a different icon set than Dark Premium prescribes
- Hard-coding Dark Premium colors instead of using tokens

## Output Format
1. Token definitions (CSS variables)
2. Tailwind config (if applicable)
3. Example component using the system
4. Dark mode overrides

