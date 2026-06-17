---
name: react-query-server-state-architect
description: Use when fetching, caching, or mutating server data in React. Always uses TanStack React Query with proper cache keys, invalidation, optimistic updates, and loading/error states.
---

# React Query Server State Architect

Server state is fundamentally different from client state. Treat it differently.

## Setup
```tsx
const queryClient = new QueryClient({
  defaultOptions: {
    queries: {
      staleTime: 60_000, // 1 minute
      gcTime: 5 * 60_000, // 5 minutes
      retry: 2,
      refetchOnWindowFocus: false,
    },
  },
})

<QueryClientProvider client={queryClient}>
  <App />
</QueryClientProvider>
```

## Query Key Convention
```ts
// Hierarchical, type-safe
const queryKeys = {
  todos: ['todos'] as const,
  todoList: (filters: TodoFilters) => [...queryKeys.todos, 'list', filters] as const,
  todoDetail: (id: string) => [...queryKeys.todos, 'detail', id] as const,
}
```

## Standard Query Hook
```ts
export function useTodos(filters: TodoFilters) {
  return useQuery({
    queryKey: queryKeys.todoList(filters),
    queryFn: () => api.todos.list(filters),
    placeholderData: keepPreviousData, // for pagination
  })
}
```

## Standard Mutation Hook
```ts
export function useCreateTodo() {
  const queryClient = useQueryClient()
  return useMutation({
    mutationFn: api.todos.create,
    onMutate: async (newTodo) => {
      await queryClient.cancelQueries({ queryKey: queryKeys.todos })
      const previous = queryClient.getQueryData<Todo[]>(queryKeys.todoList({}))
      queryClient.setQueryData<Todo[]>(queryKeys.todoList({}), (old = []) => [...old, newTodo])
      return { previous }
    },
    onError: (_err, _newTodo, context) => {
      queryClient.setQueryData(queryKeys.todoList({}), context?.previous)
    },
    onSettled: () => {
      queryClient.invalidateQueries({ queryKey: queryKeys.todos })
    },
  })
}
```

## Loading / Error States in Component
```tsx
function TodoList() {
  const { data, isLoading, isError, error, refetch } = useTodos({})

  if (isLoading) return <Skeleton />
  if (isError) return <ErrorState onRetry={() => refetch()} message={error.message} />
  if (!data.length) return <EmptyState />

  return data.map(t => <TodoItem key={t.id} todo={t} />)
}
```

## Pagination
```tsx
const { data, fetchNextPage, hasNextPage, isFetchingNextPage } = useInfiniteQuery({
  queryKey: queryKeys.todoList({ status }),
  queryFn: ({ pageParam }) => api.todos.list({ page: pageParam, status }),
  initialPageParam: 1,
  getNextPageParam: (last) => last.nextPage,
})
```

## Prefetching
```tsx
// On hover, prefetch the detail
const prefetchTodo = (id: string) => {
  queryClient.prefetchQuery({
    queryKey: queryKeys.todoDetail(id),
    queryFn: () => api.todos.get(id),
  })
}
```

## Optimistic Updates
- Update the cache immediately
- Roll back on error
- Always invalidate on settled to reconcile

## Invalidation Patterns
```ts
// Invalidate all todo queries
queryClient.invalidateQueries({ queryKey: queryKeys.todos })

// Invalidate specific list
queryClient.invalidateQueries({ queryKey: queryKeys.todoList({ status: 'open' }) })

// Invalidate everything
queryClient.invalidateQueries()
```

## Stale Time Strategy
- Real-time data (chat, prices): 0 (always refetch)
- User-generated content (todos, posts): 30s
- Reference data (settings, profile): 5min
- Static data (config, enums): Infinity (use `gcTime`)

## Forbidden Patterns
- `useEffect` + `fetch` (use React Query)
- Mutation without invalidation
- Hardcoded query keys (use a keys object)
- Disabling retry globally (set per-query)
- Calling `setQueryData` without `onError` rollback

## Output Format
1. Query keys object
2. Query hook
3. Mutation hook (with optimistic update)
4. Component usage

