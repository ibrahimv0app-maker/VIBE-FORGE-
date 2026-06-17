---
name: state-management-zustand-architect
description: Use when managing client state in React — global app state, feature stores, derived state. Prefers Zustand for simplicity; uses React Query for server state.
---

        # State Management — Zustand Architect

        Zustand is the right default for client state. React Query for server state. Context only for dependency injection.

        ## When to Use What
        | Need | Use |
        |------|-----|
        | Server data (API responses, cache) | React Query / SWR |
        | Client state (UI, form, filters) | Zustand |
        | Truly global app state (theme, auth) | Zustand |
        | Cross-component prop passing | Context (only if not state) |
        | Form state | react-hook-form |
| URL state (filters, pagination) | URL search params |

        ## Zustand Store Pattern
        ```ts
        interface BearStore {
          bears: number
          addBear: () => void
          removeBear: () => void
          reset: () => void
        }

        export const useBearStore = create<BearStore>((set) => ({
          bears: 0,
          addBear: () => set((s) => ({ bears: s.bears + 1 })),
          removeBear: () => set((s) => ({ bears: Math.max(0, s.bears - 1) })),
          reset: () => set({ bears: 0 }),
        }))
        ```

        ## Selectors (Performance)
        ```tsx
        // BAD: subscribes to entire store, re-renders on any change
        const store = useBearStore()

        // GOOD: subscribes only to bears
        const bears = useBearStore((s) => s.bears)
        const addBear = useBearStore((s) => s.addBear)

        // GOOD: shallow for multiple values
        const { bears, addBear } = useBearStore(useShallow((s) => ({ bears: s.bears, addBear: s.addBear })))
        ```

        ## Sliced Stores (Domain Separation)
        Don't put everything in one store. Slice by domain:
        ```ts
        export const useAuthStore = create<AuthStore>(authSlice)
        export const useCartStore = create<CartStore>(cartSlice)
        export const useUIStore = create<UIStore>(uiSlice)
        ```

        ## Persisted Store
        ```ts
        export const useAuthStore = create<AuthStore>()(
          persist(
            (set) => ({
              user: null,
              setUser: (user) => set({ user }),
              logout: () => set({ user: null }),
            }),
            {
              name: 'auth-storage',
              partialize: (state) => ({ user: state.user }), // only persist user, not functions
            }
          )
        )
        ```

        ## Async Actions
        ```ts
        export const useUserStore = create<UserStore>((set, get) => ({
          user: null,
          loading: false,
          error: null,
          fetchUser: async (id: string) => {
            set({ loading: true, error: null })
            try {
              const user = await api.getUser(id)
              set({ user, loading: false })
            } catch (e) {
              set({ error: e.message, loading: false })
            }
          },
        }))
        ```

        ## Derived State
        ```ts
        // Compute in selector, not in store
        const cartTotal = useCartStore((s) =>
          s.items.reduce((sum, i) => sum + i.price * i.qty, 0)
        )
        ```

        ## Devtools
        ```ts
        import { devtools } from 'zustand/middleware'
        export const useStore = create(devtools((set) => ({ ... })))
        ```

        ## Testing
        ```ts
        // Reset store between tests
        afterEach(() => {
          useStore.setState(initialState)
        })
        ```

        ## Forbidden Patterns
        - Putting server state in Zustand (use React Query)
        - Subscribing to the whole store
        - Storing derived values (compute in selectors)
        - Mutating state directly (always use `set`)
        - Storing functions in persisted state

        ## Output Format
        1. Store interface
        2. Store implementation
        3. Selector examples
        4. Persistence setup (if needed)

