---
name: github-primer-design-system
description: Use when designing or building a GitHub Primer interface. Always applies the complete GitHub Primer design tokens, typography, color system, and component conventions. Not for other aesthetics.
---

# GitHub Primer Design System

Apply the GitHub Primer aesthetic to any UI with frozen tokens and conventions.

## Design DNA
- **Typography**: Mona Sans, dense, code-friendly, blue accent, subtle borders
- **Color palette**: #0969DA primary, neutral grays
- **Best for**: developer tools, code platforms

## Token Layer (CSS variables)
Define semantic tokens that map to GitHub Primer primitives:
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

Apply GitHub Primer's actual values for each token based on the design DNA above.

## Component Conventions
- **Buttons**: follow GitHub Primer button styles (size, radius, padding, hover)
- **Inputs**: follow GitHub Primer input styles (border, focus ring, padding)
- **Cards**: follow GitHub Primer card styles (shadow, radius, padding)
- **Modals**: follow GitHub Primer modal styles (backdrop, animation, padding)
- **Tables**: follow GitHub Primer table styles (header, rows, hover, borders)
- **Typography**: follow GitHub Primer heading scale, body, captions

## Layout Principles
- Apply GitHub Primer's spacing rhythm (e.g., 4px / 8px / 16px / 24px / 32px)
- Apply GitHub Primer's container widths (e.g., max-w-7xl, max-w-4xl)
- Apply GitHub Primer's grid system
- Apply GitHub Primer's dark mode rules (if applicable)

## Animation
- Apply GitHub Primer's motion principles (duration, easing)
- GitHub Primer typically uses: 150ms ease-out for hover, 250ms for state changes

## Iconography
- Use the icon set that matches GitHub Primer (e.g., SF Symbols for Apple, Material Symbols for Material)
- Consistent stroke width / fill style

## Dark Mode
If GitHub Primer supports dark mode, define the dark token overrides:
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
- Don't mix GitHub Primer with other design systems in the same app

## Forbidden Patterns
- Mixing GitHub Primer tokens with another design system
- Overriding GitHub Primer tokens with raw values
- Using a different icon set than GitHub Primer prescribes
- Hard-coding GitHub Primer colors instead of using tokens

## Output Format
1. Token definitions (CSS variables)
2. Tailwind config (if applicable)
3. Example component using the system
4. Dark mode overrides

