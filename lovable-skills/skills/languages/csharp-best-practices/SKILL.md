---
name: csharp-best-practices
description: Use when writing C# 12 code. Always follows C# 12 idioms, style guide, type system, and best practices: LINQ, async/await, records, pattern matching.
---

# C# 12 Best Practices

Write idiomatic, production-grade C# 12.

## Style Guide
- Follow the official C# 12 style guide
- Use a formatter: LINQ, async/await, records, pattern matching
- Use a linter with strict rules
- Code should pass CI without warnings

## Type System (if applicable)
- Use C# 12's type system to its fullest: LINQ, async/await, records, pattern matching
- Prefer types over comments
- Make invalid states unrepresentable
- Use discriminated unions for closed sets
- Avoid `any` / dynamic where possible

## Error Handling
- Follow C# 12's idiom (exceptions, Result, Either, etc.)
- Handle errors at the appropriate level
- Don't swallow errors silently
- Provide context with errors

## Concurrency
- Use C# 12's native concurrency primitive
- Avoid shared mutable state
- Prefer message passing where possible
- Always propagate cancellation

## Project Structure
```
src/
├── ... (idiomatic layout)
```

## Testing
- Use C# 12's standard test framework
- One test file per source file
- Test behavior, not implementation
- Aim for 70-80% coverage

## Common Pitfalls (specific to C# 12)
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
1. The C# 12 code
2. Type annotations (if applicable)
3. Tests
4. Notes on idiomatic choices made

