---
name: error-websocket-disconnected
description: Use when handling the error: WebSocket disconnected. Always uses strategy: auto-reconnect, user message. Provides user-friendly message, recovery, and logging.
---

# Error Handling: WebSocket disconnected

Websocket disconnected.

## Strategy
auto-reconnect, user message

## Detection
How to detect this error:
- Try/catch patterns
- Error type checks
- Status code checks
- Network event listeners

## Recovery
Step-by-step recovery:
1. Detect
2. Log (structured)
3. Decide: retry, fallback, or surface
4. If retry: exponential backoff + jitter + max attempts
5. If fallback: use cached data, default value, or degraded UX
6. If surface: show user-friendly message + action

## User Message
- Plain language (no jargon, no error codes)
- Action-oriented (what can the user do?)
- Reassuring (not their fault, unless it is)
- Brief

Examples:
- "Couldn't reach the server. Check your connection and try again."
- "This file is too large. Try one under 5 MB."
- "You don't have access to this. Request access from your admin."

## Logging
Structured log with:
- Error type
- Stack trace (server) / context (client)
- User ID (if authenticated)
- Request ID (if available)
- Relevant state (URL, params)

## Monitoring
- Sentry / Datadog / similar
- Alert on error rate spike
- Track in metrics dashboard

## Retry Strategy (if applicable)
- Max attempts: 3
- Backoff: exponential (1s, 2s, 4s) + jitter
- Skip retry for: 4xx (except 408, 429), network not detected

## Forbidden Patterns
- Swallowing errors silently
- Showing stack traces to users
- Retry without backoff (DDoS your own server)
- Retry on 4xx (won't help, will hurt)
- Generic "Something went wrong" without action

## Output Format
1. Detection code
2. Recovery flow
3. User message
4. Logging code
5. Test cases (simulate the error)

