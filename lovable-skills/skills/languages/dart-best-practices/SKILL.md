---
name: dart-best-practices
description: Use when writing Dart 3 code. Always follows Dart 3 idioms, style guide, type system, and best practices: null safety, sealed classes, async/await, Flutter.
---

# Dart 3 Best Practices

Write idiomatic, production-grade Dart 3.

## Style Guide
- Follow the official Dart 3 style guide
- Use a formatter: null safety, sealed classes, async/await, Flutter
- Use a linter with strict rules
- Code should pass CI without warnings

## Type System (if applicable)
- Use Dart 3's type system to its fullest: null safety, sealed classes, async/await, Flutter
- Prefer types over comments
- Make invalid states unrepresentable
- Use discriminated unions for closed sets
- Avoid `any` / dynamic where possible

## Error Handling
- Follow Dart 3's idiom (exceptions, Result, Either, etc.)
- Handle errors at the appropriate level
- Don't swallow errors silently
- Provide context with errors

## Concurrency
- Use Dart 3's native concurrency primitive
- Avoid shared mutable state
- Prefer message passing where possible
- Always propagate cancellation

## Project Structure
```
src/
├── ... (idiomatic layout)
```

## Testing
- Use Dart 3's standard test framework
- One test file per source file
- Test behavior, not implementation
- Aim for 70-80% coverage

## Common Pitfalls (specific to Dart 3)
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
1. The Dart 3 code
2. Type annotations (if applicable)
3. Tests
4. Notes on idiomatic choices made

