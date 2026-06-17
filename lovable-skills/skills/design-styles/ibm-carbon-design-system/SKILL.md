---
name: ibm-carbon-design-system
description: Use when designing or building a IBM Carbon interface. Always applies the complete IBM Carbon design tokens, typography, color system, and component conventions. Not for other aesthetics.
---

# IBM Carbon Design System

Apply the IBM Carbon aesthetic to any UI with frozen tokens and conventions.

## Design DNA
- **Typography**: IBM Plex, dense, data-heavy, blue accent, structured grids
- **Color palette**: #0F62FE primary, cool grays
- **Best for**: enterprise, B2B dashboards

## Token Layer (CSS variables)
Define semantic tokens that map to IBM Carbon primitives:
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

Apply IBM Carbon's actual values for each token based on the design DNA above.

## Component Conventions
- **Buttons**: follow IBM Carbon button styles (size, radius, padding, hover)
- **Inputs**: follow IBM Carbon input styles (border, focus ring, padding)
- **Cards**: follow IBM Carbon card styles (shadow, radius, padding)
- **Modals**: follow IBM Carbon modal styles (backdrop, animation, padding)
- **Tables**: follow IBM Carbon table styles (header, rows, hover, borders)
- **Typography**: follow IBM Carbon heading scale, body, captions

## Layout Principles
- Apply IBM Carbon's spacing rhythm (e.g., 4px / 8px / 16px / 24px / 32px)
- Apply IBM Carbon's container widths (e.g., max-w-7xl, max-w-4xl)
- Apply IBM Carbon's grid system
- Apply IBM Carbon's dark mode rules (if applicable)

## Animation
- Apply IBM Carbon's motion principles (duration, easing)
- IBM Carbon typically uses: 150ms ease-out for hover, 250ms for state changes

## Iconography
- Use the icon set that matches IBM Carbon (e.g., SF Symbols for Apple, Material Symbols for Material)
- Consistent stroke width / fill style

## Dark Mode
If IBM Carbon supports dark mode, define the dark token overrides:
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
- Don't mix IBM Carbon with other design systems in the same app

## Forbidden Patterns
- Mixing IBM Carbon tokens with another design system
- Overriding IBM Carbon tokens with raw values
- Using a different icon set than IBM Carbon prescribes
- Hard-coding IBM Carbon colors instead of using tokens

## Output Format
1. Token definitions (CSS variables)
2. Tailwind config (if applicable)
3. Example component using the system
4. Dark mode overrides

