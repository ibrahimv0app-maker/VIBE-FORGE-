---
name: vaporwave-ui-design-system
description: Use when designing or building a Vaporwave UI interface. Always applies the complete Vaporwave UI design tokens, typography, color system, and component conventions. Not for other aesthetics.
---

# Vaporwave UI Design System

Apply the Vaporwave UI aesthetic to any UI with frozen tokens and conventions.

## Design DNA
- **Typography**: system sans, pink/cyan gradients, grid floors, Greek statues
- **Color palette**: #FF71CE / #01CDFE / #B967FF
- **Best for**: creative, retro-futurism

## Token Layer (CSS variables)
Define semantic tokens that map to Vaporwave UI primitives:
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

Apply Vaporwave UI's actual values for each token based on the design DNA above.

## Component Conventions
- **Buttons**: follow Vaporwave UI button styles (size, radius, padding, hover)
- **Inputs**: follow Vaporwave UI input styles (border, focus ring, padding)
- **Cards**: follow Vaporwave UI card styles (shadow, radius, padding)
- **Modals**: follow Vaporwave UI modal styles (backdrop, animation, padding)
- **Tables**: follow Vaporwave UI table styles (header, rows, hover, borders)
- **Typography**: follow Vaporwave UI heading scale, body, captions

## Layout Principles
- Apply Vaporwave UI's spacing rhythm (e.g., 4px / 8px / 16px / 24px / 32px)
- Apply Vaporwave UI's container widths (e.g., max-w-7xl, max-w-4xl)
- Apply Vaporwave UI's grid system
- Apply Vaporwave UI's dark mode rules (if applicable)

## Animation
- Apply Vaporwave UI's motion principles (duration, easing)
- Vaporwave UI typically uses: 150ms ease-out for hover, 250ms for state changes

## Iconography
- Use the icon set that matches Vaporwave UI (e.g., SF Symbols for Apple, Material Symbols for Material)
- Consistent stroke width / fill style

## Dark Mode
If Vaporwave UI supports dark mode, define the dark token overrides:
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
- Don't mix Vaporwave UI with other design systems in the same app

## Forbidden Patterns
- Mixing Vaporwave UI tokens with another design system
- Overriding Vaporwave UI tokens with raw values
- Using a different icon set than Vaporwave UI prescribes
- Hard-coding Vaporwave UI colors instead of using tokens

## Output Format
1. Token definitions (CSS variables)
2. Tailwind config (if applicable)
3. Example component using the system
4. Dark mode overrides

