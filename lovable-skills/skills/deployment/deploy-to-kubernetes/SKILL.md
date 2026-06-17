---
name: deploy-to-kubernetes
description: Use when deploying an app to Kubernetes (self-managed or EKS/GKE/AKS). Best for: Microservices at scale. Always configures Pods, deployments, services, ingress, HPA properly.
---

# Deploy to Kubernetes (self-managed or EKS/GKE/AKS)

Production deployment guide for Kubernetes (self-managed or EKS/GKE/AKS).

## Why Kubernetes (self-managed or EKS/GKE/AKS)
- Microservices at scale
- Key features: Pods, deployments, services, ingress, HPA

## Prerequisites
- App is containerized (or compatible with Kubernetes (self-managed or EKS/GKE/AKS)'s build system)
- Environment variables defined
- Health check endpoint implemented
- Database configured (managed or external)

## Deployment Configuration
Provide the configuration files specific to Kubernetes (self-managed or EKS/GKE/AKS):
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
- Add custom domain in Kubernetes (self-managed or EKS/GKE/AKS) dashboard
- Configure DNS (CNAME or A record)
- HTTPS auto-provisioned (Let's Encrypt / managed cert)

## Monitoring
- Kubernetes (self-managed or EKS/GKE/AKS) built-in metrics
- Logs (centralized)
- Uptime monitoring
- Error tracking (Sentry)

## Scaling
- Kubernetes (self-managed or EKS/GKE/AKS) scaling options (horizontal, vertical, auto)
- Cost implications
- Cold start mitigation (if serverless)

## Database Strategy
- Managed DB on Kubernetes (self-managed or EKS/GKE/AKS) (if offered)
- External DB (Neon, Supabase, PlanetScale, AWS RDS)
- Connection pooling
- Backups

## Backups & DR
- Database backup strategy
- Code rollback strategy
- Disaster recovery plan

## Security
- HTTPS only
- Environment secrets in Kubernetes (self-managed or EKS/GKE/AKS)'s secret manager
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

