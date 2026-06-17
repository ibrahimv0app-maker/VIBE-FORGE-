---
name: atlassian-design-system
description: Use when designing or building a Atlassian Design System interface. Always applies the complete Atlassian Design System design tokens, typography, color system, and component conventions. Not for other aesthetics.
---

# Atlassian Design System Design System

Apply the Atlassian Design System aesthetic to any UI with frozen tokens and conventions.

## Design DNA
- **Typography**: Charlie Sans, friendly, blue accent, rounded corners
- **Color palette**: #0052CC primary, neutral grays
- **Best for**: team collaboration, PM tools

## Token Layer (CSS variables)
Define semantic tokens that map to Atlassian Design System primitives:
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

Apply Atlassian Design System's actual values for each token based on the design DNA above.

## Component Conventions
- **Buttons**: follow Atlassian Design System button styles (size, radius, padding, hover)
- **Inputs**: follow Atlassian Design System input styles (border, focus ring, padding)
- **Cards**: follow Atlassian Design System card styles (shadow, radius, padding)
- **Modals**: follow Atlassian Design System modal styles (backdrop, animation, padding)
- **Tables**: follow Atlassian Design System table styles (header, rows, hover, borders)
- **Typography**: follow Atlassian Design System heading scale, body, captions

## Layout Principles
- Apply Atlassian Design System's spacing rhythm (e.g., 4px / 8px / 16px / 24px / 32px)
- Apply Atlassian Design System's container widths (e.g., max-w-7xl, max-w-4xl)
- Apply Atlassian Design System's grid system
- Apply Atlassian Design System's dark mode rules (if applicable)

## Animation
- Apply Atlassian Design System's motion principles (duration, easing)
- Atlassian Design System typically uses: 150ms ease-out for hover, 250ms for state changes

## Iconography
- Use the icon set that matches Atlassian Design System (e.g., SF Symbols for Apple, Material Symbols for Material)
- Consistent stroke width / fill style

## Dark Mode
If Atlassian Design System supports dark mode, define the dark token overrides:
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
- Don't mix Atlassian Design System with other design systems in the same app

## Forbidden Patterns
- Mixing Atlassian Design System tokens with another design system
- Overriding Atlassian Design System tokens with raw values
- Using a different icon set than Atlassian Design System prescribes
- Hard-coding Atlassian Design System colors instead of using tokens

## Output Format
1. Token definitions (CSS variables)
2. Tailwind config (if applicable)
3. Example component using the system
4. Dark mode overrides

