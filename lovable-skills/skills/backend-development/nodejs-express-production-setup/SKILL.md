---
name: nodejs-express-production-setup
description: Use when setting up a production Node.js / Express server — structure, middleware, error handling, logging, security headers, graceful shutdown.
---

# Node.js / Express Production Setup

Production Node.js needs more than `app.listen()`.

## Project Structure
```
src/
├── config/          # env, db, feature flags
├── middleware/       # auth, logging, error handling
├── routes/          # route definitions
├── services/        # business logic
├── repositories/    # data access
├── jobs/            # background jobs
├── utils/           # helpers
├── types/           # shared types
└── app.ts           # app setup
```

## App Setup
```ts
import express from 'express'
import helmet from 'helmet'
import cors from 'cors'
import compression from 'compression'
import rateLimit from 'express-rate-limit'
import { errorHandler } from './middleware/errorHandler'
import { requestLogger } from './middleware/requestLogger'

export function createApp() {
  const app = express()

  // Security
  app.use(helmet())
  app.use(cors({ origin: env.CORS_ORIGINS, credentials: true }))
  app.disable('x-powered-by')

  // Body parsing
  app.use(express.json({ limit: '1mb' }))
  app.use(express.urlencoded({ extended: true, limit: '1mb' }))

  // Compression
  app.use(compression())

  // Rate limiting
  app.use(rateLimit({ windowMs: 60_000, max: 100 }))

  // Logging
  app.use(requestLogger)

  // Health check
  app.get('/health', (_req, res) => res.json({ status: 'ok' }))
  app.get('/ready', async (_req, res) => {
    const dbOk = await checkDb()
    res.status(dbOk ? 200 : 503).json({ db: dbOk })
  })

  // Routes
  app.use('/v1/users', usersRouter)
  app.use('/v1/todos', todosRouter)

  // 404
  app.use((_req, res) => res.status(404).json({ error: { code: 'NOT_FOUND' } }))

  // Error handler (must be last)
  app.use(errorHandler)

  return app
}
```

## Error Handler
```ts
export class HttpError extends Error {
  constructor(public status: number, public code: string, message: string, public details?: any) {
    super(message)
  }
}

export function errorHandler(err, req, res, _next) {
  const isHttp = err instanceof HttpError
  const status = isHttp ? err.status : 500
  const code = isHttp ? err.code : 'INTERNAL_ERROR'

  if (status >= 500) {
    logger.error({ err, req }, 'Internal error')
  } else {
    logger.warn({ err, req }, 'Client error')
  }

  res.status(status).json({
    error: {
      code,
      message: isHttp ? err.message : 'Internal server error',
      details: err.details,
      requestId: req.id,
    },
  })
}
```

## Async Handler Wrapper
```ts
export const asyncHandler = (fn) => (req, res, next) =>
  Promise.resolve(fn(req, res, next)).catch(next)

// Usage
router.get('/todos/:id', asyncHandler(async (req, res) => {
  const todo = await todoService.get(req.params.id)
  if (!todo) throw new HttpError(404, 'NOT_FOUND', 'Todo not found')
  res.json(todo)
}))
```

## Request ID
```ts
import { randomUUID } from 'crypto'
app.use((req, _res, next) => {
  req.id = req.headers['x-request-id'] || randomUUID()
  next()
})
```

## Structured Logging (pino)
```ts
import pino from 'pino'
export const logger = pino({
  level: env.LOG_LEVEL,
  serializers: { req: (r) => ({ id: r.id, method: r.method, url: r.url }) },
})
```

## Graceful Shutdown
```ts
let server
async function start() {
  server = app.listen(env.PORT, () => logger.info({ port: env.PORT }, 'Server started'))
}

async function shutdown(signal: string) {
  logger.info({ signal }, 'Shutting down')
  server?.close(() => logger.info('HTTP closed'))
  await db.destroy()
  await queue.close()
  process.exit(0)
}

process.on('SIGTERM', () => shutdown('SIGTERM'))
process.on('SIGINT', () => shutdown('SIGINT'))

// Unhandled errors
process.on('unhandledRejection', (reason) => {
  logger.error({ reason }, 'Unhandled rejection')
})
process.on('uncaughtException', (err) => {
  logger.fatal({ err }, 'Uncaught exception')
  shutdown('uncaughtException')
})
```

## Environment Variables (Zod)
```ts
import { z } from 'zod'

const EnvSchema = z.object({
  NODE_ENV: z.enum(['development', 'production', 'test']),
  PORT: z.coerce.number().default(3000),
  DATABASE_URL: z.string().url(),
  JWT_PRIVATE_KEY: z.string(),
  CORS_ORIGINS: z.string().transform(s => s.split(',')),
  LOG_LEVEL: z.enum(['fatal', 'error', 'warn', 'info', 'debug', 'trace']).default('info'),
})

export const env = EnvSchema.parse(process.env)
```

## Health Check Endpoints
- `/health` — process is alive (returns 200 immediately)
- `/ready` — process is ready to serve (checks DB, queue, etc.)

## Forbidden Patterns
- `console.log` in production (use pino)
- `app.listen` without graceful shutdown
- No request IDs (logs are uncorrelated)
- Sync code in request handlers
- Trusting `req.headers.host` for redirects

## Output Format
1. Project structure
2. App setup
3. Middleware list
4. Error handler
5. Graceful shutdown

