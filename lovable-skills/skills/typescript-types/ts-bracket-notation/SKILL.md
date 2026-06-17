---
name: ts-bracket-notation
description: Use when you need the BracketNotation<T> - bracket notation keys TypeScript utility type. Implements using template literal.
---

# TypeScript Type: Bracket Notation

Bracketnotation<t> - bracket notation keys.

## Implementation Technique
template literal

## Type Definition
Provide the TypeScript type definition with clear comments.

## Usage Example
Show 2-3 usage examples with input types and resulting types.

## How It Works
Walk through the type evaluation step by step.

## Edge Cases
- What happens with unions
- What happens with optional fields
- What happens with readonly fields
- What happens with never / unknown / any

## Test Cases
Use tsd or type-level testing to verify:
```ts
import { expectType } from 'tsd'
expectType<ExpectedType>(actualValue)
```

## Common Pitfalls
- Distributive conditionals (use [T] to prevent)
- Inference failure on recursive types
- Performance on deeply nested types
- Display in IDEs (use simplification helpers)

## Output Format
1. Type definition
2. Usage examples
3. How it works (step by step)
4. Test cases (type-level)

