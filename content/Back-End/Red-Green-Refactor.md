---
title: Red/Green Refactor
publish:
date created: 2026-09-11
tags:
  - Backend
  - test
---

The **Red → Green → Refactor** cycle is the core cycle of **TDD (Test-Driven Development)**.

```text
        ┌──────────────┐
        │     RED      │
        │ Write a test │
        └──────┬───────┘
               ↓
        ┌──────────────┐
        │    GREEN     │
        │ Make it pass │
        └──────┬───────┘
               ↓
        ┌──────────────┐
        │  REFACTOR    │
        │ Improve code │
        └──────┬───────┘
               │
               └────────→ RED
```

### 1. 🔴 Red — Write a failing test

First, write a test for something that **doesn't exist yet**.

Example:

```js
test("adds two numbers", () => {
  expect(add(2, 3)).toBe(5);
});
```

You run it:

```text
❌ FAIL
add() doesn't exist
```

That's **Red**.

---

### 2. 🟢 Green — Make the test pass

Now write the **simplest code possible** to make the test pass.

```js
function add(a, b) {
  return a + b;
}
```

Run the test:

```text
✅ PASS
```

That's **Green**.

The goal here isn't beautiful code. It's simply:

> **Make the test pass.**

---

### 3. 🔵 Refactor — Improve the code

Now that you have a passing test, you can improve the implementation:

- remove duplication
    
- improve naming
    
- simplify logic
    
- reorganize code
    
- improve structure
    

While doing this, keep running the tests.

```text
Before refactoring
      ↓
✅ Tests pass
      ↓
Refactor
      ↓
✅ Tests still pass
```

The important rule is:

> **Don't change the behavior while refactoring.**

---

### Then repeat

Once you're done:

```text
🔴 Write another test
        ↓
🟢 Make it pass
        ↓
🔵 Refactor
        ↓
🔴 Next test
        ↓
...
```

### Why is it useful?

It gives you a controlled development loop:

```text
Test defines behavior
       ↓
Implementation satisfies behavior
       ↓
Tests protect behavior
       ↓
Code can safely be improved
```

That's why the cycle is often summarized as:

> **Red → Green → Refactor → Repeat**.


---
[[Back-End]]
[[Test]]