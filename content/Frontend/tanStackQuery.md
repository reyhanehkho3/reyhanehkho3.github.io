---
title: tanStackQuery
publish: true
date created: 2026-09-11
tags:
  - frontend
  - codeless
---
**TanStack Query** is a frontend library for managing **server state** — data that comes from an API/backend.

The simplest mental model:

> **TanStack Query = a smart manager for fetching, caching, updating, and synchronizing API data.**

### Without TanStack Query

Suppose you need users from your backend:

```js
const [users, setUsers] = useState([])
const [loading, setLoading] = useState(false)
const [error, setError] = useState(null)

async function fetchUsers() {
  setLoading(true)

  try {
    const response = await fetch("/api/users")
    setUsers(await response.json())
  } catch (err) {
    setError(err)
  } finally {
    setLoading(false)
  }
}
```

You then have to think about:

- Loading
    
- Errors
    
- Caching
    
- Refetching
    
- Retry
    
- Stale data
    
- Pagination
    
- Mutations
    
- Keeping multiple components synchronized
    

TanStack Query handles much of this for you.

---

### With TanStack Query

Conceptually:

```js
const { data, isLoading, error } = useQuery({
  queryKey: ["users"],
  queryFn: fetchUsers
})
```

Now TanStack Query manages the server data:

```text
                Backend API
                    │
                    ▼
             TanStack Query
                    │
          ┌─────────┼─────────┐
          ▼         ▼         ▼
        Cache     Loading    Error
          │
          ▼
       Component
```

### Why is the cache important?

Imagine two components need the same users:

```text
Navbar ────────┐
               │
Dashboard ─────┼──► TanStack Query ──► API
               │          │
UserList ──────┘          ▼
                         Cache
```

Instead of each component independently requesting:

```text
GET /api/users
GET /api/users
GET /api/users
```

TanStack Query can reuse the cached result when appropriate.

---

### It also handles mutations

For example:

```text
POST /api/tasks
PUT /api/tasks/123
DELETE /api/tasks/123
```

TanStack Query has **mutations** for operations that change server data.

A common flow is:

```text
User clicks "Delete"
       ↓
Mutation
       ↓
DELETE /api/tasks/123
       ↓
Success
       ↓
Invalidate/refetch tasks
       ↓
UI shows updated list
```

### TanStack Query vs state management

This distinction is **very important**.

**Local/UI state:**

```text
Is modal open?
Selected tab?
Input value?
Dropdown open?
```

Usually handled by React/Vue state.

**Server state:**

```text
Users from API
Tasks from API
Projects from API
Current profile from API
```

TanStack Query is designed specifically for this second category.

```text
Frontend State
│
├── UI state
│     └── useState / Pinia / etc.
│
└── Server state
      └── TanStack Query
```

### Why you were hearing about it with "fetch libraries"

You previously asked about **fetch libraries with caching, retry, etc.** TanStack Query is one of the major examples.

It provides things like:

- Fetching
    
- Caching
    
- Automatic refetching
    
- Retry
    
- Loading/error states
    
- Pagination/infinite queries
    
- Mutations
    
- Cache invalidation
    
- Optimistic updates
    
- Synchronization between components
    

So:

> **`fetch()`** = "Make this HTTP request."

> **TanStack Query** = "Manage the whole lifecycle of this server data."


---
[[Frontend]]
[[My-Journey-In-Codeless]]