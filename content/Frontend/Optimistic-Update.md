---
title: Optimistic Update
publish: true
date created: 2026-09-10
tags:
  - frontend
  - basic
  - codeless
---
An **optimistic update** is a frontend technique where you **update the UI immediately, before the server confirms that the operation succeeded**.

The idea is:

> "I expect this request to succeed, so I'll show the user the result immediately."

### Example: Like button

Suppose you click ❤️:

#### Normal update

```text
User clicks Like
      ↓
Send request to API
      ↓
Wait...
      ↓
Server says "success"
      ↓
UI changes ❤️
```

The user may experience a delay.

#### Optimistic update

```text
User clicks Like
      ↓
UI immediately changes ❤️
      ↓
Send request to API
      ↓
Server says "success" ✅
```

It feels much faster.

---

## What if the request fails?

You **roll back** the UI.

```text
User clicks Like
      ↓
UI → ❤️ immediately
      ↓
API request
      ↓
❌ Request failed
      ↓
UI → ♡
```

So the basic pattern is:

```text
1. Update UI immediately
        ↓
2. Send request
        ↓
3. Success → keep the change
        ↓
4. Failure → undo the change
```

---

## Example: Deleting a task

Imagine:

```text
Tasks:

☐ Fix login
☐ Add dashboard
☐ Write tests
```

User clicks **Delete** on "Fix login".

With optimistic updating:

```text
Click Delete
    ↓
Remove "Fix login" from UI immediately
    ↓
DELETE /api/tasks/123
    ↓
       ┌── Success → done ✅
       │
       └── Failure → put task back ❌
```

The user doesn't have to wait for the network before seeing the task disappear.

---

## Why is it called "optimistic"?

Because the frontend is being **optimistic**:

> "I'm going to assume the server will accept this."

If you're wrong, you correct the UI.

---

## When is it useful?

Especially for actions that:

- usually succeed
    
- should feel instant
    
- have a simple rollback
    

Examples:

```text
❤️ Like a post
⭐ Favorite an item
☑️ Complete a task
🗑️ Delete a notification
➕ Add an item
```

It's less appropriate when an operation has complicated consequences or a high chance of failure.

---

### One important distinction

Optimistic **update** isn't the same as optimistic **UI rendering**.

**Optimistic update:**

```text
UI changes before server confirmation.
```

**Normal server-driven update:**

```text
Server confirms → UI changes.
```

So when you're learning data fetching, you can think of optimistic updates as another technique alongside:

```text
Fetching
├── Loading states
├── Error handling
├── Caching
├── Retrying
├── Refetching
└── Optimistic updates
```

Libraries like **TanStack Query** provide mechanisms for implementing optimistic updates.


---
[[Frontend]]
[[My-Journey-In-Codeless]]