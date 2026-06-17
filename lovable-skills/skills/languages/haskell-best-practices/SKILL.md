---
name: haskell-best-practices
description: Use when writing Haskell code. Always follows Haskell idioms, style guide, type system, and best practices: purity, monads, type classes, lazy evaluation.
---

# Haskell Best Practices

Write idiomatic, production-grade Haskell.

## Style Guide
- Follow the official Haskell style guide
- Use a formatter: purity, monads, type classes, lazy evaluation
- Use a linter with strict rules
- Code should pass CI without warnings

## Type System (if applicable)
- Use Haskell's type system to its fullest: purity, monads, type classes, lazy evaluation
- Prefer types over comments
- Make invalid states unrepresentable
- Use discriminated unions for closed sets
- Avoid `any` / dynamic where possible

## Error Handling
- Follow Haskell's idiom (exceptions, Result, Either, etc.)
- Handle errors at the appropriate level
- Don't swallow errors silently
- Provide context with errors

## Concurrency
- Use Haskell's native concurrency primitive
- Avoid shared mutable state
- Prefer message passing where possible
- Always propagate cancellation

## Project Structure
```
src/
├── ... (idiomatic layout)
```

## Testing
- Use Haskell's standard test framework
- One test file per source file
- Test behavior, not implementation
- Aim for 70-80% coverage

## Common Pitfalls (specific to Haskell)
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
1. The Haskell code
2. Type annotations (if applicable)
3. Tests
4. Notes on idiomatic choices made

