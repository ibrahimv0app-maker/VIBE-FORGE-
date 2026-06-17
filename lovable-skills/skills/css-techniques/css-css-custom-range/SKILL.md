---
name: css-css-custom-range
description: Use when implementing custom range slider. Always uses modern, accessible, browser-compatible CSS: appearance: none, ::-webkit-slider-thumb. Not for legacy browser support.
---

# CSS Technique: Css Custom Range

Custom range slider using appearance: none, ::-webkit-slider-thumb.

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

