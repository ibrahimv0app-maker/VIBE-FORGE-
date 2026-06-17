---
name: ai-cost-optimization
description: Use when optimizing AI costs — model routing, caching, batching, prompt compression. Always reduces cost without sacrificing quality.
---

# Ai Cost Optimization

AI cost optimization: model routing, semantic caching, batching, prompt compression..

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

