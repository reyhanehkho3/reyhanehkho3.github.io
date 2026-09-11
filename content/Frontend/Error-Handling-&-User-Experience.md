---
title: Error Handling and User Experience
publish: true
date created: 2026-09-10
tags:
  - frontend
  - basic
  - codeless
---
Errors are not just backend problems.

Your frontend needs to handle them gracefully.

---

## Error Boundary

An **Error Boundary** catches certain errors occurring during rendering/component execution so that one broken part of the UI doesn't necessarily destroy the entire application.

Instead of:

```
Application crashes 💥
```

you might show:

```
Something went wrong.

[Try again]
```

Conceptually:

```
Application
├── Navbar
├── TaskList ← error
└── Footer

        ↓

Error Boundary
        ↓

"Something went wrong"
```

This concept is especially associated with React; Vue has its own error-handling mechanisms rather than React's `ErrorBoundary` API.

---

# Empty State

An **empty state** is not an error.

For example:

```
GET /api/tasks
       ↓
200 OK
       ↓
[]
```

The request succeeded.

There are simply no tasks.

Bad UX:

```
[blank screen]
```

Better:

```
No tasks yet.

Create your first task.

[Create Task]
```

That's an empty state.

---

# User Feedback

The user should know what happened.

For example:

### Loading

```
Loading tasks...
```

### Success

```
✓ Task created successfully
```

### Validation error

```
Email is required.
```

### API error

```
Could not save the task.
Please try again.
```

### Empty state

```
You don't have any tasks yet.
```

The goal is:

> **Never make the user guess what the application is doing.**



---
[[Frontend]]
[[My-Journey-In-Codeless]]