---
title: ORM
date created: 2026-09-11
publish: true
tags:
  - database
  - codeless
---
**ORM** stands for **Object-Relational Mapping**.

It's a tool/library that lets you work with a **database using programming-language objects instead of writing SQL for everything**.

### Without an ORM

Suppose you have a `users` table:

```sql
SELECT * FROM users WHERE id = 5;
```

You write SQL directly and get database rows back.

### With an ORM

You might write something like:

```js
const user = await prisma.user.findUnique({
  where: { id: 5 }
});
```

The ORM translates this into the appropriate SQL behind the scenes.

```text
Your code
   ↓
ORM
   ↓
SQL
   ↓
PostgreSQL
   ↓
Rows
   ↓
ORM
   ↓
Your objects
```

### Why use an ORM?

It makes common database operations easier:

```text
Create user
Find user
Update user
Delete user
Find user's tasks
Create project
```

Instead of repeatedly writing SQL, you use the ORM's API.

### Examples of ORMs

For the technologies you've been working with:

- **Prisma** → Node.js/TypeScript
    
- **Sequelize** → Node.js
    
- **TypeORM** → TypeScript/JavaScript
    
- **Hibernate** → Java
    

For example, with Prisma:

```js
const users = await prisma.user.findMany();
```

instead of:

```sql
SELECT * FROM users;
```

### ORM and relationships

This is one of the useful parts.

Suppose:

```text
User
 │
 └── has many
       ↓
     Tasks
```

An ORM can let you express that relationship directly:

```js
const user = await prisma.user.findUnique({
  where: { id: 5 },
  include: { tasks: true }
});
```

Instead of manually writing the SQL joins.

### But ORM ≠ database

This is important:

```text
PostgreSQL = database
Prisma     = ORM
```

The ORM **doesn't replace PostgreSQL**.

It sits between your application and the database:

```text
Express application
       ↓
     Prisma
       ↓
   PostgreSQL
```

**Mental model:**

> **ORM = a translator between your application's objects/code and relational database tables/SQL.**

---
[[Database]]
[[My-Journey-In-Codeless]]