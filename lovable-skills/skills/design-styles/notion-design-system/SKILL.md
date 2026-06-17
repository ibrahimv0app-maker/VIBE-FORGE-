---
name: notion-design-system
description: Use when designing or building a Notion interface. Always applies the complete Notion design tokens, typography, color system, and component conventions. Not for other aesthetics.
---

# Notion Design System

Apply the Notion aesthetic to any UI with frozen tokens and conventions.

## Design DNA
- **Typography**: Lyon, system stack, minimal chrome, paper-like, soft borders, emoji as iconography
- **Color palette**: near-black on white, subtle warm grays
- **Best for**: productivity, docs

## Token Layer (CSS variables)
Define semantic tokens that map to Notion primitives:
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

Apply Notion's actual values for each token based on the design DNA above.

## Component Conventions
- **Buttons**: follow Notion button styles (size, radius, padding, hover)
- **Inputs**: follow Notion input styles (border, focus ring, padding)
- **Cards**: follow Notion card styles (shadow, radius, padding)
- **Modals**: follow Notion modal styles (backdrop, animation, padding)
- **Tables**: follow Notion table styles (header, rows, hover, borders)
- **Typography**: follow Notion heading scale, body, captions

## Layout Principles
- Apply Notion's spacing rhythm (e.g., 4px / 8px / 16px / 24px / 32px)
- Apply Notion's container widths (e.g., max-w-7xl, max-w-4xl)
- Apply Notion's grid system
- Apply Notion's dark mode rules (if applicable)

## Animation
- Apply Notion's motion principles (duration, easing)
- Notion typically uses: 150ms ease-out for hover, 250ms for state changes

## Iconography
- Use the icon set that matches Notion (e.g., SF Symbols for Apple, Material Symbols for Material)
- Consistent stroke width / fill style

## Dark Mode
If Notion supports dark mode, define the dark token overrides:
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
- Don't mix Notion with other design systems in the same app

## Forbidden Patterns
- Mixing Notion tokens with another design system
- Overriding Notion tokens with raw values
- Using a different icon set than Notion prescribes
- Hard-coding Notion colors instead of using tokens

## Output Format
1. Token definitions (CSS variables)
2. Tailwind config (if applicable)
3. Example component using the system
4. Dark mode overrides

