---
name: api-admin-user-ban
description: Use when implementing the `POST /admin/users/:id/ban` endpoint. Always handles: ban user. Follows REST conventions and security best practices.
---

# API Endpoint: POST /admin/users/:id/ban

Implement `POST /admin/users/:id/ban` — ban user.

## Route Definition
Show the route handler with:
- HTTP method + path
- Auth requirement
- Request validation (Zod / similar)
- Response schema
- Error cases

## Request Schema
Define the request body / params / query schema.

## Response Schema
Define the success and error response shapes.

## Auth / Authorization
- Who can call this endpoint?
- What role / scope is required?
- Multi-tenant isolation?

## Validation
- Input validation
- Business rule validation
- Authorization check

## Business Logic
Step-by-step:
1. Validate input
2. Authorize
3. Execute business logic
4. Side effects (email, webhook, audit log)
5. Return response

## Side Effects
- Database writes (transactional)
- Async jobs (queue)
- Webhooks
- Emails
- Notifications
- Audit log entries

## Error Cases
- 400: invalid input
- 401: not authenticated
- 403: not authorized
- 404: resource not found
- 409: conflict (duplicate, state)
- 422: semantic validation
- 429: rate limited
- 500: server error

## Rate Limiting
- Per-user limit
- Per-IP limit
- Burst allowance

## Testing
- Happy path
- Validation errors
- Auth / authz errors
- Conflict errors
- Rate limiting
- Idempotency (if applicable)

## Output Format
1. Route handler code
2. Request / response schemas
3. Auth middleware
4. Validation
5. Tests

