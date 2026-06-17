---
name: java-best-practices
description: Use when writing Java 21 code. Always follows Java 21 idioms, style guide, type system, and best practices: records, sealed classes, pattern matching, virtual threads.
---

# Java 21 Best Practices

Write idiomatic, production-grade Java 21.

## Style Guide
- Follow the official Java 21 style guide
- Use a formatter: records, sealed classes, pattern matching, virtual threads
- Use a linter with strict rules
- Code should pass CI without warnings

## Type System (if applicable)
- Use Java 21's type system to its fullest: records, sealed classes, pattern matching, virtual threads
- Prefer types over comments
- Make invalid states unrepresentable
- Use discriminated unions for closed sets
- Avoid `any` / dynamic where possible

## Error Handling
- Follow Java 21's idiom (exceptions, Result, Either, etc.)
- Handle errors at the appropriate level
- Don't swallow errors silently
- Provide context with errors

## Concurrency
- Use Java 21's native concurrency primitive
- Avoid shared mutable state
- Prefer message passing where possible
- Always propagate cancellation

## Project Structure
```
src/
├── ... (idiomatic layout)
```

## Testing
- Use Java 21's standard test framework
- One test file per source file
- Test behavior, not implementation
- Aim for 70-80% coverage

## Common Pitfalls (specific to Java 21)
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
1. The Java 21 code
2. Type annotations (if applicable)
3. Tests
4. Notes on idiomatic choices made

