---
name: adobe-spectrum-design-system
description: Use when designing or building a Adobe Spectrum interface. Always applies the complete Adobe Spectrum design tokens, typography, color system, and component conventions. Not for other aesthetics.
---

# Adobe Spectrum Design System

Apply the Adobe Spectrum aesthetic to any UI with frozen tokens and conventions.

## Design DNA
- **Typography**: Adobe Clean, multi-app, dense, creative-tool aesthetic
- **Color palette**: #2680EB primary, neutral grays
- **Best for**: creative tools, media apps

## Token Layer (CSS variables)
Define semantic tokens that map to Adobe Spectrum primitives:
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

Apply Adobe Spectrum's actual values for each token based on the design DNA above.

## Component Conventions
- **Buttons**: follow Adobe Spectrum button styles (size, radius, padding, hover)
- **Inputs**: follow Adobe Spectrum input styles (border, focus ring, padding)
- **Cards**: follow Adobe Spectrum card styles (shadow, radius, padding)
- **Modals**: follow Adobe Spectrum modal styles (backdrop, animation, padding)
- **Tables**: follow Adobe Spectrum table styles (header, rows, hover, borders)
- **Typography**: follow Adobe Spectrum heading scale, body, captions

## Layout Principles
- Apply Adobe Spectrum's spacing rhythm (e.g., 4px / 8px / 16px / 24px / 32px)
- Apply Adobe Spectrum's container widths (e.g., max-w-7xl, max-w-4xl)
- Apply Adobe Spectrum's grid system
- Apply Adobe Spectrum's dark mode rules (if applicable)

## Animation
- Apply Adobe Spectrum's motion principles (duration, easing)
- Adobe Spectrum typically uses: 150ms ease-out for hover, 250ms for state changes

## Iconography
- Use the icon set that matches Adobe Spectrum (e.g., SF Symbols for Apple, Material Symbols for Material)
- Consistent stroke width / fill style

## Dark Mode
If Adobe Spectrum supports dark mode, define the dark token overrides:
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
- Don't mix Adobe Spectrum with other design systems in the same app

## Forbidden Patterns
- Mixing Adobe Spectrum tokens with another design system
- Overriding Adobe Spectrum tokens with raw values
- Using a different icon set than Adobe Spectrum prescribes
- Hard-coding Adobe Spectrum colors instead of using tokens

## Output Format
1. Token definitions (CSS variables)
2. Tailwind config (if applicable)
3. Example component using the system
4. Dark mode overrides

