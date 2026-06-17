---
name: kotlin-best-practices
description: Use when writing Kotlin code. Always follows Kotlin idioms, style guide, type system, and best practices: coroutines, sealed classes, data classes, null safety.
---

# Kotlin Best Practices

Write idiomatic, production-grade Kotlin.

## Style Guide
- Follow the official Kotlin style guide
- Use a formatter: coroutines, sealed classes, data classes, null safety
- Use a linter with strict rules
- Code should pass CI without warnings

## Type System (if applicable)
- Use Kotlin's type system to its fullest: coroutines, sealed classes, data classes, null safety
- Prefer types over comments
- Make invalid states unrepresentable
- Use discriminated unions for closed sets
- Avoid `any` / dynamic where possible

## Error Handling
- Follow Kotlin's idiom (exceptions, Result, Either, etc.)
- Handle errors at the appropriate level
- Don't swallow errors silently
- Provide context with errors

## Concurrency
- Use Kotlin's native concurrency primitive
- Avoid shared mutable state
- Prefer message passing where possible
- Always propagate cancellation

## Project Structure
```
src/
├── ... (idiomatic layout)
```

## Testing
- Use Kotlin's standard test framework
- One test file per source file
- Test behavior, not implementation
- Aim for 70-80% coverage

## Common Pitfalls (specific to Kotlin)
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
1. The Kotlin code
2. Type annotations (if applicable)
3. Tests
4. Notes on idiomatic choices made

