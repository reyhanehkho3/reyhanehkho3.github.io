---
title: Hook
publish: true
date created: 2026-09-11
tags:
  - frontend
  - basic
  - codeless
---
In frontend, a **hook** is a function that lets a component **use or “hook into” a feature of the framework**.

You’ll hear this term especially with **React**, where hooks are a major concept.

### Simple example

Normally, a component is just UI:

```text
Component
   ↓
renders UI
```

A hook lets it access things like:

```text
Component
   │
   ├── state
   ├── lifecycle
   ├── context
   └── other framework features
```

For example, React's `useState`:

```js
const [count, setCount] = useState(0);
```

Here:

- `count` = current state
    
- `setCount` = changes the state
    
- `useState()` = **hook**
    

Without the hook, the component wouldn't have React-managed state in this way.

### Another example: `useEffect`

```js
useEffect(() => {
  fetchUsers();
}, []);
```

`useEffect` lets you run code as a **side effect** of the component lifecycle.

For example:

```text
Component appears
       ↓
useEffect runs
       ↓
fetch users
       ↓
update state
       ↓
UI updates
```

### Custom hooks

You can also create your own hooks to reuse logic.

Instead of repeating authentication logic:

```text
Component A ──┐
Component B ──┼── authentication logic
Component C ──┘
```

you can create:

```js
useAuth()
```

and then:

```js
const { user, logout } = useAuth();
```

Multiple components can reuse that logic.

### Hook vs component

This distinction is important:

**Component:**

> Reusable **UI**

```text
<Button />
<UserProfile />
<Navbar />
```

**Hook:**

> Reusable **logic**

```text
useAuth()
useFetch()
useForm()
useLocalStorage()
```

So a good mental model is:

> **Component = reusable UI**  
> **Hook = reusable component logic**

---
[[Frontend]]
[[My-Journey-In-Codeless]]