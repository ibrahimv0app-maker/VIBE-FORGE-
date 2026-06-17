---
name: ui-design-system-architect
description: Use when designing UI systems — color, typography, spacing, shadows, motion. Always produces a token-based system that scales from a single source of truth.
---

# UI Design System Architect

A design system is a contract. Tokens → components → patterns → screens.

## Token Hierarchy
1. **Primitive tokens**: raw values (`blue-500: #3b82f6`)
2. **Semantic tokens**: meaning-based (`primary: blue-500`, `background: white`)
3. **Component tokens**: scoped (`button-primary-bg: primary`)

Components reference semantic tokens. Semantic tokens reference primitives. Changing primitives flows through everything.

## Color System
```css
:root {
  /* Primitive palette (50-900) */
  --blue-50: #eff6ff;
  --blue-100: #dbeafe;
  --blue-500: #3b82f6;
  --blue-900: #1e3a8a;

  /* Semantic tokens */
  --color-primary: var(--blue-500);
  --color-primary-hover: var(--blue-600);
  --color-primary-foreground: white;

  --color-background: white;
  --color-foreground: #0a0a0a;
  --color-muted: #f4f4f5;
  --color-muted-foreground: #71717a;
  --color-border: #e4e4e7;

  --color-success: #10b981;
  --color-warning: #f59e0b;
  --color-error: #ef4444;
  --color-info: #3b82f6;
}

.dark {
  --color-background: #0a0a0a;
  --color-foreground: #fafafa;
  --color-muted: #18181b;
  --color-muted-foreground: #a1a1aa;
  --color-border: #27272a;
}
```

## Accessibility
- Text contrast: ≥ 4.5:1 (normal text), ≥ 3:1 (large text)
- UI contrast: ≥ 3:1
- Don't rely on color alone (add icons / text for state)
- Test with `aria-disabled`, not just opacity

## Typography Scale
```css
--font-sans: 'Inter', system-ui, sans-serif;
--font-serif: 'Source Serif Pro', Georgia, serif;
--font-mono: 'JetBrains Mono', monospace;

/* Modular scale (1.25 ratio) */
--text-xs: 0.64rem;     /* 10px */
--text-sm: 0.8rem;      /* 13px */
--text-base: 1rem;      /* 16px */
--text-lg: 1.25rem;     /* 20px */
--text-xl: 1.563rem;    /* 25px */
--text-2xl: 1.953rem;   /* 31px */
--text-3xl: 2.441rem;   /* 39px */
--text-4xl: 3.052rem;   /* 49px */

/* Line heights */
--leading-tight: 1.2;
--leading-normal: 1.5;
--leading-relaxed: 1.75;

/* Font weights */
--font-regular: 400;
--font-medium: 500;
--font-semibold: 600;
--font-bold: 700;
```

## Spacing Scale (8px grid)
```css
--space-0: 0;
--space-1: 0.25rem;   /* 4px */
--space-2: 0.5rem;    /* 8px */
--space-3: 0.75rem;   /* 12px */
--space-4: 1rem;      /* 16px */
--space-6: 1.5rem;    /* 24px */
--space-8: 2rem;      /* 32px */
--space-12: 3rem;     /* 48px */
--space-16: 4rem;     /* 64px */
--space-24: 6rem;     /* 96px */
```

## Border Radius
```css
--radius-none: 0;
--radius-sm: 0.25rem;   /* 4px */
--radius-md: 0.375rem;  /* 6px */
--radius-lg: 0.5rem;    /* 8px */
--radius-xl: 0.75rem;   /* 12px */
--radius-2xl: 1rem;     /* 16px */
--radius-full: 9999px;
```

## Shadows
```css
--shadow-xs: 0 1px 2px rgba(0,0,0,0.05);
--shadow-sm: 0 1px 3px rgba(0,0,0,0.1), 0 1px 2px rgba(0,0,0,0.06);
--shadow-md: 0 4px 6px rgba(0,0,0,0.1), 0 2px 4px rgba(0,0,0,0.06);
--shadow-lg: 0 10px 15px rgba(0,0,0,0.1), 0 4px 6px rgba(0,0,0,0.05);
--shadow-xl: 0 20px 25px rgba(0,0,0,0.1), 0 10px 10px rgba(0,0,0,0.04);
```

## Motion
```css
--duration-fast: 150ms;
--duration-normal: 250ms;
--duration-slow: 400ms;

--ease-out: cubic-bezier(0.16, 1, 0.3, 1);
--ease-in: cubic-bezier(0.7, 0, 0.84, 0);
--ease-in-out: cubic-bezier(0.65, 0, 0.35, 1);
--ease-spring: cubic-bezier(0.34, 1.56, 0.64, 1);
```

## Z-Index Scale
```css
--z-base: 0;
--z-dropdown: 1000;
--z-sticky: 1100;
--z-overlay: 1200;
--z-modal: 1300;
--z-popover: 1400;
--z-toast: 1500;
--z-tooltip: 1600;
```

## Component Patterns
```css
/* Button */
.btn {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  gap: var(--space-2);
  padding: 0 var(--space-4);
  height: 2.5rem;
  border-radius: var(--radius-md);
  font-weight: var(--font-medium);
  transition: background var(--duration-fast) var(--ease-out);
}
.btn-primary {
  background: var(--color-primary);
  color: var(--color-primary-foreground);
}
.btn-primary:hover {
  background: var(--color-primary-hover);
}
```

## Design System Documentation
Each token category needs:
- The token list (name + value)
- Usage guidelines (when to use)
- Anti-patterns (when NOT to use)
- Visual examples

## Forbidden Patterns
- Raw color values in components (`color: #3b82f6`)
- Inconsistent spacing (use the scale, not arbitrary values)
- Multiple shadow systems
- More than 4 font weights loaded
- Z-index wars (use the scale)

## Output Format
1. Token definitions (CSS)
2. Tailwind config (if applicable)
3. Component examples
4. Documentation structure

