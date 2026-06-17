---
name: editorial-magazine-design-system
description: Use when designing or building a Editorial Magazine interface. Always applies the complete Editorial Magazine design tokens, typography, color system, and component conventions. Not for other aesthetics.
---

# Editorial Magazine Design System

Apply the Editorial Magazine aesthetic to any UI with frozen tokens and conventions.

## Design DNA
- **Typography**: Playfair / Tinos serif, grid layouts, generous whitespace, fine rules
- **Color palette**: near-black on cream + one accent
- **Best for**: media, publications

## Token Layer (CSS variables)
Define semantic tokens that map to Editorial Magazine primitives:
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

Apply Editorial Magazine's actual values for each token based on the design DNA above.

## Component Conventions
- **Buttons**: follow Editorial Magazine button styles (size, radius, padding, hover)
- **Inputs**: follow Editorial Magazine input styles (border, focus ring, padding)
- **Cards**: follow Editorial Magazine card styles (shadow, radius, padding)
- **Modals**: follow Editorial Magazine modal styles (backdrop, animation, padding)
- **Tables**: follow Editorial Magazine table styles (header, rows, hover, borders)
- **Typography**: follow Editorial Magazine heading scale, body, captions

## Layout Principles
- Apply Editorial Magazine's spacing rhythm (e.g., 4px / 8px / 16px / 24px / 32px)
- Apply Editorial Magazine's container widths (e.g., max-w-7xl, max-w-4xl)
- Apply Editorial Magazine's grid system
- Apply Editorial Magazine's dark mode rules (if applicable)

## Animation
- Apply Editorial Magazine's motion principles (duration, easing)
- Editorial Magazine typically uses: 150ms ease-out for hover, 250ms for state changes

## Iconography
- Use the icon set that matches Editorial Magazine (e.g., SF Symbols for Apple, Material Symbols for Material)
- Consistent stroke width / fill style

## Dark Mode
If Editorial Magazine supports dark mode, define the dark token overrides:
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
- Don't mix Editorial Magazine with other design systems in the same app

## Forbidden Patterns
- Mixing Editorial Magazine tokens with another design system
- Overriding Editorial Magazine tokens with raw values
- Using a different icon set than Editorial Magazine prescribes
- Hard-coding Editorial Magazine colors instead of using tokens

## Output Format
1. Token definitions (CSS variables)
2. Tailwind config (if applicable)
3. Example component using the system
4. Dark mode overrides

