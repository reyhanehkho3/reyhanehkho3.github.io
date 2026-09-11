---
title: Tight Coupling
publish:
date created: 2026-09-11
tags:
  - Backend
  - codeless
---
**Tight coupling** means that **one part of your code depends heavily on another part**.

If you change one part, you often have to change the other part too.

### Simple example

```js
class OrderService {
    constructor() {
        this.mysqlDatabase = new MySQLDatabase();
    }

    createOrder(order) {
        this.mysqlDatabase.save(order);
    }
}
```

`OrderService` is **tightly coupled** to `MySQLDatabase`.

Why?

Because it directly creates and depends on a specific database implementation:

```text
OrderService
     ↓
MySQLDatabase
```

If you want to switch to PostgreSQL:

```text
MySQL → PostgreSQL
```

you probably need to modify `OrderService`.

---

### Loose coupling

Instead, you can depend on an abstraction:

```js
class OrderService {
    constructor(database) {
        this.database = database;
    }

    createOrder(order) {
        this.database.save(order);
    }
}
```

Now:

```text
             ┌─ MySQLDatabase
OrderService ┤
             └─ PostgreSQLDatabase
```

`OrderService` doesn't care which database it receives.

### Why tight coupling is usually bad

It makes code:

- harder to **change**
    
- harder to **test**
    
- harder to **reuse**
    
- harder to **maintain**
    

For example, testing this:

```js
OrderService → MySQLDatabase
```

may require a real MySQL database.

With loose coupling, you can give it a fake:

```text
OrderService → FakeDatabase
```

and test the service without a real database.

### Mental model

Think of it like two objects being **glued together**:

> **Tight coupling:** “I can't change you without affecting me.”

> **Loose coupling:** “I know what you can do, but I don't care how you do it.”

**Code smell connection:** Tight coupling is often considered a design problem/code smell, especially when dependencies are concrete and spread throughout the application.

---
[[Back-End]]
[[My-Journey-In-Codeless]]