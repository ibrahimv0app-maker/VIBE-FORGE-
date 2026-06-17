---
name: angular-chart-pie
description: Use when building a pie / donut chart in Angular 17+. Always uses use Angular signals, standalone components, and RxJS and follows Angular 17+ best practices for accessibility, performance, and composition.
---

# Angular 17+ Chart Pie Component

Build a production-grade pie / donut chart in Angular 17+.

## Requirements
- use Angular signals, standalone components, and RxJS
- Features: label positioning, hover highlight, legend
- Fully accessible (WCAG 2.1 AA)
- Keyboard navigable
- Themeable via design tokens (no hard-coded colors)
- Composable (consumers can override anything via props/slots)

## Component Anatomy
1. Root container with proper ARIA role
2. Trigger / activator element
3. Content / panel element
4. State management (internal, with controlled option)
5. Event handlers (click, keyboard, focus, blur)
6. Cleanup on unmount

## Accessibility
- Correct ARIA role for the chart-pie
- Keyboard support: Tab to focus, Arrow keys to navigate, Enter/Space to activate, Escape to dismiss
- `aria-expanded`, `aria-controls`, `aria-labelledby`, `aria-describedby` as appropriate
- Focus management: trap focus in modals/menus, restore focus on close
- Screen reader announcements for state changes

## Angular 17+ Patterns
- Use Angular 17+ idioms (not React patterns ported)
- Forward refs / expose API for parent control
- Accept className/`class` prop for styling extension
- Spread `...rest` props onto the root element
- Use the framework's transition system for animations

## Variants
- Size: sm / md / lg
- Variant: default / outline / ghost (as applicable)
- State: default / hover / focus / active / disabled / error

## Code Template
Implement the component using:
- Angular 17+ state primitives
- Composition over configuration
- Props for customization, slots for content
- Typescript / typed props

## Test Cases
- Renders with required props
- Renders all variants
- Keyboard interaction works
- State updates correctly
- Calls event handlers
- Accessible (axe-core passes)

## Forbidden Patterns
- Inline styles for themeable values
- Hard-coded text (accept via slot/children)
- DOM manipulation outside the framework
- Missing keyboard support
- Missing ARIA attributes
- Default exports (use named exports)

## Output Format
1. Component code
2. Types (props interface)
3. Usage example (3 variants)
4. Accessibility checklist
5. Test cases

