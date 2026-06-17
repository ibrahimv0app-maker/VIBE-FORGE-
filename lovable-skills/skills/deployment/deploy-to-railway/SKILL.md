---
name: deploy-to-railway
description: Use when deploying an app to Railway. Best for: Full-stack apps, databases, workers. Always configures One-click deploys, built-in DBs, simple pricing properly.
---

# Deploy to Railway

Production deployment guide for Railway.

## Why Railway
- Full-stack apps, databases, workers
- Key features: One-click deploys, built-in DBs, simple pricing

## Prerequisites
- App is containerized (or compatible with Railway's build system)
- Environment variables defined
- Health check endpoint implemented
- Database configured (managed or external)

## Deployment Configuration
Provide the configuration files specific to Railway:
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
- Add custom domain in Railway dashboard
- Configure DNS (CNAME or A record)
- HTTPS auto-provisioned (Let's Encrypt / managed cert)

## Monitoring
- Railway built-in metrics
- Logs (centralized)
- Uptime monitoring
- Error tracking (Sentry)

## Scaling
- Railway scaling options (horizontal, vertical, auto)
- Cost implications
- Cold start mitigation (if serverless)

## Database Strategy
- Managed DB on Railway (if offered)
- External DB (Neon, Supabase, PlanetScale, AWS RDS)
- Connection pooling
- Backups

## Backups & DR
- Database backup strategy
- Code rollback strategy
- Disaster recovery plan

## Security
- HTTPS only
- Environment secrets in Railway's secret manager
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

