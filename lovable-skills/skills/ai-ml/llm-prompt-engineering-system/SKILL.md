---
name: llm-prompt-engineering-system
description: Use when designing prompt templates, system prompts, and prompt chains for LLMs. Always uses structured prompting with clear roles, examples, and output formats.
---

# Llm Prompt Engineering System

LLM prompt engineering: system prompts, few-shot, chain-of-thought, structured outputs, prompt templates..

## Architecture
Define the components, data flow, and decision points clearly.

## Implementation
Provide production-ready code with:
- Type safety
- Error handling
- Logging / observability
- Tests
- Configuration via env vars

## Evaluation
Always include an evaluation strategy:
- Metrics
- Golden dataset
- Regression tests
- Continuous monitoring

## Cost / Performance
Document the cost / latency / quality tradeoffs.

## Forbidden Patterns
- Hard-coded API keys
- No error handling on API calls
- No retries with backoff
- No rate limiting
- No timeout on LLM calls
- Synchronous calls where async would work

## Output Format
1. Architecture diagram (textual)
2. Implementation
3. Configuration
4. Evaluation plan

