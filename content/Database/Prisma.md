---
title: Prisma
publish: true
date created: 2026-09-11
tags:
  - database
  - ORM
  - codeless
---
**Prisma** is a **database toolkit for Node.js/TypeScript**. It is most commonly used as an **ORM**.

Think of it like this:

```text
Your Node.js / Express code
          ↓
       Prisma
          ↓
      PostgreSQL
```

### Example

Suppose your PostgreSQL database has:

```text
users
----------------
id
name
email
```

With Prisma, you can write:

```js
const users = await prisma.user.findMany();
```

Instead of writing:

```sql
SELECT * FROM users;
```

Prisma handles the communication with PostgreSQL for you.

### Prisma has several parts

**1. Prisma Client**

The code you use in your application:

```js
const user = await prisma.user.findUnique({
  where: { id: 5 }
});
```

**2. Prisma Schema**

You describe your database structure in `schema.prisma`:

```prisma
model User {
  id    Int    @id @default(autoincrement())
  name  String
  email String @unique
}
```

From this, Prisma knows what a `User` looks like.

**3. Prisma Migrate**

Helps manage database schema changes.

For example:

```text
Add User
   ↓
Add Task
   ↓
Add relationship User → Task
   ↓
Change email constraint
```

Prisma can generate/apply migrations for these changes.

### Prisma vs PostgreSQL

Don't confuse them:

```text
PostgreSQL
= actual database
= stores your data

Prisma
= application-side database toolkit/ORM
= helps your code communicate with PostgreSQL
```

For your Express projects, you could have:

```text
Vue frontend
     ↓
Express API
     ↓
Prisma
     ↓
PostgreSQL
```

So when you previously saw:

> **"PostgreSQL + Prisma"**

it means **PostgreSQL is the database, and Prisma is the tool your Node.js backend uses to work with that database.**

---
[[Database]]
[[ORM]]
[[My-Journey-In-Codeless]]