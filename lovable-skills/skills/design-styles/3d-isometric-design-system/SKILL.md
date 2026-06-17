---
name: 3d-isometric-design-system
description: Use when designing or building a 3D Isometric UI interface. Always applies the complete 3D Isometric UI design tokens, typography, color system, and component conventions. Not for other aesthetics.
---

# 3D Isometric UI Design System

Apply the 3D Isometric UI aesthetic to any UI with frozen tokens and conventions.

## Design DNA
- **Typography**: system sans, isometric illustrations, soft shadows, pastel palette
- **Color palette**: pastels + one accent
- **Best for**: marketing, landing pages

## Token Layer (CSS variables)
Define semantic tokens that map to 3D Isometric UI primitives:
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

Apply 3D Isometric UI's actual values for each token based on the design DNA above.

## Component Conventions
- **Buttons**: follow 3D Isometric UI button styles (size, radius, padding, hover)
- **Inputs**: follow 3D Isometric UI input styles (border, focus ring, padding)
- **Cards**: follow 3D Isometric UI card styles (shadow, radius, padding)
- **Modals**: follow 3D Isometric UI modal styles (backdrop, animation, padding)
- **Tables**: follow 3D Isometric UI table styles (header, rows, hover, borders)
- **Typography**: follow 3D Isometric UI heading scale, body, captions

## Layout Principles
- Apply 3D Isometric UI's spacing rhythm (e.g., 4px / 8px / 16px / 24px / 32px)
- Apply 3D Isometric UI's container widths (e.g., max-w-7xl, max-w-4xl)
- Apply 3D Isometric UI's grid system
- Apply 3D Isometric UI's dark mode rules (if applicable)

## Animation
- Apply 3D Isometric UI's motion principles (duration, easing)
- 3D Isometric UI typically uses: 150ms ease-out for hover, 250ms for state changes

## Iconography
- Use the icon set that matches 3D Isometric UI (e.g., SF Symbols for Apple, Material Symbols for Material)
- Consistent stroke width / fill style

## Dark Mode
If 3D Isometric UI supports dark mode, define the dark token overrides:
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
- Don't mix 3D Isometric UI with other design systems in the same app

## Forbidden Patterns
- Mixing 3D Isometric UI tokens with another design system
- Overriding 3D Isometric UI tokens with raw values
- Using a different icon set than 3D Isometric UI prescribes
- Hard-coding 3D Isometric UI colors instead of using tokens

## Output Format
1. Token definitions (CSS variables)
2. Tailwind config (if applicable)
3. Example component using the system
4. Dark mode overrides

