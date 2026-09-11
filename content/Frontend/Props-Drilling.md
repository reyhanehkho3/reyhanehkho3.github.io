---
title: Props Drilling
publish:
date created: 2026-09-10
tags:
  - frontend
  - basic
  - codeless
---
**Props drilling** means passing data through multiple components **just to get it from a higher-level component to a deeply nested component**, even though the components in between don't actually need the data.

### Simple example

Imagine:

```
App
 ↓
Dashboard
 ↓
TaskList
 ↓
TaskCard
```

`App` has the user's name:

```
userName = "Reyhaneh"
```

But `TaskCard` needs it.

So you pass it through every component:

```
App
 └─ userName
      ↓
Dashboard
 └─ userName
      ↓
TaskList
 └─ userName
      ↓
TaskCard
 └─ userName
```

In Vue, it might look like:

```
<!-- App -->
<Dashboard :user-name="userName" />
```

Then:

```
<!-- Dashboard -->
<TaskList :user-name="userName" />
```

Then:

```
<!-- TaskList -->
<TaskCard :user-name="userName" />
```

Finally:

```
<!-- TaskCard -->
<p>Hello {{ userName }}</p>
```

The problem is that **Dashboard and TaskList don't care about `userName`**. They're just carrying it along.

That's **props drilling**.

---

### Example 2

Imagine:

```
App
 ↓
Layout
 ↓
Sidebar
 ↓
UserProfile
```

You want `UserProfile` to know the current user:

```
App
  user
   ↓
Layout
  user
   ↓
Sidebar
  user
   ↓
UserProfile
```

But `Layout` and `Sidebar` don't actually use `user`.

That becomes annoying when you have:

```
App
 ↓
A
 ↓
B
 ↓
C
 ↓
D
 ↓
E
```

and you have to pass the same prop through all five levels.


---
[[Frontend]]
[[My-Journey-In-Codeless]]