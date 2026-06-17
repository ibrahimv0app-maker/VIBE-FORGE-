---
name: deploy-to-azure-container-apps
description: Use when deploying an app to Azure Container Apps. Best for: Containerized serverless on Azure. Always configures Scale to zero, Dapr, managed env properly.
---

# Deploy to Azure Container Apps

Production deployment guide for Azure Container Apps.

## Why Azure Container Apps
- Containerized serverless on Azure
- Key features: Scale to zero, Dapr, managed env

## Prerequisites
- App is containerized (or compatible with Azure Container Apps's build system)
- Environment variables defined
- Health check endpoint implemented
- Database configured (managed or external)

## Deployment Configuration
Provide the configuration files specific to Azure Container Apps:
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
- Add custom domain in Azure Container Apps dashboard
- Configure DNS (CNAME or A record)
- HTTPS auto-provisioned (Let's Encrypt / managed cert)

## Monitoring
- Azure Container Apps built-in metrics
- Logs (centralized)
- Uptime monitoring
- Error tracking (Sentry)

## Scaling
- Azure Container Apps scaling options (horizontal, vertical, auto)
- Cost implications
- Cold start mitigation (if serverless)

## Database Strategy
- Managed DB on Azure Container Apps (if offered)
- External DB (Neon, Supabase, PlanetScale, AWS RDS)
- Connection pooling
- Backups

## Backups & DR
- Database backup strategy
- Code rollback strategy
- Disaster recovery plan

## Security
- HTTPS only
- Environment secrets in Azure Container Apps's secret manager
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

