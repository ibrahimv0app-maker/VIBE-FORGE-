---
name: cloudflare-worker-architect
description: Use when building Cloudflare Workers. Always uses KV, D1, R2, Durable Objects, Queues.
---

# Cloudflare Worker Architect

Use when building Cloudflare Workers. Always uses KV, D1, R2, Durable Objects, Queues.

## Platform Concepts
Define the core concepts of the platform.

## Setup
Step-by-step setup.

## Common Patterns
- Trigger → Action
- Error handling
- Retry strategy
- Pagination
- Rate limiting

## Best Practices
- Idempotency
- Atomic operations
- Backpressure
- Observability

## Forbidden Patterns
- Synchronous long-running tasks
- Hard-coded credentials
- No error handling
- No retries

## Output Format
1. Workflow configuration
2. Code (if needed)
3. Test plan

