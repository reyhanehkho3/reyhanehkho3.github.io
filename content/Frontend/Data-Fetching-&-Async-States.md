---
title: Data Fetching and Async States
publish:
date created: 2026-09-10
tags:
  - frontend
  - basic
  - codeless
---
Frontend applications constantly communicate with APIs.

For example:

```
Frontend
   ↓
GET /api/tasks
   ↓
Backend
   ↓
Database
```

But the response doesn't arrive immediately.

Therefore, you have different states.

## Loading

The request hasn't finished.

```
Loading...
```

Example:

```
GET /api/tasks
       ↓
   loading = true
       ↓
   "Loading tasks..."
```

---

## Success

The request worked.

```
GET /api/tasks
       ↓
200 OK
       ↓
display tasks
```

---

## Error

Something went wrong.

```
GET /api/tasks
       ↓
500 Internal Server Error
       ↓
"Could not load tasks."
```

So conceptually:

```
        ┌── Loading
Request ┤
        ├── Success
        └── Error
```

### Example

```
TaskList

if loading:
    "Loading..."

else if error:
    "Failed to load tasks."

else:
    show tasks
```

### Why fetching tools exist

You can manually do:

```
fetch("/api/tasks")
```

But larger applications need more functionality:

```
fetch
├── caching
├── retries
├── refetching
├── request deduplication
├── stale data management
└── loading/error states
```

Tools/libraries such as TanStack Query help manage **server state and data fetching**.

The important concept isn't memorizing a particular library.

Understand:

> **Fetching data is asynchronous, so the UI must represent the different stages of the request.**

---
[[Frontend]]
[[My-Journey-In-Codeless]]