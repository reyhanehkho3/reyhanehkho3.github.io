---
title: Composable
publish:
date created: 2026-09-11
tags:
  - frontend
  - basic
  - codeless
---
In frontend, **composable** means:

> **You can combine small pieces of logic or UI together to build something more complex.**

Think **LEGO blocks** 🧱.

### 1. Composable components

Instead of making one huge component:

```text
UserPage
 ├── header
 ├── profile
 ├── posts
 ├── comments
 └── buttons
```

you make smaller components:

```text
UserPage
 ├── Header
 ├── Profile
 ├── PostList
 │    └── Post
 └── CommentList
      └── Comment
```

Then you can reuse them:

```text
Profile → UserPage
Profile → Sidebar
Profile → Settings
```

That's **component composition**.

---

### 2. Composable logic

This is especially common with **Vue composables**.

Suppose several components need authentication logic:

```text
LoginPage
Dashboard
Navbar
Settings
```

Instead of putting authentication logic into each component, you create:

```js
useAuth()
```

Then:

```js
const { user, login, logout } = useAuth()
```

Each component can use the same logic.

```text
             useAuth()
            /    |    \
           /     |     \
      Login   Navbar   Dashboard
```

That's **composable logic**.

### Hook vs composable

The concepts are very similar:

|React|Vue|
|---|---|
|Hook|Composable|
|`useAuth()`|`useAuth()`|
|`useFetch()`|`useFetch()`|
|`useLocalStorage()`|`useLocalStorage()`|

The terminology differs, but the idea is similar: **extract reusable logic that can be combined and reused.**

### The important idea

When frontend developers say:

> "Make this composable."

They often mean:

> **Don't put everything into one giant component. Break the logic/UI into small reusable pieces that can be combined.**

For example:

```text
❌ Huge component
UserDashboard
 ├── authentication logic
 ├── fetching logic
 ├── pagination logic
 ├── form logic
 ├── notification logic
 └── UI

✅ Composable design
UserDashboard
 ├── useAuth()
 ├── useUsers()
 ├── usePagination()
 ├── useForm()
 └── UI components
```

So the mental model is:

**Composable = small, reusable pieces that can be combined to create larger functionality.**


---
[[Frontend]]
[[My-Journey-In-Codeless]]