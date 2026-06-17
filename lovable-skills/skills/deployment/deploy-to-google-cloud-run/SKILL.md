---
name: deploy-to-google-cloud-run
description: Use when deploying an app to Google Cloud Run. Best for: Containerized serverless. Always configures Scale to zero, managed, pay per use properly.
---

# Deploy to Google Cloud Run

Production deployment guide for Google Cloud Run.

## Why Google Cloud Run
- Containerized serverless
- Key features: Scale to zero, managed, pay per use

## Prerequisites
- App is containerized (or compatible with Google Cloud Run's build system)
- Environment variables defined
- Health check endpoint implemented
- Database configured (managed or external)

## Deployment Configuration
Provide the configuration files specific to Google Cloud Run:
- `vercel.json` / `netlify.toml` / `Dockerfile` / `docker-compose.yml` / `app.yaml` / etc.
- Environment variable setup
- Build settings
- Custom domain configuration
- HTTPS / SSL setup

## CI/CD Integration
- Connect GitHub repo
- Auto-deploy on push to main
- Preview deploys on PRs (if supported)
- Rollback strategy

## Environment Variables
List required env vars:
- `DATABASE_URL`
- `JWT_SECRET`
- `STRIPE_SECRET_KEY`
- etc.
Mark which are public (safe to expose) vs secret.

## Custom Domain
- Add custom domain in Google Cloud Run dashboard
- Configure DNS (CNAME or A record)
- HTTPS auto-provisioned (Let's Encrypt / managed cert)

## Monitoring
- Google Cloud Run built-in metrics
- Logs (centralized)
- Uptime monitoring
- Error tracking (Sentry)

## Scaling
- Google Cloud Run scaling options (horizontal, vertical, auto)
- Cost implications
- Cold start mitigation (if serverless)

## Database Strategy
- Managed DB on Google Cloud Run (if offered)
- External DB (Neon, Supabase, PlanetScale, AWS RDS)
- Connection pooling
- Backups

## Backups & DR
- Database backup strategy
- Code rollback strategy
- Disaster recovery plan

## Security
- HTTPS only
- Environment secrets in Google Cloud Run's secret manager
- Rate limiting
- WAF (if available)

## Forbidden Patterns
- Hard-coded secrets in code
- Not using preview deploys
- No health check
- Single instance without redundancy for critical apps
- No rollback plan

## Output Format
1. Configuration files
2. Environment variable list
3. Deployment command / steps
4. Post-deploy verification checklist

