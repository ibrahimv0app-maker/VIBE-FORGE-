---
name: owasp-top-10-auditor
description: Use when auditing a web application for security vulnerabilities. Always checks OWASP Top 10, verifies findings, and provides actionable remediation.
---

# OWASP Top 10 Auditor

Security audit checklist. Don't skip any category.

## 1. Injection
- [ ] All SQL queries use parameterized statements
- [ ] No string concatenation in queries
- [ ] ORM queries are parameterized
- [ ] No `eval()`, `Function()`, `child_process.exec(userInput)`
- [ ] No shell injection in file paths

## 2. Broken Authentication
- [ ] Passwords hashed with bcrypt/argon2 (not MD5/SHA1)
- [ ] Password reset tokens are single-use and expire
- [ ] Session tokens regenerated after login
- [ ] Failed login attempts rate-limited
- [ ] MFA available for sensitive accounts
- [ ] No predictable session IDs

## 3. Sensitive Data Exposure
- [ ] HTTPS enforced (HTTP redirects to HTTPS)
- [ ] HSTS header set
- [ ] Sensitive data encrypted at rest
- [ ] API keys not in client-side code
- [ ] No secrets in version control
- [ ] Logs don't contain passwords / tokens / PII

## 4. XML External Entities (XXE)
- [ ] XML parsers disable external entities
- [ ] Or use JSON instead of XML

## 5. Broken Access Control
- [ ] Authorization checks on every protected route
- [ ] Server-side enforcement (not just UI hiding)
- [ ] User can't access other users' data by changing IDs
- [ ] Admin endpoints protected
- [ ] API rate-limited per user
- [ ] CORS configured properly (not `*`)

## 6. Security Misconfiguration
- [ ] Default credentials changed
- [ ] Debug mode off in production
- [ ] Error messages don't leak stack traces
- [ ] Security headers set (CSP, HSTS, X-Frame-Options, etc.)
- [ ] Unnecessary features disabled
- [ ] File permissions correct

## 7. Cross-Site Scripting (XSS)
- [ ] All user input is escaped on output
- [ ] Framework auto-escaping enabled (React's JSX, etc.)
- [ ] `dangerouslySetInnerHTML` audited
- [ ] CSP header set
- [ ] HttpOnly cookies for session
- [ ] No reflected user input in HTML without escaping

## 8. Insecure Deserialization
- [ ] No deserializing untrusted data
- [ ] Or use signed/verified serialization
- [ ] JSON.parse on untrusted input is fine (but validate schema)

## 9. Using Components with Known Vulnerabilities
- [ ] `npm audit` clean (or known false positives)
- [ ] Dependencies updated regularly
- [ ] No unmaintained dependencies
- [ ] Lock file committed
- [ ] SBOM (software bill of materials) available

## 10. Insufficient Logging & Monitoring
- [ ] Auth events logged (login, logout, failed login)
- [ ] Privileged actions logged
- [ ] Logs centralized
- [ ] Alerts on suspicious activity
- [ ] Logs retained per compliance requirements

## Security Headers Check
```
Content-Security-Policy: default-src 'self'; script-src 'self' 'unsafe-inline'; ...
Strict-Transport-Security: max-age=31536000; includeSubDomains; preload
X-Frame-Options: DENY
X-Content-Type-Options: nosniff
Referrer-Policy: strict-origin-when-cross-origin
Permissions-Policy: geolocation=(), microphone=(), camera=()
```

## Audit Process
1. Map the application (routes, inputs, auth flows)
2. For each input: trace it through the app, look for unsafe usage
3. For each route: verify auth and authz
4. For each dependency: check for known CVEs
5. For each configuration: verify it's secure
6. Document findings with severity (Critical/High/Medium/Low)
7. Provide remediation for each finding

## Severity Definitions
- **Critical**: exploitable remotely, no auth, RCE or data leak
- **High**: exploitable, requires auth or specific conditions
- **Medium**: requires user interaction or specific conditions
- **Low**: defense in depth, hard to exploit

## Forbidden Patterns
- Skipping categories "because we don't use X"
- Marking findings as fixed without verification
- Not providing remediation
- Audit without a written report

## Output Format
1. Application summary
2. Findings table (severity, category, description, remediation)
3. Risk score
4. Prioritized remediation plan

