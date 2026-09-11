---
title: Zod
publish: true
date created: 2026-09-11
tags:
  - Backend
  - codeless
  - frontend
---
**Zod** is a **TypeScript/JavaScript library for validating data**.

In simple terms:

> **Zod checks whether data has the shape and types you expect.**

### Example

Suppose your API expects a user:

```js
{
  name: "Reyhaneh",
  age: 25,
  email: "rey@example.com"
}
```

You can define a Zod schema:

```js
import { z } from "zod";

const userSchema = z.object({
  name: z.string(),
  age: z.number(),
  email: z.string().email()
});
```

Then validate data:

```js
userSchema.parse(user);
```

If the data is:

```js
{
  name: "Reyhaneh",
  age: "25",
  email: "wrong"
}
```

Zod rejects it because:

- `age` should be a number, but it's a string
    
- `email` isn't a valid email
    

### Where is Zod commonly used?

Especially in **frontend + API applications**:

```text
Frontend
   ↓
Form data
   ↓
Zod validation
   ↓
API request
   ↓
Backend
   ↓
Zod validation
   ↓
Database
```

For example, with a login form:

```js
const loginSchema = z.object({
  email: z.string().email(),
  password: z.string().min(8)
});
```

This lets you catch invalid input before sending it to the API.

### Zod vs TypeScript

A very important distinction:

**TypeScript checks types at development/compile time.**

```ts
type User = {
  name: string;
  age: number;
};
```

But data coming from an API is **runtime data**. TypeScript cannot guarantee that the API actually sent what you expect.

Zod can check it at runtime:

```text
TypeScript
   ↓
"According to my code, this should be a User."

Zod
   ↓
"Let me check whether the actual data really is a User."
```

So a common combination is:

> **TypeScript = type safety during development**  
> **Zod = runtime validation of actual data**


---
[[Back-End]]
[[Frontend]]
[[My-Journey-In-Codeless]]