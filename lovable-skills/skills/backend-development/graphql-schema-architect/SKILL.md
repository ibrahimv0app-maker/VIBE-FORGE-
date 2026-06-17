---
name: graphql-schema-architect
description: Use when designing GraphQL schemas — types, queries, mutations, subscriptions, resolvers. Always follows schema-first design, naming conventions, and Relay-style connections.
---

# GraphQL Schema Architect

GraphQL schemas are read more than they are written. Optimize for readability.

## Naming Conventions
- Types: PascalCase (`User`, `Todo`, `TodoConnection`)
- Fields: camelCase (`createdAt`, `displayName`)
- Enums: PascalCase values (`TodoStatus.OPEN`, `TodoStatus.DONE`)
- Mutations: verb + noun (`createTodo`, `updateTodo`, `deleteTodo`)
- Input types: `<Type>Input` (`CreateTodoInput`, `UpdateTodoInput`)

## Type Definitions
```graphql
type Todo {
  id: ID!
  title: String!
  description: String
  status: TodoStatus!
  assignee: User
  createdAt: DateTime!
  updatedAt: DateTime!
}

enum TodoStatus {
  OPEN
  IN_PROGRESS
  DONE
  CANCELLED
}

scalar DateTime
```

## Queries
```graphql
type Query {
  todo(id: ID!): Todo
  todos(first: Int, after: String, filter: TodoFilter): TodoConnection!
}

input TodoFilter {
  status: TodoStatus
  assigneeId: ID
  search: String
}
```

## Connections (Relay-style pagination)
```graphql
type TodoConnection {
  edges: [TodoEdge!]!
  pageInfo: PageInfo!
  totalCount: Int!
}

type TodoEdge {
  node: Todo!
  cursor: String!
}

type PageInfo {
  hasNextPage: Boolean!
  hasPreviousPage: Boolean!
  startCursor: String
  endCursor: String
}
```

## Mutations
```graphql
type Mutation {
  createTodo(input: CreateTodoInput!): CreateTodoPayload!
  updateTodo(input: UpdateTodoInput!): UpdateTodoPayload!
  deleteTodo(input: DeleteTodoInput!): DeleteTodoPayload!
}

input CreateTodoInput {
  title: String!
  description: String
  assigneeId: ID
}

type CreateTodoPayload {
  todo: Todo
  errors: [UserError!]!
}

type UserError {
  field: String
  message: String!
}
```

## Mutation Payload Pattern
Every mutation returns a payload with:
- The mutated entity (nullable, in case of error)
- An errors array (empty if success)
- Optional: `clientMutationId` for Relay

## Subscriptions
```graphql
type Subscription {
  todoUpdated(id: ID!): Todo!
  todoCreated: Todo!
}
```

## Resolver Pattern
```ts
export const resolvers = {
  Query: {
    todo: async (_, { id }, ctx) => ctx.dataSources.todos.get(id),
    todos: async (_, { first, after, filter }, ctx) => {
      const { edges, pageInfo, totalCount } = await ctx.dataSources.todos.list({ first, after, filter })
      return { edges, pageInfo, totalCount }
    },
  },
  Mutation: {
    createTodo: async (_, { input }, ctx) => {
      ctx.requireAuth()
      try {
        const todo = await ctx.dataSources.todos.create({ ...input, userId: ctx.user.id })
        return { todo, errors: [] }
      } catch (e) {
        return { todo: null, errors: [{ field: null, message: e.message }] }
      }
    },
  },
  Todo: {
    assignee: async (todo, _, ctx) => ctx.dataSources.users.get(todo.assigneeId),
  },
}
```

## DataLoader (N+1 Prevention)
```ts
const userLoader = new DataLoader(async (ids: string[]) => {
  const users = await db.users.findMany({ where: { id: { in: ids } } })
  return ids.map(id => users.find(u => u.id === id))
})

Todo: {
  assignee: (todo, _, ctx) => ctx.loaders.user.load(todo.assigneeId),
}
```

## Schema Design Rules
- Start with the UI's data needs, not the database
- Use custom scalars for typed values (`DateTime`, `URL`, `Email`, `UUID`)
- Avoid `JSON` scalar unless absolutely necessary
- Make nullable fields that can fail (`assignee: User` not `assignee: User!`)
- Use enums for fixed value sets
- Version by adding fields, never removing or renaming (use deprecation)

## Deprecation
```graphql
type Todo {
  title: String! @deprecated(reason: "Use `name` instead.")
  name: String!
}
```

## Security
- Authentication at resolver level, not field level (mostly)
- Field-level auth for sensitive fields (`User.email`, `User.paymentMethod`)
- Rate limit mutations separately from queries
- Query depth limiting (prevent malicious nested queries)
- Query complexity scoring for expensive queries

## Forbidden Patterns
- `JSON` scalar everywhere (defeats the point of GraphQL)
- Exposing database tables directly (design for the client)
- N+1 queries (always use DataLoader)
- Mutations that return scalars (always return a payload type)
- Cycles in the schema (Todo → User → Todo → ...)

## Output Format
1. Schema (type definitions)
2. Resolvers
3. DataLoader setup
4. Example query and response

