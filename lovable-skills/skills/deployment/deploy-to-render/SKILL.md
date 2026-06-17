---
name: deploy-to-render
description: Use when deploying an app to Render. Best for: Web services, background workers, cron, DBs. Always configures Auto-deploy, managed Postgres, free tier properly.
---

# Deploy to Render

Production deployment guide for Render.

## Why Render
- Web services, background workers, cron, DBs
- Key features: Auto-deploy, managed Postgres, free tier

## Prerequisites
- App is containerized (or compatible with Render's build system)
- Environment variables defined
- Health check endpoint implemented
- Database configured (managed or external)

## Deployment Configuration
Provide the configuration files specific to Render:
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
- Add custom domain in Render dashboard
- Configure DNS (CNAME or A record)
- HTTPS auto-provisioned (Let's Encrypt / managed cert)

## Monitoring
- Render built-in metrics
- Logs (centralized)
- Uptime monitoring
- Error tracking (Sentry)

## Scaling
- Render scaling options (horizontal, vertical, auto)
- Cost implications
- Cold start mitigation (if serverless)

## Database Strategy
- Managed DB on Render (if offered)
- External DB (Neon, Supabase, PlanetScale, AWS RDS)
- Connection pooling
- Backups

## Backups & DR
- Database backup strategy
- Code rollback strategy
- Disaster recovery plan

## Security
- HTTPS only
- Environment secrets in Render's secret manager
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

