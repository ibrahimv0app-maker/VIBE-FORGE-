---
name: prisma-schema-architect
description: Use when designing Prisma schemas for Next.js / Node.js apps. Always uses proper relations, indexes, enums, and follows Prisma best practices.
---

# Prisma Schema Architect

Prisma schemas are the source of truth. Design them carefully.

## Basic Pattern
```prisma
// prisma/schema.prisma
generator client {
  provider = "prisma-client-js"
}

datasource db {
  provider = "postgresql"
  url      = env("DATABASE_URL")
}

model User {
  id           String   @id @default(uuid())
  email        String   @unique
  name         String?
  createdAt    DateTime @default(now()) @map("created_at")
  updatedAt    DateTime @updatedAt @map("updated_at")
  todos        Todo[]

  @@map("users")
}

model Todo {
  id          String     @id @default(uuid())
  title       String
  description String?
  status      TodoStatus @default(OPEN)
  userId      String     @map("user_id")
  user        User       @relation(fields: [userId], references: [id], onDelete: Cascade)
  createdAt   DateTime   @default(now()) @map("created_at")
  updatedAt   DateTime   @updatedAt @map("updated_at")

  @@index([userId, status])
  @@map("todos")
}

enum TodoStatus {
  OPEN
  IN_PROGRESS
  DONE
  CANCELLED
}
```

## Naming Convention
- Model: PascalCase singular (`User`, `Todo`)
- Fields: camelCase (`createdAt`, `userId`)
- Use `@map` to map to snake_case in DB
- Use `@@map` to map table name to snake_case plural

## Relations
```prisma
// One-to-many
model User {
  todos Todo[]
}
model Todo {
  userId String
  user   User   @relation(fields: [userId], references: [id])
}

// Many-to-many (implicit)
model Post {
  tags Tag[]
}
model Tag {
  posts Post[]
}

// Many-to-many (explicit, with extra fields)
model PostTag {
  postId   String
  tagId    String
  post     Post   @relation(fields: [postId], references: [id])
  tag      Tag    @relation(fields: [tagId], references: [id])
  assignedAt DateTime @default(now())

  @@id([postId, tagId])
}
```

## Indexes
```prisma
model Todo {
  ...
  @@index([userId])
  @@index([userId, status])
  @@index([createdAt(sort: Desc)])
  @@unique([userId, title])
}
```

## Soft Deletes
```prisma
model Todo {
  ...
  deletedAt DateTime?

  @@index([userId, status, deletedAt])
}

// Query with soft delete filter
await prisma.todo.findMany({
  where: { deletedAt: null, ... },
})

// Or use a Prisma middleware / extension to auto-filter
```

## JSON Fields
```prisma
model Product {
  metadata Json
}

// Query
await prisma.product.findMany({
  where: { metadata: { path: ['category'], equals: 'electronics' } },
})
```

## Decimal / Money
```prisma
model Order {
  totalCents Int      // preferred
  // OR
  total      Decimal  @db.Decimal(19, 4)
}
```

## Composite Primary Keys
```prisma
model PostTag {
  postId String
  tagId  String
  post   Post @relation(fields: [postId], references: [id])
  tag    Tag  @relation(fields: [tagId], references: [id])

  @@id([postId, tagId])
}
```

## Transactions
```ts
await prisma.$transaction([
  prisma.todo.create({ data: { ... } }),
  prisma.auditLog.create({ data: { ... } }),
])

// Interactive transactions (for complex logic)
await prisma.$transaction(async (tx) => {
  const todo = await tx.todo.create({ data: { ... } })
  await tx.auditLog.create({ data: { todoId: todo.id, ... } })
  return todo
})
```

## Migrations
```bash
# Create migration from schema changes
npx prisma migrate dev --name add_todo_status

# Apply migrations in production
npx prisma migrate deploy

# Reset (DEV ONLY)
npx prisma migrate reset
```

## Type-Safe Queries
```ts
import { Prisma } from '@prisma/client'

// Type-safe where input
const where: Prisma.TodoWhereInput = {
  status: 'OPEN',
  userId,
}

// Include relations
const todo = await prisma.todo.findUnique({
  where: { id },
  include: { user: true, tags: true },
})
```

## Performance Tips
- Use `select` instead of `include` when you don't need all fields
- Use `findMany` with `take`/`skip` for pagination
- Use cursor pagination for large datasets: `cursor: { id }, skip: 1, take: 20`
- Use `findFirst` when you only need one (no array wrap)
- Use `groupBy` for aggregations
- Use `prisma.$queryRaw` for complex queries Prisma can't express

## Forbidden Patterns
- `String @id` without `@default(uuid())`
- Missing `@@index` on foreign keys
- `Float` for money
- Not mapping to snake_case (mixed conventions)
- `prisma migrate reset` in production

## Output Format
1. Schema
2. Migration command
3. Example queries
4. Performance notes

