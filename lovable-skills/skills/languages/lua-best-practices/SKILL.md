---
name: lua-best-practices
description: Use when writing Lua code. Always follows Lua idioms, style guide, type system, and best practices: metatables, coroutines, Luarocks, strict mode.
---

# Lua Best Practices

Write idiomatic, production-grade Lua.

## Style Guide
- Follow the official Lua style guide
- Use a formatter: metatables, coroutines, Luarocks, strict mode
- Use a linter with strict rules
- Code should pass CI without warnings

## Type System (if applicable)
- Use Lua's type system to its fullest: metatables, coroutines, Luarocks, strict mode
- Prefer types over comments
- Make invalid states unrepresentable
- Use discriminated unions for closed sets
- Avoid `any` / dynamic where possible

## Error Handling
- Follow Lua's idiom (exceptions, Result, Either, etc.)
- Handle errors at the appropriate level
- Don't swallow errors silently
- Provide context with errors

## Concurrency
- Use Lua's native concurrency primitive
- Avoid shared mutable state
- Prefer message passing where possible
- Always propagate cancellation

## Project Structure
```
src/
├── ... (idiomatic layout)
```

## Testing
- Use Lua's standard test framework
- One test file per source file
- Test behavior, not implementation
- Aim for 70-80% coverage

## Common Pitfalls (specific to Lua)
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
1. The Lua code
2. Type annotations (if applicable)
3. Tests
4. Notes on idiomatic choices made

