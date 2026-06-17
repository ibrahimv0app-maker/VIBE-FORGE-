---
name: aol-90s-design-system
description: Use when designing or building a 90s Web Revival interface. Always applies the complete 90s Web Revival design tokens, typography, color system, and component conventions. Not for other aesthetics.
---

# 90s Web Revival Design System

Apply the 90s Web Revival aesthetic to any UI with frozen tokens and conventions.

## Design DNA
- **Typography**: Times New Roman, table layouts, primary colors, animated GIFs
- **Color palette**: pure RGB primaries, gray backgrounds
- **Best for**: retro, art projects

## Token Layer (CSS variables)
Define semantic tokens that map to 90s Web Revival primitives:
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

Apply 90s Web Revival's actual values for each token based on the design DNA above.

## Component Conventions
- **Buttons**: follow 90s Web Revival button styles (size, radius, padding, hover)
- **Inputs**: follow 90s Web Revival input styles (border, focus ring, padding)
- **Cards**: follow 90s Web Revival card styles (shadow, radius, padding)
- **Modals**: follow 90s Web Revival modal styles (backdrop, animation, padding)
- **Tables**: follow 90s Web Revival table styles (header, rows, hover, borders)
- **Typography**: follow 90s Web Revival heading scale, body, captions

## Layout Principles
- Apply 90s Web Revival's spacing rhythm (e.g., 4px / 8px / 16px / 24px / 32px)
- Apply 90s Web Revival's container widths (e.g., max-w-7xl, max-w-4xl)
- Apply 90s Web Revival's grid system
- Apply 90s Web Revival's dark mode rules (if applicable)

## Animation
- Apply 90s Web Revival's motion principles (duration, easing)
- 90s Web Revival typically uses: 150ms ease-out for hover, 250ms for state changes

## Iconography
- Use the icon set that matches 90s Web Revival (e.g., SF Symbols for Apple, Material Symbols for Material)
- Consistent stroke width / fill style

## Dark Mode
If 90s Web Revival supports dark mode, define the dark token overrides:
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
- Don't mix 90s Web Revival with other design systems in the same app

## Forbidden Patterns
- Mixing 90s Web Revival tokens with another design system
- Overriding 90s Web Revival tokens with raw values
- Using a different icon set than 90s Web Revival prescribes
- Hard-coding 90s Web Revival colors instead of using tokens

## Output Format
1. Token definitions (CSS variables)
2. Tailwind config (if applicable)
3. Example component using the system
4. Dark mode overrides

