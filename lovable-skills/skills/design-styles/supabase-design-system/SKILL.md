---
name: supabase-design-system
description: Use when designing or building a Supabase interface. Always applies the complete Supabase design tokens, typography, color system, and component conventions. Not for other aesthetics.
---

# Supabase Design System

Apply the Supabase aesthetic to any UI with frozen tokens and conventions.

## Design DNA
- **Typography**: Inter, developer-focused, dark mode native, green accent
- **Color palette**: #3ECF8E primary, neutral grays
- **Best for**: developer tools, BaaS UIs

## Token Layer (CSS variables)
Define semantic tokens that map to Supabase primitives:
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

Apply Supabase's actual values for each token based on the design DNA above.

## Component Conventions
- **Buttons**: follow Supabase button styles (size, radius, padding, hover)
- **Inputs**: follow Supabase input styles (border, focus ring, padding)
- **Cards**: follow Supabase card styles (shadow, radius, padding)
- **Modals**: follow Supabase modal styles (backdrop, animation, padding)
- **Tables**: follow Supabase table styles (header, rows, hover, borders)
- **Typography**: follow Supabase heading scale, body, captions

## Layout Principles
- Apply Supabase's spacing rhythm (e.g., 4px / 8px / 16px / 24px / 32px)
- Apply Supabase's container widths (e.g., max-w-7xl, max-w-4xl)
- Apply Supabase's grid system
- Apply Supabase's dark mode rules (if applicable)

## Animation
- Apply Supabase's motion principles (duration, easing)
- Supabase typically uses: 150ms ease-out for hover, 250ms for state changes

## Iconography
- Use the icon set that matches Supabase (e.g., SF Symbols for Apple, Material Symbols for Material)
- Consistent stroke width / fill style

## Dark Mode
If Supabase supports dark mode, define the dark token overrides:
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
- Don't mix Supabase with other design systems in the same app

## Forbidden Patterns
- Mixing Supabase tokens with another design system
- Overriding Supabase tokens with raw values
- Using a different icon set than Supabase prescribes
- Hard-coding Supabase colors instead of using tokens

## Output Format
1. Token definitions (CSS variables)
2. Tailwind config (if applicable)
3. Example component using the system
4. Dark mode overrides

