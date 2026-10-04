---
title: DTO
publish: true
date created: 2026-09-17
tags:
  - database
  - codeless
  - Nitros
---
**DTO** stands for **Data Transfer Object**.

It's an object whose purpose is to **define the shape of data being transferred** between different parts of your application.

In a **NestJS** backend, you'll see DTOs everywhere.

### Simple example

Suppose your frontend sends a request to create a user:

```json
{
  "name": "Alice",
  "email": "alice@example.com",
  "password": "123456"
}
```

You could define a DTO:

```ts
export class CreateUserDto {
  name: string;
  email: string;
  password: string;
}
```

Then your controller can use it:

```ts
@Post()
createUser(@Body() createUserDto: CreateUserDto) {
  return this.usersService.create(createUserDto);
}
```

The flow becomes:

```text
Frontend
   │
   │  JSON
   ▼
Controller
   │
   │  CreateUserDto
   ▼
Service
   │
   ▼
Database
```

### DTO vs Entity

This distinction is **very important** when working with NestJS + TypeORM:

**Entity** describes how data is stored in the database:

```ts
@Entity()
export class User {
  @PrimaryGeneratedColumn()
  id: number;

  @Column()
  name: string;

  @Column()
  email: string;

  @Column()
  password: string;
}
```

**DTO** describes what data your API accepts or returns:

```ts
export class CreateUserDto {
  name: string;
  email: string;
  password: string;
}
```

So:

```text
DTO      → API / data transfer
Entity   → Database / persistence
```

They **can look similar**, but they have different responsibilities.

### DTOs are also useful for validation

NestJS commonly uses `class-validator` with DTOs:

```ts
import { IsEmail, IsNotEmpty, MinLength } from "class-validator";

export class CreateUserDto {
  @IsNotEmpty()
  name: string;

  @IsEmail()
  email: string;

  @MinLength(8)
  password: string;
}
```

Now if someone sends:

```json
{
  "name": "",
  "email": "not-an-email",
  "password": "123"
}
```

NestJS can reject the request because it doesn't satisfy the DTO's validation rules.

### A useful mental model

Think of a DTO as an **API contract**:

```text
             DTO
              │
     ┌────────┴────────┐
     │                 │
  What can          What shape
  be sent?          must it have?
     │                 │
     └────────┬────────┘
              ▼
          Controller
```

So when you see something like:

```ts
createUser(@Body() dto: CreateUserDto)
```

you can read it as:

> "Take the request body and treat it as data that must follow the `CreateUserDto` contract."


---
[[Database]]
[[My-Journey-In-Codeless]]