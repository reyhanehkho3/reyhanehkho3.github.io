---
title: Performance
publish: true
date created: 2026-09-10
tags:
  - frontend
  - basic
  - codeless
---
Performance means making the application do **less unnecessary work** and load only what is needed.

---

## Memoization

Memoization means:

> **Remember the result of an expensive calculation so you don't have to calculate it again unnecessarily.**

Imagine:

```
calculateStatistics(10,000 tasks)
```

takes 100ms.

If the inputs haven't changed:

```
same input
   ↓
use previous result
```

instead of calculating again.

In frontend frameworks you'll encounter things like:

```
computed values
memoized components
memoized functions
```

depending on the framework.

---

## Code splitting

Instead of sending the entire application to the browser at once:

```
1 MB JavaScript
```

you can split it:

```
main.js
tasks.js
admin.js
reports.js
```

Then load `admin.js` only when the user visits the admin section.

---

## Lazy loading

Lazy loading means:

> **Don't load something until it is actually needed.**

For example:

```
User opens application

Load:
✓ Dashboard
✓ Navbar

Don't load:
✗ Admin panel
✗ Reports
✗ Settings
```

When the user opens Reports:

```
load reports.js
```

This can significantly improve initial load performance for large applications.

---

## Preventing extra computations

Suppose you have:

```
const expensiveResult = calculateSomething(tasks)
```

and `tasks` haven't changed.

There's no reason to repeatedly calculate it just because some unrelated UI state changed.

So performance optimization is largely about:

```
What changed?
      ↓
What actually needs to update?
      ↓
Do only that work.
```

### Important warning

Don't blindly optimize everything.

First understand the application and identify actual bottlenecks.



---
[[Frontend]]
[[My-Journey-In-Codeless]]