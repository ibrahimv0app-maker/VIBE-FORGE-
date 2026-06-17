---
name: css-grid-responsive
description: Use when implementing responsive grid without media queries. Always uses modern, accessible, browser-compatible CSS: auto-fit, minmax, repeat. Not for legacy browser support.
---

# CSS Technique: Grid Responsive

Responsive grid without media queries using auto-fit, minmax, repeat.

## Browser Support
- Chrome / Edge: latest 2 versions
- Firefox: latest 2 versions
- Safari: latest 2 versions
- Note any features requiring @supports fallback

## Implementation
Provide production-ready CSS with:
- Vendor prefixes (via Autoprefixer, not hand-written)
- Fallbacks for older browsers where critical
- Accessibility (focus states, reduced motion)
- RTL / logical properties where applicable
- Dark mode support where applicable

## HTML Structure
Show the minimum HTML needed for the technique.

## CSS Code
Show the complete CSS, well-commented.

## Usage Example
Show a real-world usage with surrounding context.

## Common Pitfalls
- Forgetting reduced motion
- Not handling RTL
- Missing focus states
- Layout shift on load

## Forbidden Patterns
- `!important` (use specificity instead)
- Inline styles
- Hard-coded values (use variables)
- JavaScript for what CSS can do

## Output Format
1. HTML structure
2. CSS code
3. Browser support notes
4. Accessibility considerations

