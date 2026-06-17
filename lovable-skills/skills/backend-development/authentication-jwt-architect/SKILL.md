---
name: authentication-jwt-architect
description: Use when implementing JWT authentication — issuance, refresh, revocation, storage, security. Always follows current best practices for token security.
---

        # JWT Authentication Architect

        JWTs are a footgun. Use them carefully.

        ## Token Strategy
        - **Access token**: short-lived (15 min), stateless
        - **Refresh token**: long-lived (7-30 days), stateful (stored in DB, revocable)
        - **ID token** (OIDC): identity claims, for the client only

        ## Access Token Claims
        ```json
        {
          "sub": "user_123",
          "iss": "https://api.example.com",
          "aud": "https://api.example.com",
          "iat": 1633024800,
          "exp": 1633025700,
          "scope": "todos:read todos:write",
          "type": "access"
        }
        ```

        ## Refresh Token Pattern
        ```
        POST /auth/refresh
        Cookie: refresh_token=... (httponly, secure, samesite=strict)

        Response:
        {
          "accessToken": "eyJ...",
          "expiresIn": 900
        }
        ```

        ## Token Storage
        - **Access token (browser)**: in-memory (JS variable), NOT localStorage
        - **Refresh token (browser)**: HttpOnly cookie with `Secure`, `SameSite=Strict`, `Path=/auth/refresh`
        - **Access token (mobile)**: secure storage (Keychain / Keystore)
        - **Refresh token (mobile)**: secure storage, separate from access

        ## Why Not localStorage?
        - Any XSS can read localStorage
- HttpOnly cookies are not accessible to JS
        - In-memory access tokens limit the damage of XSS to the current session

        ## Issuance Flow
        ```
        1. User logs in (POST /auth/login with email + password)
        2. Server validates credentials
        3. Server issues access token (15 min) + refresh token (7 days)
        4. Server stores refresh token hash in DB (for revocation)
        5. Server sends access token in response body
        6. Server sets refresh token as HttpOnly cookie
        7. Client stores access token in memory
        8. Client uses access token in Authorization header for API calls
        ```

        ## Refresh Flow
        ```
        1. Access token expires
        2. Client calls POST /auth/refresh (cookie sent automatically)
        3. Server validates refresh token against DB
        4. Server issues new access token (+ optional new refresh token = rotation)
        5. Server invalidates old refresh token (rotation)
        6. Client receives new access token
        ```

        ## Refresh Token Rotation
        - Issue a new refresh token on every refresh
        - Invalidate the old one
        - If an invalidated refresh token is used → revoke the entire family (token reuse detected)

        ## Revocation
        - Refresh tokens are stored hashed in DB → can be revoked
        - Access tokens are stateless → cannot be revoked without a blocklist
        - For immediate logout: short access token lifetime + refresh token revocation
        - For high-security: maintain an access token blocklist (Redis, short TTL)

        ## Logout Flow
        ```
        POST /auth/logout
        Cookie: refresh_token=...

        Server:
        1. Hash refresh token
        2. Delete from DB
        3. Clear cookie
        4. (Optional) Add access token JTI to blocklist
        ```

        ## JWT Signing
        - **Algorithm**: EdDSA (Ed25519) preferred, RS256 acceptable, HS256 only for single-service
        - **Keys**: rotate annually, store in secret manager
        - **Kid header**: include key ID for key rotation
        - Never use `alg: none`
        - Never accept `alg` from the token (force your expected alg)

        ## Validation Rules
        ```ts
        function validateToken(token: string): Claims {
          // 1. Verify signature (with expected algorithm)
          // 2. Check iss
          // 3. Check aud
          // 3. Check exp (with clock skew tolerance, e.g., 30s)
          // 5. Check iat (reject future tokens)
          // 6. Check nbf if present
          // 7. Check type == 'access'
          return claims
        }
        ```

        ## CSRF Protection (when using cookies)
        - SameSite=Strict on cookies (preferred)
        - Or: double-submit cookie pattern
        - Or: custom header check (CSRF token in header)

        ## Multi-Tenant / Scopes
        ```json
        {
          "sub": "user_123",
          "tenantId": "tenant_456",
          "scope": "todos:read todos:write admin:*"
        }
        ```

        ## Forbidden Patterns
        - Storing access tokens in localStorage
        - Long-lived access tokens (>1 hour)
        - HS256 with shared secret across services
        - Not validating `iss` and `aud`
        - Accepting `alg` from the token
        - Not rotating refresh tokens

        ## Output Format
        1. Token strategy (lifetimes, storage)
        2. Issuance flow
        3. Refresh flow
        4. Revocation strategy
        5. Validation code

