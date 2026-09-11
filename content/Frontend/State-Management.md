---
title: State Mangement
publish: true
date created: 2026-09-10
tags:
  - frontend
  - basic
  - codeless
---
**State** is information that can change while your application is running.

For example:

```
isMenuOpen = true
username = "Reyhaneh"
tasks = [...]
isLoading = false
```

There are three important categories.

---

## Local State

State that belongs to one component.

Example:

```
isDropdownOpen
```

Only the dropdown cares about it.

```
UserMenu
└── isDropdownOpen
```

You don't need a global state system for this.

### Example

```
Button clicked
     ↓
isDropdownOpen = true
     ↓
dropdown appears
```

---

## Global State

State shared by many unrelated components.

For example:

```
Current logged-in user
Theme
Shopping cart
Authentication state
```

You might have:

```
Navbar ─────┐
            │
Dashboard ──┼──→ User State
            │
Profile ────┘
```

A state-management library/store can hold this shared state.

In Vue, for example, **Pinia** is commonly used.

---

## Server State

This is slightly different.

Server state is data that **belongs to your backend/database** and is retrieved through an API.

For example:

```
GET /api/tasks
```

returns:

```
[
  {
    "id": 1,
    "title": "Fix login bug"
  }
]
```

That data is server state.

It can become outdated:

```
Frontend: task = "Fix login bug"

Backend:
task was renamed to "Fix authentication bug"
```

Now your frontend has stale data.

That's why server state often needs things like:

- caching
- refetching
- synchronization
- invalidation
- retrying

### Simple comparison

|Type|Example|Usually belongs to|
|---|---|---|
|Local state|Is menu open?|Component|
|Global state|Current user|Frontend|
|Server state|List of tasks|Backend/database|

### Very important idea

Don't put **everything** into global state.

For example:

```
isDropdownOpen
```

probably doesn't belong in your global store.

---
[[Frontend]]
[[My-Journey-In-Codeless]]