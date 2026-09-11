---
title: Code Smell
publish: true
date created: 2026-09-11
tags:
  - Backend
  - codeless
---
A **code smell** is a sign in code that **something might be poorly designed or difficult to maintain**.

It doesn't necessarily mean the code is **wrong** or has a bug. It means: **“This code deserves a closer look.”**

### Simple example

```js
function createUser(name, email, age, address, phone, role, country) {
    // ...
}
```

Having **too many parameters** can be a code smell. It might indicate that the function is doing too much or that the data should be grouped into an object.

For example:

```js
function createUser(userData) {
    // ...
}
```

### Common code smells

|Code smell|Example|
|---|---|
|**Long function**|A function has 200 lines|
|**Large class**|One class handles auth, payments, emails, and users|
|**Duplicate code**|Same logic copied in 5 places|
|**Too many parameters**|`foo(a, b, c, d, e, f, g)`|
|**Deep nesting**|`if → if → for → if → if`|
|**Magic numbers**|`if (age > 17)` with unexplained `17`|
|**Poor naming**|`x`, `data`, `thing()`|
|**God object/class**|One object knows and controls almost everything|
|**Long conditional**|Huge `if/else if/else if` chain|
|**Dead code**|Code that is never used|

### Important distinction

**Code smell ≠ bug**

```js
function calculatePrice(price) {
    return price * 1.2;
}
```

This might work perfectly, but `1.2` is a **magic number**. That's a smell because someone reading the code may not know what `1.2` represents.

You could improve it:

```js
const TAX_RATE = 1.2;

function calculatePrice(price) {
    return price * TAX_RATE;
}
```

### Mental model

Think of a code smell like a **bad smell in a room**.

It doesn't prove there's a problem, but it tells you:

> **“Something here might need investigation.”**

Code smells are one reason practices like **refactoring** and the **Boy Scout Rule** are useful.



---
[[Back-End]]
[[My-Journey-In-Codeless]]