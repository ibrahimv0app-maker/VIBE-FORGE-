---
name: security-session-fixation-prevention
description: Use when addressing session fixation prevention. Always uses regenerate session ID and follows current best practices.
---

# Security: Session Fixation Prevention

Session fixation prevention.

## Threat Model
Describe the threat this addresses:
- Attack vector
- Attacker capability required
- Impact if exploited

## Prevention Strategy
regenerate session ID

## Implementation
Provide production-ready code / configuration with:
- Defense in depth (multiple layers)
- Fail-safe defaults
- No security through obscurity
- Logging for security events

## Verification
- How to verify the fix works
- Automated tests
- Manual tests
- Penetration tests

## Common Bypasses
List known bypasses and how to prevent them.

## False Positives / Negatives
- Common false positives to ignore
- Common false negatives to address

## Compliance Mapping
- OWASP Top 10: which category
- CWE: which ID
- PCI DSS: which requirement
- SOC 2: which criterion

## Monitoring
- What to log
- Alert thresholds
- Incident response

## Output Format
1. Threat model
2. Prevention code / config
3. Verification tests
4. Monitoring plan

