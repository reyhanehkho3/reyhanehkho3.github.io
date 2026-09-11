---
title: Forms and Validation
publish:
date created: 2026-09-10
tags:
  - frontend
  - basic
  - codeless
---
Forms are everywhere:

```
Login
Register
Create task
Edit profile
Change password
Search
```

There are several concepts here.

---

## Controlled Input

The frontend keeps the input's value in state.

For example:

```
Input
  ↓
username state
  ↓
Input
```

If the user types:

```
reyhaneh
```

your state becomes:

```
username = "reyhaneh"
```

The UI and state remain synchronized.

---

## Client-side validation

Validation performed by the frontend **before sending the request**.

For example:

```
Email:
reyhaneh

❌ Invalid email
```

Or:

```
Password:
123

❌ Password must contain at least 8 characters
```

This gives the user immediate feedback.

---

## Server-side validation

The backend **must validate again**.

For example:

```
Frontend
   ↓
"email looks valid"
   ↓
Backend
   ↓
validate email again
```

Why?

Because users can bypass the frontend.

Someone can directly send:

```
POST /api/register
```

without using your website.

Therefore:

> **Client validation improves UX. Server validation provides actual security/integrity.**

---

## Schema-based validation

Instead of writing dozens of individual checks, you define a schema.

Conceptually:

```
User schema:

username → required
email → valid email
password → minimum 8 characters
age → number
```

Then the validation library checks the entire object.

Common schema-validation libraries include:

- Zod
- Yup
- Valibot

### Example

```
Register Form
     ↓
Schema validation
     ↓
valid? ── No → show errors
  │
 Yes
  ↓
POST /api/register
  ↓
Server validation
```

---
[[Frontend]]
[[Forms&Validation]]