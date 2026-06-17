---
name: rest-api-design-architect
description: Use when designing or implementing REST APIs. Always follows RESTful conventions, versioning, pagination, filtering, error format, and status code best practices.
---

# REST API Design Architect

A REST API is a contract. Treat it like one.

## URL Conventions
- Resource names: plural nouns (`/users`, `/todos`, `/orders`)
- Hierarchical: `/users/{userId}/todos`
- kebab-case for multi-word: `/password-resets`
- Versioning: `/v1/users` (path versioning preferred)
- Query params: snake_case or camelCase (pick one, be consistent)

## HTTP Methods
| Method | Use | Idempotent | Safe |
|--------|-----|------------|------|
| GET | Read | Yes | Yes |
| POST | Create | No | No |
| PUT | Full update | Yes | No |
| PATCH | Partial update | No | No |
| DELETE | Delete | Yes | No |

## Status Codes
- 200 OK — successful GET, PUT, PATCH, DELETE
- 201 Created — successful POST
204 No Content — successful DELETE (no body)
- 400 Bad Request — validation error
- 401 Unauthorized — not authenticated
- 403 Forbidden — authenticated but not allowed
- 404 Not Found — resource doesn't exist
- 409 Conflict — duplicate / state conflict
- 422 Unprocessable Entity — semantic validation error
- 429 Too Many Requests — rate limited
- 500 Internal Server Error — server bug

## Pagination
```
GET /v1/todos?page=2&pageSize=20

Response:
{
  "data": [...],
  "pagination": {
    "page": 2,
    "pageSize": 20,
    "total": 143,
    "totalPages": 8
  }
}
```

Cursor pagination preferred for large datasets:
```
GET /v1/todos?cursor=abc123&limit=20

Response:
{
  "data": [...],
  "nextCursor": "def456",
  "hasMore": true
}
```

## Filtering & Sorting
```
GET /v1/todos?status=open&priority=high&sort=-createdAt,assignee
```
- `-` prefix = descending
- Multiple sort fields = comma-separated

## Error Format
```json
{
  "error": {
    "code": "VALIDATION_ERROR",
    "message": "Invalid request",
    "details": [
      { "field": "email", "message": "Must be a valid email" },
      { "field": "password", "message": "Must be at least 8 characters" }
    ],
    "requestId": "req_abc123"
  }
}
```

## Response Envelope
Pick one and stick to it:
```json
// Option A: direct
{ "id": 1, "title": "..." }

// Option B: wrapped
{ "data": { "id": 1, "title": "..." }, "meta": {...} }
```

## Authentication
- Bearer token: `Authorization: Bearer <token>`
- API key: `X-API-Key: <key>` (for service-to-service)
- Never pass tokens in URL params

## Rate Limiting Headers
```
X-RateLimit-Limit: 100
X-RateLimit-Remaining: 95
X-RateLimit-Reset: 1633024800
```

## Idempotency
For POST /payments and other non-idempotent operations:
```
Idempotency-Key: <uuid>
```
Server stores the key + response; same key returns same response.

## Versioning Strategy
- Path: `/v1/`, `/v2/` (most common, easy to route)
- Header: `Accept: application/vnd.api+json;version=1`
- Breaking changes require a new major version

## What Counts as a Breaking Change
- Removing a field
- Changing a field type
- Changing a URL
- Changing required/optional
- Changing status codes
- Adding required fields

## Non-Breaking Changes (Safe)
- Adding optional fields
- Adding new endpoints
- Adding new enum values (be careful)

## Output Format
1. Endpoint table (method, path, description)
2. Request schema (Zod / TypeScript)
3. Response schema
4. Error cases
5. Example request/response

