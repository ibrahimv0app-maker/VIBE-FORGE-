---
name: sql-query-optimizer
description: Use when optimizing slow SQL queries — EXPLAIN plan analysis, index strategy, query rewriting, denormalization. Always diagnoses before optimizing.
---

# SQL Query Optimizer

Don't optimize by guess. Use EXPLAIN.

## Diagnosis Workflow
1. Identify the slow query (from logs / APM)
2. Run `EXPLAIN (ANALYZE, BUFFERS)` on it
3. Look for:
   - Seq Scan on large tables (should be Index Scan)
   - High cost numbers
   - Sort operations on large datasets
   - Hash Join with large build side
   - Nested Loop with many iterations
4. Identify the bottleneck
5. Apply ONE fix at a time, re-measure

## Reading EXPLAIN
```
Seq Scan on todos  (cost=0.00..12540.00 rows=100000 width=...)
                        ^^^^^^^^^^^^^^^^^^^^^^^^^
                        high cost = bad
```

Look for:
- `Seq Scan` on tables > 10k rows → missing index
- `Index Scan` → good
- `Index Only Scan` → great (covering index)
- `Bitmap Heap Scan` → many rows matched, OK
- `Sort` on > 1k rows → add index for ORDER BY
- `Hash Join` → usually fine, but high memory on build side is bad
- `Nested Loop` → fine for small N, terrible for large N
- `HashAggregate` → may spill to disk if large

## Index Strategy

### Missing Index
```sql
-- Slow: SELECT * FROM todos WHERE user_id = '...' AND status = 'open'
EXPLAIN ANALYZE: Seq Scan on todos

-- Fix:
CREATE INDEX idx_todos_user_status ON todos(user_id, status);
```

### Covering Index
```sql
-- Slow: SELECT user_id, title FROM todos WHERE status = 'open'
-- Even with index on status, fetches the row from heap

-- Fix: INCLUDE the columns you need
CREATE INDEX idx_todos_status_covering ON todos(status) INCLUDE (user_id, title);
-- Now Index Only Scan
```

### Composite Index Column Order
- Equality columns first (`WHERE status = 'open'`)
- Range columns last (`WHERE created_at > '...'`)
- Sort columns match the index order
- `CREATE INDEX ON todos(user_id, status, created_at DESC)` covers:
  - `WHERE user_id = ? AND status = ? ORDER BY created_at DESC`

### Partial Index
```sql
-- Only index active todos (most queries filter this anyway)
CREATE INDEX idx_todos_active ON todos(user_id, status)
  WHERE deleted_at IS NULL;
```

### Expression Index
```sql
-- For case-insensitive email lookup
CREATE INDEX idx_users_email_lower ON users(LOWER(email));
```

## Query Rewriting

### Avoid SELECT *
```sql
-- Bad: SELECT * FROM users
-- Good: SELECT id, email, name FROM users
```
Less data to fetch, allows Index Only Scan.

### Avoid N+1
```sql
-- Bad (in a loop): SELECT * FROM todos WHERE user_id = ?
-- Good: SELECT * FROM todos WHERE user_id IN (?, ?, ?)
-- Best: JOIN
SELECT t.* FROM todos t
JOIN users u ON t.user_id = u.id
WHERE u.company_id = ?;
```

### Use LIMIT with ORDER BY
```sql
-- Bad: SELECT * FROM todos ORDER BY created_at DESC
-- Good: SELECT * FROM todos ORDER BY created_at DESC LIMIT 50
```
With a matching index, this can return in <1ms.

### Pagination: Keyset vs OFFSET
```sql
-- Slow (OFFSET scans and discards rows):
SELECT * FROM todos ORDER BY created_at DESC LIMIT 20 OFFSET 10000;

-- Fast (keyset pagination):
SELECT * FROM todos
WHERE created_at < '2024-01-01'
ORDER BY created_at DESC LIMIT 20;
```

### Avoid Functions on Indexed Columns
```sql
-- Bad (index not used): SELECT * FROM users WHERE EXTRACT(YEAR FROM created_at) = 2024
-- Good: SELECT * FROM users WHERE created_at >= '2024-01-01' AND created_at < '2025-01-01'
```

### Use EXISTS instead of IN for Subqueries
```sql
-- Often faster:
SELECT * FROM users u WHERE EXISTS (
  SELECT 1 FROM todos t WHERE t.user_id = u.id
);
```

## Connection Pooling
- Use PgBouncer for Postgres (transaction mode)
- Pool size: 10-30 per app instance (don't go crazy)
- Connection lifetime: 5-10 minutes
- Use a single Prisma Client instance per app

## Denormalization (Last Resort)
Only denormalize when:
- Joins are killing performance
- The denormalized data is read-heavy, write-light
- You can keep it consistent (triggers, app logic, materialized views)

```sql
-- Store user_name on todo to avoid JOIN
ALTER TABLE todos ADD COLUMN user_name TEXT;
-- Keep in sync with trigger
```

## Materialized Views
```sql
CREATE MATERIALIZED VIEW todo_counts AS
SELECT user_id, status, COUNT(*) as count
FROM todos
GROUP BY user_id, status;

CREATE UNIQUE INDEX ON todo_counts(user_id, status);

-- Refresh:
REFRESH MATERIALIZED VIEW CONCURRENTLY todo_counts;
```

## Forbidden Patterns
- Optimizing without EXPLAIN
- Applying multiple optimizations at once (can't measure impact)
- Adding indexes without checking if they're used
- `SELECT *` in production
- OFFSET pagination on large tables

## Output Format
1. Original slow query
2. EXPLAIN ANALYZE output
3. Diagnosis
4. Fix applied
5. EXPLAIN after fix
6. Before/after timing

