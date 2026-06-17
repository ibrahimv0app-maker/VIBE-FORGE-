---
name: nextjs-app-router-architect
description: Use when building Next.js 14/15 apps with the App Router. Always uses Server Components by default, Client Components only when needed, proper data fetching, and route handlers.
---

# Next.js App Router Architect

App Router flips the model: Server Components by default, Client Components opt-in.

## Component Decision
- **Server Component (default)**: data fetching, static content, no interactivity
- **Client Component (`'use client'`)**: state, effects, event handlers, browser APIs

## Page Pattern (Server Component)
```tsx
// app/todos/page.tsx — Server Component
import { Suspense } from 'react'
import { TodoList } from './TodoList'
import { TodoForm } from './TodoForm'
import { getTodos } from '@/lib/api'

export const revalidate = 60 // ISR

export default async function TodosPage({ searchParams }: { searchParams: { status?: string } }) {
  const todos = await getTodos(searchParams)

  return (
    <main className="container mx-auto p-6">
      <h1>Todos</h1>
      <TodoForm />
      <Suspense fallback={<TodoListSkeleton />}>
        <TodoList initialTodos={todos} />
      </Suspense>
    </main>
  )
}
```

## Client Component
```tsx
// app/todos/TodoForm.tsx
'use client'

import { useState } from 'react'
import { useToast } from '@/components/ui/use-toast'

export function TodoForm() {
  const [title, setTitle] = useState('')
  const { toast } = useToast()

  const onSubmit = async (e: React.FormEvent) => {
    e.preventDefault()
    // mutation
  }

  return <form onSubmit={onSubmit}>...</form>
}
```

## Loading States (Streaming)
```tsx
// app/todos/loading.tsx — automatically used as Suspense fallback
export default function Loading() {
  return <TodoListSkeleton />
}
```

## Error Boundary
```tsx
// app/todos/error.tsx — must be a Client Component
'use client'

export default function Error({ error, reset }: { error: Error; reset: () => void }) {
  return (
    <div>
      <h2>Something went wrong</h2>
      <button onClick={reset}>Try again</button>
    </div>
  )
}
```

## Route Handlers (API)
```ts
// app/api/todos/route.ts
import { NextRequest, NextResponse } from 'next/server'
import { z } from 'zod'
import { getServerSession } from 'next-auth'

const CreateTodo = z.object({
  title: z.string().min(1).max(200),
})

export async function POST(req: NextRequest) {
  const session = await getServerSession()
  if (!session) return NextResponse.json({ error: 'Unauthorized' }, { status: 401 })

  const body = await req.json()
  const parsed = CreateTodo.safeParse(body)
  if (!parsed.success) {
    return NextResponse.json({ error: parsed.error.flatten() }, { status: 400 })
  }

  const todo = await db.todo.create({ data: { ...parsed.data, userId: session.user.id } })
  return NextResponse.json(todo, { status: 201 })
}
```

## Data Fetching Patterns
- **Server Component fetch**: `await db.query()` directly
- **Server Action**: form submissions, mutations
- **Route Handler**: external API consumers, webhooks
- **Client-side fetch**: only for data that changes frequently and isn't SEO-relevant

## Server Actions
```tsx
'use server'

import { revalidatePath } from 'next/cache'
import { z } from 'zod'

export async function createTodo(formData: FormData) {
  const parsed = CreateTodoSchema.parse({
    title: formData.get('title'),
  })
  await db.todo.create({ data: parsed })
  revalidatePath('/todos')
}
```

## Metadata
```tsx
// app/todos/page.tsx
export const metadata: Metadata = {
  title: 'Todos',
  description: 'Manage your todos',
}

// Dynamic
export async function generateMetadata({ params }): Promise<Metadata> {
  const todo = await getTodo(params.id)
  return { title: todo.title }
}
```

## Layout Nesting
```
app/
├── layout.tsx          # root layout (html, body)
├── (marketing)/
│   ├── layout.tsx      # marketing layout (nav + footer)
│   ├── page.tsx        # homepage
│   └── about/page.tsx
├── (app)/
│   ├── layout.tsx      # app layout (sidebar)
│   └── dashboard/page.tsx
└── api/
```

## Performance Rules
- Default to Server Components (less JS shipped)
- Use `next/image` for all images
- Use `next/font` for fonts
- Use `next/link` for navigation
- Use `dynamic(() => import(...), { ssr: false })` for client-only components
- Stream with Suspense for slow data

## Forbidden Patterns
- `'use client'` at the top of every file
- Calling `db` from Client Components
- Not handling loading / error states
- Fetching the same data in multiple Server Components (use cache)
- Using `useEffect` for data fetching

## Output Format
1. File structure
2. Server Component code
3. Client Component code (if needed)
4. Loading / error boundaries
5. Metadata

