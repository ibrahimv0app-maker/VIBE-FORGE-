---
name: sql-schema-architect
description: Use when designing SQL database schemas — Postgres, MySQL, SQLite. Always follows normalization, naming, indexing, and constraint best practices.
---

# SQL Schema Architect

Schemas outlive applications. Design them with care.

## Naming Conventions
- Tables: snake_case plural (`users`, `todo_items`)
- Columns: snake_case (`created_at`, `user_id`)
- Primary keys: `id` (UUID preferred)
- Foreign keys: `<table_singular>_id` (`user_id`, `todo_id`)
- Join tables: descriptive (`user_roles`, not `users_roles`)
- Indexes: `idx_<table>_<columns>` (`idx_todos_user_id_status`)
- Foreign key constraints: `fk_<from>_<to>` (`fk_todos_user`)
- Unique constraints: `uq_<table>_<columns>`

## UUID Primary Keys
```sql
CREATE EXTENSION IF NOT EXISTS "pgcrypto";

CREATE TABLE users (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  email TEXT NOT NULL UNIQUE,
  created_at TIMESTAMPTZ NOT NULL DEFAULT NOW(),
  updated_at TIMESTAMPTZ NOT NULL DEFAULT NOW()
);
```
Benefits: no sequential ID leakage, can generate client-side, no central counter bottleneck.

## Timestamps
- Always `TIMESTAMPTZ` (with timezone), never `TIMESTAMP`
- Always `NOW()` default
- `created_at` — set once, never updated
- `updated_at` — update on every change (use a trigger)

```sql
CREATE OR REPLACE FUNCTION update_updated_at()
RETURNS TRIGGER AS $$
BEGIN
  NEW.updated_at = NOW();
  RETURN NEW;
END;
$$ LANGUAGE plpgsql;

CREATE TRIGGER set_updated_at
  BEFORE UPDATE ON users
  FOR EACH ROW
  EXECUTE FUNCTION update_updated_at();
```

## Foreign Keys
```sql
CREATE TABLE todos (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  user_id UUID NOT NULL REFERENCES users(id) ON DELETE CASCADE,
  title TEXT NOT NULL,
  status TEXT NOT NULL DEFAULT 'open',
  created_at TIMESTAMPTZ NOT NULL DEFAULT NOW(),
  updated_at TIMESTAMPTZ NOT NULL DEFAULT NOW()
);

CREATE INDEX idx_todos_user_id ON todos(user_id);
CREATE INDEX idx_todos_status ON todos(status);
CREATE INDEX idx_todos_user_status ON todos(user_id, status);
```

## ON DELETE Rules
- `CASCADE`: delete children when parent is deleted (use carefully)
- `SET NULL`: keep children, set FK to null (requires nullable FK)
- `RESTRICT`: prevent parent deletion if children exist (safest)
- `NO ACTION`: same as RESTRICT, but checked at end of statement

## Indexing Strategy
- Index every foreign key
- Index every column in WHERE clauses
- Composite indexes: order by selectivity (most selective first)
- Partial indexes for sparse data: `WHERE deleted_at IS NULL`
- Don't over-index (slow writes, bloated storage)

```sql
-- Partial index (only non-deleted rows)
CREATE INDEX idx_todos_active ON todos(user_id, status) WHERE deleted_at IS NULL;

-- Expression index (case-insensitive email)
CREATE UNIQUE INDEX idx_users_email_lower ON users(LOWER(email));
```

## Constraints
```sql
CREATE TABLE products (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  name TEXT NOT NULL CHECK (length(name) >= 1 AND length(name) <= 200),
  price_cents INTEGER NOT NULL CHECK (price_cents >= 0),
  sku TEXT NOT NULL UNIQUE,
  stock INTEGER NOT NULL DEFAULT 0 CHECK (stock >= 0),
  metadata JSONB NOT NULL DEFAULT '{}'::jsonb
);
```

## ENUM vs Lookup Table
- ENUM: 1-3 values, never change → use TEXT with CHECK constraint
- Lookup table: 4+ values, may change → use a separate table

```sql
-- Simple: CHECK constraint
CREATE TABLE todos (
  status TEXT NOT NULL CHECK (status IN ('open', 'in_progress', 'done', 'cancelled'))
);

-- Complex: lookup table
CREATE TABLE todo_statuses (id TEXT PRIMARY KEY, name TEXT NOT NULL);
INSERT INTO todo_statuses VALUES ('open', 'Open'), ...;
CREATE TABLE todos (status TEXT NOT NULL REFERENCES todo_statuses(id));
```

## Soft Deletes
```sql
ALTER TABLE todos ADD COLUMN deleted_at TIMESTAMPTZ;

-- Query: WHERE deleted_at IS NULL
-- Index: CREATE INDEX ... WHERE deleted_at IS NULL
```

## JSON Columns
- Use `JSONB` (Postgres) for queryable JSON, never `JSON`
- Don't use JSON for data you need to query/join — use real columns
- Use GIN index for JSONB queries: `CREATE INDEX ON products USING GIN (metadata)`

## Money
- Never use FLOAT for money
- Use INTEGER cents (`price_cents`) or NUMERIC(19, 4)

## Migration Pattern
```sql
-- Up
CREATE TABLE todos (...);

-- Down
DROP TABLE todos;
```

## Migration Safety (Zero-Downtime)
- Add column with default (Postgres 11+ is instant)
- Don't add `NOT NULL` without a default to a large table
- Create indexes `CONCURRENTLY` (Postgres) — doesn't lock the table
- Drop columns in two steps: 1) make nullable / unused, 2) drop later

## Forbidden Patterns
- FLOAT for money
- `TIMESTAMP` without timezone
- VARCHAR(N) without a real reason (use TEXT)
- Missing foreign keys
- Missing indexes on FKs
- ENUM types for things that change
- `SELECT *` in app code

## Output Format
1. Schema (CREATE TABLE statements)
2. Indexes (with rationale)
3. Constraints
4. Triggers (if any)
5. Migration safety notes

