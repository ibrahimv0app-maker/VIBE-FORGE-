---
name: react-component-architect
description: Use when creating React components — buttons, cards, forms, modals, complex layouts. Always produces accessible, reusable, type-safe components with proper composition patterns.
---

# React Component Architect

Every React component you write must be: accessible, reusable, type-safe, performant, and composable.

## Component Anatomy
```tsx
// 1. Imports (typed, organized)
import { forwardRef, ReactNode } from 'react'
import { cva, VariantProps } from 'class-variance-authority'

// 2. Variant definitions (CVA pattern)
const buttonVariants = cva('base classes', {
  variants: {
    variant: { primary: '...', secondary: '...', ghost: '...' },
    size: { sm: '...', md: '...', lg: '...' },
  },
  defaultVariants: { variant: 'primary', size: 'md' },
})

// 3. Props interface (extends native HTML props)
export interface ButtonProps
  extends React.ButtonHTMLAttributes<HTMLButtonElement>,
    VariantProps<typeof buttonVariants> {
  isLoading?: boolean
  leftIcon?: ReactNode
  rightIcon?: ReactNode
}

// 4. Component (forwardRef for ref forwarding)
export const Button = forwardRef<HTMLButtonElement, ButtonProps>(
  ({ className, variant, size, isLoading, leftIcon, rightIcon, children, disabled, ...props }, ref) => {
    return (
      <button
        ref={ref}
        className={cn(buttonVariants({ variant, size, className }))}
        disabled={disabled || isLoading}
        aria-busy={isLoading}
        {...props}
      >
        {isLoading && <Spinner className="mr-2" />}
        {!isLoading && leftIcon && <span className="mr-2">{leftIcon}</span>}
        {children}
        {!isLoading && rightIcon && <span className="ml-2">{rightIcon}</span>}
      </button>
    )
  }
)
Button.displayName = 'Button'
```

## Rules
1. **Always forwardRef** — consumers need ref access
2. **Always extend native HTML props** — don't reinvent `onClick`, `disabled`, etc.
3. **Always use CVA or equivalent** for variant management
4. **Always spread `...props` last** — consumers can override anything
5. **Always set `displayName`** for React DevTools
6. **Always handle loading and disabled states**
7. **Always include aria attributes** (aria-busy, aria-disabled, aria-expanded, etc.)
8. **Never use `any`** — type everything explicitly
9. **Never inline styles** unless dynamic values are required
10. **Never hardcode text** — accept children for flexible composition

## Accessibility Checklist
- [ ] Keyboard accessible (works with Tab + Enter/Space)
- [ ] Focus visible (focus ring)
- [ ] ARIA attributes for state (aria-busy, aria-expanded, aria-disabled)
- [ ] Semantic HTML (button, not div with onClick)
- [ ] Screen reader friendly (sr-only labels when needed)
- [ ] Color contrast ≥ 4.5:1 for text, 3:1 for UI

## Composition Patterns
- **Compound components**: `<Tabs><TabsList><TabsTrigger/></TabsList><TabsContent/></Tabs>` for complex widgets
- **Render props / function-as-child**: for flexible rendering
- **Slot pattern**: for inserting content into specific positions
- **Polymorphic `as` prop**: only when necessary (most cases don't need it)

## File Structure
```
Button/
├── Button.tsx          # component
├── Button.test.tsx     # tests
├── Button.stories.tsx  # stories
└── index.ts            # export
```

## Forbidden Patterns
- `div` with `onClick` (use `button`)
- Inline arrow functions in prop lists without `useCallback`
- `useState` for derived values (use `useMemo`)
- Prop drilling more than 2 levels (use Context)
- Default exports for components (named exports only)

## Output Format
1. The component code
2. Usage example
3. Accessibility checklist result
4. Test cases to write

