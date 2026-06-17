---
name: apple-hig-design-system
description: Use when designing or building a Apple Human Interface Guidelines interface. Always applies the complete Apple Human Interface Guidelines design tokens, typography, color system, and component conventions. Not for other aesthetics.
---

# Apple Human Interface Guidelines Design System

Apply the Apple Human Interface Guidelines aesthetic to any UI with frozen tokens and conventions.

## Design DNA
- **Typography**: San Francisco fonts, blur materials, vibrancy, subtle shadows, generous whitespace, SF Symbols
- **Color palette**: system blue #007AFF, system gray, semantic colors
- **Best for**: iOS / macOS / visionOS apps

## Token Layer (CSS variables)
Define semantic tokens that map to Apple Human Interface Guidelines primitives:
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

Apply Apple Human Interface Guidelines's actual values for each token based on the design DNA above.

## Component Conventions
- **Buttons**: follow Apple Human Interface Guidelines button styles (size, radius, padding, hover)
- **Inputs**: follow Apple Human Interface Guidelines input styles (border, focus ring, padding)
- **Cards**: follow Apple Human Interface Guidelines card styles (shadow, radius, padding)
- **Modals**: follow Apple Human Interface Guidelines modal styles (backdrop, animation, padding)
- **Tables**: follow Apple Human Interface Guidelines table styles (header, rows, hover, borders)
- **Typography**: follow Apple Human Interface Guidelines heading scale, body, captions

## Layout Principles
- Apply Apple Human Interface Guidelines's spacing rhythm (e.g., 4px / 8px / 16px / 24px / 32px)
- Apply Apple Human Interface Guidelines's container widths (e.g., max-w-7xl, max-w-4xl)
- Apply Apple Human Interface Guidelines's grid system
- Apply Apple Human Interface Guidelines's dark mode rules (if applicable)

## Animation
- Apply Apple Human Interface Guidelines's motion principles (duration, easing)
- Apple Human Interface Guidelines typically uses: 150ms ease-out for hover, 250ms for state changes

## Iconography
- Use the icon set that matches Apple Human Interface Guidelines (e.g., SF Symbols for Apple, Material Symbols for Material)
- Consistent stroke width / fill style

## Dark Mode
If Apple Human Interface Guidelines supports dark mode, define the dark token overrides:
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
- Don't mix Apple Human Interface Guidelines with other design systems in the same app

## Forbidden Patterns
- Mixing Apple Human Interface Guidelines tokens with another design system
- Overriding Apple Human Interface Guidelines tokens with raw values
- Using a different icon set than Apple Human Interface Guidelines prescribes
- Hard-coding Apple Human Interface Guidelines colors instead of using tokens

## Output Format
1. Token definitions (CSS variables)
2. Tailwind config (if applicable)
3. Example component using the system
4. Dark mode overrides

