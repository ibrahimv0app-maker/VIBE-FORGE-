---
name: shopify-polaris-design-system
description: Use when designing or building a Shopify Polaris interface. Always applies the complete Shopify Polaris design tokens, typography, color system, and component conventions. Not for other aesthetics.
---

# Shopify Polaris Design System

Apply the Shopify Polaris aesthetic to any UI with frozen tokens and conventions.

## Design DNA
- **Typography**: Inter, multi-tenant, green accent, table-heavy, conservative
- **Color palette**: #008060 primary, neutral grays
- **Best for**: e-commerce admin, B2B

## Token Layer (CSS variables)
Define semantic tokens that map to Shopify Polaris primitives:
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

Apply Shopify Polaris's actual values for each token based on the design DNA above.

## Component Conventions
- **Buttons**: follow Shopify Polaris button styles (size, radius, padding, hover)
- **Inputs**: follow Shopify Polaris input styles (border, focus ring, padding)
- **Cards**: follow Shopify Polaris card styles (shadow, radius, padding)
- **Modals**: follow Shopify Polaris modal styles (backdrop, animation, padding)
- **Tables**: follow Shopify Polaris table styles (header, rows, hover, borders)
- **Typography**: follow Shopify Polaris heading scale, body, captions

## Layout Principles
- Apply Shopify Polaris's spacing rhythm (e.g., 4px / 8px / 16px / 24px / 32px)
- Apply Shopify Polaris's container widths (e.g., max-w-7xl, max-w-4xl)
- Apply Shopify Polaris's grid system
- Apply Shopify Polaris's dark mode rules (if applicable)

## Animation
- Apply Shopify Polaris's motion principles (duration, easing)
- Shopify Polaris typically uses: 150ms ease-out for hover, 250ms for state changes

## Iconography
- Use the icon set that matches Shopify Polaris (e.g., SF Symbols for Apple, Material Symbols for Material)
- Consistent stroke width / fill style

## Dark Mode
If Shopify Polaris supports dark mode, define the dark token overrides:
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
- Don't mix Shopify Polaris with other design systems in the same app

## Forbidden Patterns
- Mixing Shopify Polaris tokens with another design system
- Overriding Shopify Polaris tokens with raw values
- Using a different icon set than Shopify Polaris prescribes
- Hard-coding Shopify Polaris colors instead of using tokens

## Output Format
1. Token definitions (CSS variables)
2. Tailwind config (if applicable)
3. Example component using the system
4. Dark mode overrides

