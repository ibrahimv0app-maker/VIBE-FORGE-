---
name: y2k-design-system
description: Use when designing or building a Y2K Aesthetic interface. Always applies the complete Y2K Aesthetic design tokens, typography, color system, and component conventions. Not for other aesthetics.
---

# Y2K Aesthetic Design System

Apply the Y2K Aesthetic aesthetic to any UI with frozen tokens and conventions.

## Design DNA
- **Typography**: system sans, chrome gradients, glossy buttons, sparkles, blob shapes
- **Color palette**: chrome silver + saturated accents
- **Best for**: retro, creative

## Token Layer (CSS variables)
Define semantic tokens that map to Y2K Aesthetic primitives:
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

Apply Y2K Aesthetic's actual values for each token based on the design DNA above.

## Component Conventions
- **Buttons**: follow Y2K Aesthetic button styles (size, radius, padding, hover)
- **Inputs**: follow Y2K Aesthetic input styles (border, focus ring, padding)
- **Cards**: follow Y2K Aesthetic card styles (shadow, radius, padding)
- **Modals**: follow Y2K Aesthetic modal styles (backdrop, animation, padding)
- **Tables**: follow Y2K Aesthetic table styles (header, rows, hover, borders)
- **Typography**: follow Y2K Aesthetic heading scale, body, captions

## Layout Principles
- Apply Y2K Aesthetic's spacing rhythm (e.g., 4px / 8px / 16px / 24px / 32px)
- Apply Y2K Aesthetic's container widths (e.g., max-w-7xl, max-w-4xl)
- Apply Y2K Aesthetic's grid system
- Apply Y2K Aesthetic's dark mode rules (if applicable)

## Animation
- Apply Y2K Aesthetic's motion principles (duration, easing)
- Y2K Aesthetic typically uses: 150ms ease-out for hover, 250ms for state changes

## Iconography
- Use the icon set that matches Y2K Aesthetic (e.g., SF Symbols for Apple, Material Symbols for Material)
- Consistent stroke width / fill style

## Dark Mode
If Y2K Aesthetic supports dark mode, define the dark token overrides:
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
- Don't mix Y2K Aesthetic with other design systems in the same app

## Forbidden Patterns
- Mixing Y2K Aesthetic tokens with another design system
- Overriding Y2K Aesthetic tokens with raw values
- Using a different icon set than Y2K Aesthetic prescribes
- Hard-coding Y2K Aesthetic colors instead of using tokens

## Output Format
1. Token definitions (CSS variables)
2. Tailwind config (if applicable)
3. Example component using the system
4. Dark mode overrides

