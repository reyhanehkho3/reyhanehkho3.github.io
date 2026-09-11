---
title: Boy Scout Rule
publish:
date created: 2026-09-11
tags:
  - software-development
  - codeless
---
The **Boy Scout Rule** in software development is:

> **“Leave the code cleaner than you found it.”**

It comes from the idea that Boy Scouts should leave a campsite cleaner than they found it.

### In programming

Suppose you open a file to fix a bug:

```js
function calculateTotal(price,tax){
 return price+tax;
}
```

You fix the bug **and** notice the formatting is messy, so you improve it:

```js
function calculateTotal(price, tax) {
  return price + tax;
}
```

You didn't do a huge refactor. You just made the code **slightly better while you were already there**.

### Another example

You find:

```text
user.js
```

and notice:

```js
function getUserData() { ... }
function doStuff() { ... }
```

You might rename `doStuff()` to something meaningful:

```js
function updateUserProfile() { ... }
```

### Important

The Boy Scout Rule **doesn't mean**:

> "Every time I touch code, rewrite the whole thing."

It means:

> **Make small, safe improvements when you encounter code.**

So over time:

```text
Messy code
   ↓
small improvement
   ↓
slightly cleaner
   ↓
small improvement
   ↓
cleaner
   ↓
...
```

This helps prevent **technical debt from continuously accumulating**.


---
[[Software-Development]]
[[My-Journey-In-Codeless]]