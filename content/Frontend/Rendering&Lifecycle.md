---
title: Rendering and Lifecycle
publish: true
date created: 2026-09-10
tags:
  - frontend
  - basic
  - codeless
---
A component has a **lifecycle**.

Conceptually:

```
Component created
      ↓
Rendered
      ↓
Updated
      ↓
Destroyed
```

---

## Effects

An effect is code that runs because something happened or something changed.

For example:

```
Component mounted
       ↓
fetch user data
```

Or:

```
userId changed
       ↓
fetch new user
```

In React you encounter:

```
useEffect(...)
```

In Vue you'll encounter things such as:

```
onMounted(...)
watch(...)
watchEffect(...)
```

The important question is:

> **What causes this code to run?**

For example:

```
onMounted()
```

runs after the component is mounted.

A watcher can run when a particular reactive value changes.

---

## Preventing unnecessary re-renders

Imagine:

```
Parent
├── Header
├── TaskList
├── UserList
└── Footer
```

If something changes in the parent, you don't necessarily want expensive work to happen everywhere.

You therefore learn techniques such as:

- memoization
- stable props
- computed values
- avoiding unnecessary state
- avoiding expensive calculations during rendering

---

## CSR

**Client-Side Rendering**

The browser receives JavaScript and the frontend builds the UI.

```
Server
  ↓
HTML/JS
  ↓
Browser
  ↓
JavaScript runs
  ↓
UI appears
```

Typical SPA applications use CSR heavily.

---

## SSR

**Server-Side Rendering**

The server generates HTML first.

```
Browser
  ↓
Request
  ↓
Server
  ↓
HTML
  ↓
Browser
```

The browser can display meaningful HTML sooner.

Frameworks such as Next.js and Nuxt support SSR.

---

## Hydration

With SSR, the server may send HTML like:

```
<button>Like</button>
```

The browser can display it, but the HTML isn't yet fully connected to your JavaScript behavior.

**Hydration** is when the frontend JavaScript attaches the application behavior to the server-rendered HTML.

Conceptually:

```
SSR
 ↓
HTML arrives
 ↓
Browser displays HTML
 ↓
JavaScript loads
 ↓
Hydration
 ↓
Interactive application
```


---
[[Frontend]]
[[My-Journey-In-Codeless]]