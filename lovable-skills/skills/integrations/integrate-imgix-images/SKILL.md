---
name: integrate-imgix-images
description: Use when integrating Imgix image CDN into an app. Always uses the official SDK, handles webhooks, errors, retries, and follows the provider's best practices. Features: transformations, optimization.
---

# Integrate Imgix image CDN

Production integration guide for Imgix image CDN.

## What Imgix image CDN Provides
transformations, optimization

## Setup
1. Create account / project on Imgix image CDN
2. Get API credentials (keys, tokens, OAuth client)
3. Add credentials to environment variables (never commit)
4. Install official SDK: `npm install imgix_images` (or equivalent)

## SDK Setup
```ts
// lib/imgix-images.ts
import { Client } from 'imgix-images'

export const client = new Client({
  apiKey: process.env.IMGIX_IMAGES_API_KEY!,
})
```

## Core Operations
Implement wrappers for the operations you need:
- Authentication (if applicable)
- Create / read / update / delete (CRUD)
- Webhook handling
- Error handling
- Rate limit handling
- Idempotency (for write operations)

## Webhooks
- Verify webhook signatures (CRITICAL — never skip)
- Idempotent handling (webhooks can be delivered multiple times)
- Return 200 quickly, process async
- Have a webhook retry / dead-letter strategy

## Error Handling
```ts
try {
  await client.resource.create(...)
} catch (err) {
  if (err instanceof RateLimitError) {
    // backoff and retry
  } else if (err instanceof ValidationError) {
    // log and surface to user
  } else {
    // log and rethrow
  }
}
```

## Rate Limiting
- Respect rate limit headers
- Implement exponential backoff
- Use a queue for high-volume operations

## Testing
- Mock the SDK in unit tests
- Use sandbox / test mode for integration tests
- Test webhook signature verification
- Test error scenarios

## Security
- API keys in env vars, never in code
- Webhook signature verification
- HTTPS only
- Don't log sensitive data
- Principle of least privilege for API scopes

## Monitoring
- Log all API calls (request, response, latency)
- Alert on error rates
- Track usage / cost
- Monitor webhook delivery

## Cost Optimization
- Cache responses where possible
- Batch operations when supported
- Use webhooks instead of polling
- Monitor usage and set budgets

## Forbidden Patterns
- Hard-coded API keys
- Skipping webhook signature verification
- No retry on transient errors
- Synchronous processing of webhooks
- No rate limit handling
- No idempotency for writes

## Output Format
1. SDK setup
2. Core operation wrappers
3. Webhook handler
4. Error handling
5. Environment variables list

