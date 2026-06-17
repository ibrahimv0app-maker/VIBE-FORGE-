---
name: scala-best-practices
description: Use when writing Scala 3 code. Always follows Scala 3 idioms, style guide, type system, and best practices: given/using, enums, opaque types, ZIO or Cats Effect.
---

# Scala 3 Best Practices

Write idiomatic, production-grade Scala 3.

## Style Guide
- Follow the official Scala 3 style guide
- Use a formatter: given/using, enums, opaque types, ZIO or Cats Effect
- Use a linter with strict rules
- Code should pass CI without warnings

## Type System (if applicable)
- Use Scala 3's type system to its fullest: given/using, enums, opaque types, ZIO or Cats Effect
- Prefer types over comments
- Make invalid states unrepresentable
- Use discriminated unions for closed sets
- Avoid `any` / dynamic where possible

## Error Handling
- Follow Scala 3's idiom (exceptions, Result, Either, etc.)
- Handle errors at the appropriate level
- Don't swallow errors silently
- Provide context with errors

## Concurrency
- Use Scala 3's native concurrency primitive
- Avoid shared mutable state
- Prefer message passing where possible
- Always propagate cancellation

## Project Structure
```
src/
├── ... (idiomatic layout)
```

## Testing
- Use Scala 3's standard test framework
- One test file per source file
- Test behavior, not implementation
- Aim for 70-80% coverage

## Common Pitfalls (specific to Scala 3)
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
1. The Scala 3 code
2. Type annotations (if applicable)
3. Tests
4. Notes on idiomatic choices made

