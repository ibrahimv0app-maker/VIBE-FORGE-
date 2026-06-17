---
name: python-best-practices
description: Use when writing Python code. Always follows Python idioms, style guide, type system, and best practices: type hints, dataclasses, async/await, PEP 8, ruff/black.
---

# Python Best Practices

Write idiomatic, production-grade Python.

## Style Guide
- Follow the official Python style guide
- Use a formatter: type hints, dataclasses, async/await, PEP 8, ruff/black
- Use a linter with strict rules
- Code should pass CI without warnings

## Type System (if applicable)
- Use Python's type system to its fullest: type hints, dataclasses, async/await, PEP 8, ruff/black
- Prefer types over comments
- Make invalid states unrepresentable
- Use discriminated unions for closed sets
- Avoid `any` / dynamic where possible

## Error Handling
- Follow Python's idiom (exceptions, Result, Either, etc.)
- Handle errors at the appropriate level
- Don't swallow errors silently
- Provide context with errors

## Concurrency
- Use Python's native concurrency primitive
- Avoid shared mutable state
- Prefer message passing where possible
- Always propagate cancellation

## Project Structure
```
src/
├── ... (idiomatic layout)
```

## Testing
- Use Python's standard test framework
- One test file per source file
- Test behavior, not implementation
- Aim for 70-80% coverage

## Common Pitfalls (specific to Python)
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
1. The Python code
2. Type annotations (if applicable)
3. Tests
4. Notes on idiomatic choices made

