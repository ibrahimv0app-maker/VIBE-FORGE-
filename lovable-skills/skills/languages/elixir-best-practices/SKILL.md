---
name: elixir-best-practices
description: Use when writing Elixir code. Always follows Elixir idioms, style guide, type system, and best practices: pattern matching, OTP, genservers, Ecto.
---

# Elixir Best Practices

Write idiomatic, production-grade Elixir.

## Style Guide
- Follow the official Elixir style guide
- Use a formatter: pattern matching, OTP, genservers, Ecto
- Use a linter with strict rules
- Code should pass CI without warnings

## Type System (if applicable)
- Use Elixir's type system to its fullest: pattern matching, OTP, genservers, Ecto
- Prefer types over comments
- Make invalid states unrepresentable
- Use discriminated unions for closed sets
- Avoid `any` / dynamic where possible

## Error Handling
- Follow Elixir's idiom (exceptions, Result, Either, etc.)
- Handle errors at the appropriate level
- Don't swallow errors silently
- Provide context with errors

## Concurrency
- Use Elixir's native concurrency primitive
- Avoid shared mutable state
- Prefer message passing where possible
- Always propagate cancellation

## Project Structure
```
src/
├── ... (idiomatic layout)
```

## Testing
- Use Elixir's standard test framework
- One test file per source file
- Test behavior, not implementation
- Aim for 70-80% coverage

## Common Pitfalls (specific to Elixir)
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
1. The Elixir code
2. Type annotations (if applicable)
3. Tests
4. Notes on idiomatic choices made

