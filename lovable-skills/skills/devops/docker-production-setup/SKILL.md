---
name: docker-production-setup
description: Use when writing Dockerfiles for production Node.js / Next.js / Python apps. Always uses multi-stage builds, non-root user, minimal base image, and proper caching.
---

# Docker Production Setup

Production Docker images must be: small, secure, fast to build, fast to start.

## Node.js Dockerfile (Multi-Stage)
```dockerfile
# Stage 1: Dependencies
FROM node:20-alpine AS deps
WORKDIR /app
COPY package*.json ./
RUN npm ci --only=production

# Stage 2: Build
FROM node:20-alpine AS builder
WORKDIR /app
COPY package*.json ./
RUN npm ci
COPY . .
RUN npm run build

# Stage 3: Production
FROM node:20-alpine AS runner
ENV NODE_ENV=production
WORKDIR /app

# Non-root user
RUN addgroup -g 1001 -S nodejs && adduser -S nextjs -u 1001
USER nextjs

# Copy only what we need
COPY --from=builder --chown=nextjs:nodejs /app/.next/standalone ./
COPY --from=builder --chown=nextjs:nodejs /app/.next/static ./.next/static
COPY --from=builder --chown=nextjs:nodejs /app/public ./public

EXPOSE 3000
ENV PORT=3000
ENV HOSTNAME="0.0.0.0"

HEALTHCHECK --interval=30s --timeout=3s --start-period=5s --retries=3 \
  CMD wget -qO- http://localhost:3000/health || exit 1

CMD ["node", "server.js"]
```

## .dockerignore (Critical)
```
node_modules
.next
.git
.env*
.vscode
.idea
coverage
*.md
Dockerfile
docker-compose*.yml
```

## Multi-Stage Build Benefits
- Final image doesn't contain dev dependencies
- Final image doesn't contain source code (only built artifacts)
- Final image doesn't contain build tools
- Smaller attack surface, smaller image, faster pulls

## Layer Caching
```dockerfile
# BAD: invalidates cache on every code change
COPY . .
RUN npm ci

# GOOD: only invalidates when package.json changes
COPY package*.json ./
RUN npm ci
COPY . .
```

## Non-Root User
```dockerfile
RUN addgroup -g 1001 -S nodejs && adduser -S nextjs -u 1001
USER nextjs
```
If the app is compromised, the attacker is `nextjs`, not `root`.

## Base Image Choice
- `node:20-alpine` — small (~120MB), good default
- `node:20-slim` — Debian-based, more compatible
- `node:20` — full Debian, largest, only if you need system libs
- Pin to a specific version: `node:20.11.0-alpine3.19`

## Health Check
```dockerfile
HEALTHCHECK --interval=30s --timeout=3s --start-period=5s --retries=3 \
  CMD wget -qO- http://localhost:3000/health || exit 1
```
Lets Docker know if your app is actually alive.

## Environment Variables
```dockerfile
# Defaults (override at runtime)
ENV NODE_ENV=production
ENV PORT=3000
```
Never bake secrets into the image — pass at runtime:
```bash
docker run -e DATABASE_URL=... myapp
```

## Docker Compose (Dev)
```yaml
version: '3.9'
services:
  app:
    build: .
    ports: ['3000:3000']
    env_file: .env
    depends_on:
      db:
        condition: service_healthy
  db:
    image: postgres:16-alpine
    environment:
      POSTGRES_DB: app
      POSTGRES_USER: postgres
      POSTGRES_PASSWORD: postgres
    ports: ['5432:5432']
    healthcheck:
      test: ['CMD-SHELL', 'pg_isready -U postgres']
      interval: 5s
      timeout: 3s
      retries: 5
    volumes:
      - db-data:/var/lib/postgresql/data

volumes:
  db-data:
```

## Image Size Targets
- Node.js app: < 300MB
- Next.js standalone: < 200MB
- Static site (nginx): < 50MB
- Python app: < 400MB

## Security
- Scan with `trivy` or `snyk`
- Update base images regularly
- Don't run as root
- Don't bake secrets
- Use `read-only` filesystem where possible: `docker run --read-only`

## Forbidden Patterns
- Single-stage builds for production
- `COPY . .` before `npm ci` (no caching)
- Running as root
- Baking `.env` files into the image
- `latest` tag in production (use semantic versions)
- No `.dockerignore` (huge build context)

## Output Format
1. Dockerfile
2. .dockerignore
3. docker-compose.yml (if dev setup)
4. Build & run commands
5. Image size + security notes

