---
title: TypeScript
publish: true
date created: 2026-09-17
tags:
  - javascript

  - codeless

  - Nitros
---
**TypeScript (TS)** is a programming language developed by Microsoft. It is essentially **JavaScript with additional features, especially static typing**.

The simplest way to think about it:

> **TypeScript = JavaScript + types + better developer tooling**

### JavaScript

In JavaScript, you can write:

```javascript
function add(a, b) {
  return a + b;
}

add(10, 20);
```

JavaScript doesn't require you to say what type `a` and `b` are.

You could accidentally do:

```javascript
add("hello", 20);
```

and JavaScript won't complain before running the code.

---

### TypeScript

With TypeScript, you can specify the types:

```typescript
function add(a: number, b: number): number {
  return a + b;
}
```

Now TypeScript knows:

```text
a → number
b → number
return value → number
```

So this produces a type error:

```typescript
add("hello", 20);
```

because `"hello"` is a string, not a number.

---

### Why is this useful?

For small applications, types might seem unnecessary. But in a large project they become very useful.

Imagine:

```typescript
function createUser(
  name: string,
  age: number,
  email: string
) {
  // ...
}
```

Someone using this function immediately knows what data it expects.

It also helps your IDE give you better:

- autocomplete
    
- error detection
    
- refactoring
    
- documentation
    
- navigation through large codebases
    

---

### TypeScript doesn't run directly in the browser

This is an important concept.

You normally write:

```text
TypeScript
    ↓
TypeScript compiler
    ↓
JavaScript
    ↓
Browser / Node.js
```

For example:

```typescript
const name: string = "Alice";
```

gets transformed into JavaScript roughly like:

```javascript
const name = "Alice";
```

The browser ultimately runs **JavaScript**, not TypeScript.

---

### TypeScript is a superset of JavaScript

This means normal JavaScript is generally valid TypeScript:

```typescript
const name = "Alice";

console.log(name);
```

You can gradually add types:

```typescript
const name: string = "Alice";
const age: number = 25;
const isAdmin: boolean = false;
```

There are also more advanced types:

```typescript
interface User {
  id: number;
  name: string;
  email: string;
}

const user: User = {
  id: 1,
  name: "Alice",
  email: "alice@example.com"
};
```

### How this relates to your project

If you're working with **NestJS**, you'll see TypeScript everywhere:

```text
NestJS
   ↓
TypeScript
   ↓
Node.js
```

For example, a NestJS controller:

```typescript
@Controller('users')
export class UsersController {

  @Get()
  getUsers(): User[] {
    return this.usersService.getUsers();
  }
}
```

Here TypeScript tells us that `getUsers()` returns an array of `User` objects.

So the relationship is:

**Node.js** → runs JavaScript on the server  
**TypeScript** → language used to write the code  
**NestJS** → framework used to structure the Node.js backend

That combination is very common for modern backend development.

---
[[JavaScript]]
[[My-Journey-In-Codeless]]