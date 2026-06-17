---
name: tailwind-design-system-builder
description: Use when setting up a Tailwind CSS design system — tokens, theme config, utility patterns, component classes. Always produces a scalable, themeable, dark-mode-ready foundation.
---

# Tailwind Design System Builder

A design system is not "a tailwind config". It's the contract between design and engineering.

## Token Layer (CSS variables in :root)
```css
:root {
  /* Color primitives */
  --color-primary-50: #eff6ff;
  --color-primary-500: #3b82f6;
  --color-primary-900: #1e3a8a;
  /* ... full 50-900 scale */

  /* Spacing scale (8px grid) */
  --space-1: 0.25rem;
  --space-2: 0.5rem;
  --space-3: 0.75rem;
  --space-4: 1rem;
  --space-6: 1.5rem;
  --space-8: 2rem;
  --space-12: 3rem;
  --space-16: 4rem;

  /* Typography */
  --font-sans: 'Inter', system-ui, sans-serif;
  --font-mono: 'JetBrains Mono', monospace;

  /* Radii */
  --radius-sm: 4px;
  --radius-md: 8px;
  --radius-lg: 12px;
  --radius-full: 9999px;

  /* Shadows */
  --shadow-sm: 0 1px 2px rgba(0,0,0,0.05);
  --shadow-md: 0 4px 6px rgba(0,0,0,0.1);

  /* Transitions */
  --ease-out: cubic-bezier(0.16, 1, 0.3, 1);
  --duration-fast: 150ms;
  --duration-normal: 250ms;
}
```

## Tailwind Config (extends tokens)
```js
module.exports = {
  darkMode: 'class',
  theme: {
    extend: {
      colors: {
        primary: 'rgb(var(--color-primary) / <alpha-value>)',
        // semantic tokens
        background: 'var(--color-background)',
        foreground: 'var(--color-foreground)',
        muted: 'var(--color-muted)',
        accent: 'var(--color-accent)',
      },
      fontFamily: {
        sans: ['var(--font-sans)'],
        mono: ['var(--font-mono)'],
      },
      borderRadius: {
        sm: 'var(--radius-sm)',
        md: 'var(--radius-md)',
      },
    },
  },
}
```

## Semantic Token Rule
- NEVER use raw color tokens (`bg-blue-500`) directly in components
- ALWAYS use semantic tokens (`bg-primary`, `bg-background`, `text-foreground`)
- This makes theming, dark mode, and white-labeling trivial

## Dark Mode Strategy
```css
:root { --color-background: #ffffff; --color-foreground: #0a0a0a; }
.dark { --color-background: #0a0a0a; --color-foreground: #fafafa; }
```
Components reference semantic tokens — dark mode "just works".

## Component Class Pattern (CVA)
```ts
const button = cva('inline-flex items-center justify-center font-medium transition-colors', {
  variants: {
    variant: {
      primary: 'bg-primary text-primary-foreground hover:bg-primary/90',
      secondary: 'bg-muted text-foreground hover:bg-muted/80',
    },
    size: {
      sm: 'h-8 px-3 text-sm',
      md: 'h-10 px-4',
      lg: 'h-12 px-6 text-lg',
    },
  },
})
```

## Spacing Rules
- 8px grid for everything (4px, 8px, 12px, 16px, 24px, 32px, 48px, 64px)
- Component padding: 16-24px standard
- Section gaps: 64-96px on desktop, 32-48px on mobile
- Never use arbitrary values (`p-[13px]`) — use the scale

## Forbidden Patterns
- Raw color utilities in components
- Arbitrary values for spacing
- Inline styles
- Tailwind classes without a token reference
- Mixing design systems (don't pull in Material UI colors)

## Output Format
1. Token layer (CSS variables)
2. Tailwind config
3. Semantic token list
4. Example component using the system

