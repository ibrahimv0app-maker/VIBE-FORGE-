---
name: c-best-practices
description: Use when writing C23 code. Always follows C23 idioms, style guide, type system, and best practices: static analysis, _Generic, thread-local, memory safety.
---

# C23 Best Practices

Write idiomatic, production-grade C23.

## Style Guide
- Follow the official C23 style guide
- Use a formatter: static analysis, _Generic, thread-local, memory safety
- Use a linter with strict rules
- Code should pass CI without warnings

## Type System (if applicable)
- Use C23's type system to its fullest: static analysis, _Generic, thread-local, memory safety
- Prefer types over comments
- Make invalid states unrepresentable
- Use discriminated unions for closed sets
- Avoid `any` / dynamic where possible

## Error Handling
- Follow C23's idiom (exceptions, Result, Either, etc.)
- Handle errors at the appropriate level
- Don't swallow errors silently
- Provide context with errors

## Concurrency
- Use C23's native concurrency primitive
- Avoid shared mutable state
- Prefer message passing where possible
- Always propagate cancellation

## Project Structure
```
src/
├── ... (idiomatic layout)
```

## Testing
- Use C23's standard test framework
- One test file per source file
- Test behavior, not implementation
- Aim for 70-80% coverage

## Common Pitfalls (specific to C23)
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
1. The C23 code
2. Type annotations (if applicable)
3. Tests
4. Notes on idiomatic choices made

