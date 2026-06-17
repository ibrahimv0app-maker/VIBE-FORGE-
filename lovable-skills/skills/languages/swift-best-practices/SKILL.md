---
name: swift-best-practices
description: Use when writing Swift 5.10 code. Always follows Swift 5.10 idioms, style guide, type system, and best practices: structured concurrency, actors, optionals, SwiftUI.
---

# Swift 5.10 Best Practices

Write idiomatic, production-grade Swift 5.10.

## Style Guide
- Follow the official Swift 5.10 style guide
- Use a formatter: structured concurrency, actors, optionals, SwiftUI
- Use a linter with strict rules
- Code should pass CI without warnings

## Type System (if applicable)
- Use Swift 5.10's type system to its fullest: structured concurrency, actors, optionals, SwiftUI
- Prefer types over comments
- Make invalid states unrepresentable
- Use discriminated unions for closed sets
- Avoid `any` / dynamic where possible

## Error Handling
- Follow Swift 5.10's idiom (exceptions, Result, Either, etc.)
- Handle errors at the appropriate level
- Don't swallow errors silently
- Provide context with errors

## Concurrency
- Use Swift 5.10's native concurrency primitive
- Avoid shared mutable state
- Prefer message passing where possible
- Always propagate cancellation

## Project Structure
```
src/
├── ... (idiomatic layout)
```

## Testing
- Use Swift 5.10's standard test framework
- One test file per source file
- Test behavior, not implementation
- Aim for 70-80% coverage

## Common Pitfalls (specific to Swift 5.10)
- Document the language-specific gotchas
- Reference the language's anti-pattern list

## Code Review Checklist
- [ ] Passes formatter and linter
- [ ] No `any` / dynamic escapes
- [ ] Errors handled explicitly
- [ ] No unused imports / variables
- [ ] Tests added for new behavior
- [ ] No premature optimization

## Output Format
1. The Swift 5.10 code
2. Type annotations (if applicable)
3. Tests
4. Notes on idiomatic choices made

