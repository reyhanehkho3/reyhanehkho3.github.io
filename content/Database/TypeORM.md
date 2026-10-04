---
title: TypeORM
publish: true
date created: 2026-09-17
tags:
  - database
  - codeless
  - Nitros
---
**TypeORM** is an **Object-Relational Mapper (ORM)** for **TypeScript and JavaScript**. It makes it easier to work with relational databases such as PostgreSQL, MySQL, SQLite, and SQL Server without writing SQL for every operation.

Instead of writing SQL like:

```sql
SELECT * FROM users WHERE id = 10;
```

With TypeORM, you can work with TypeScript objects:

```ts
const user = await userRepository.findOne({
  where: { id: 10 }
});
```

### How it works

You typically define an **Entity**, which represents a database table:

```ts
import {
  Entity,
  PrimaryGeneratedColumn,
  Column
} from "typeorm";

@Entity()
export class User {
  @PrimaryGeneratedColumn()
  id: number;

  @Column()
  name: string;

  @Column()
  email: string;
}
```

TypeORM maps that class roughly to:

```text
users
-------------------------
id     | name    | email
-------------------------
1      | Alice   | ...
2      | Bob     | ...
```

Then you can perform database operations using a repository:

```ts
const userRepository = dataSource.getRepository(User);

// Create
const user = userRepository.create({
  name: "Alice",
  email: "alice@example.com"
});

await userRepository.save(user);

// Read
const users = await userRepository.find();

// Update
user.name = "Alice Smith";
await userRepository.save(user);

// Delete
await userRepository.remove(user);
```

TypeORM also handles things like **relationships** (`OneToMany`, `ManyToOne`, etc.), **migrations**, **transactions**, **query building**, and **schema mapping**.

A useful mental model is:

```text
TypeScript Class
      ↓
    TypeORM
      ↓
 SQL Database
      ↓
PostgreSQL / MySQL / SQLite / etc.
```

It's especially common in **Node.js + TypeScript** applications and is often used with frameworks such as NestJS.


---
[[Frontend]]
[[My-Journey-In-Codeless]]
