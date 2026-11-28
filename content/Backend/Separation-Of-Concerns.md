---
title: Separation of concerns
publish: true
date created: 2026-10-07
tags:
  - backend
---
It means:

> **Keep different responsibilities of a system separate from each other.**

Instead of putting everything in one giant piece of code, you divide it into parts where each part has a clear responsibility.

### A simple example

Imagine you have an online shop.

A bad design might have one function doing all of this:

```text
handleOrder()
 ├── validate user
 ├── calculate price
 ├── save order to database
 ├── charge credit card
 ├── send email
 └── create log
```

That's a lot of different concerns mixed together.

With **Separation of Concerns**, you might have:

```text
OrderController
      ↓
OrderService
      ↓
OrderRepository
      ↓
Database
```

And separately:

```text
PaymentService → Payment Provider
EmailService   → Email Provider
Logger         → Logging system
```

Each part has a job.

---

### In a backend

For example, in a NestJS/Express application:

```text
Controller
   │
   │ HTTP request/response
   ↓
Service
   │
   │ business logic
   ↓
Repository
   │
   │ database operations
   ↓
Database
```

So:

**Controller:**

> "A request came in. What should I return?"

**Service:**

> "What should the application actually do?"

**Repository:**

> "How do I get/save the data?"

This is Separation of Concerns.

---

### Why is it useful?

Imagine you put database code directly inside your controller:

```javascript
app.get('/users', async (req, res) => {
    const users = await db.query(
        'SELECT * FROM users WHERE ...'
    );

    // 50 more lines of business logic...

    res.json(users);
});
```

Now the controller knows:

- HTTP
    
- SQL
    
- business rules
    
- data processing
    

Changing one thing can affect everything else.

With separation:

```javascript
// Controller
const users = await userService.getUsers();
res.json(users);
```

The controller doesn't need to know **how** users are retrieved.

That makes the code easier to:

- understand
    
- test
    
- change
    
- maintain
    
- reuse
    

---

### One important distinction

**Separation of Concerns is a principle, not a specific architecture.**

Things like:

- MVC
    
- Layered Architecture
    
- Clean Architecture
    
- Hexagonal Architecture
    

are different ways of applying this and other principles.

The basic idea is simply:

> **Don't make one part of your system responsible for things that belong to different concerns.**

A useful rule of thumb is:

> **If changing one responsibility forces you to modify lots of unrelated code, your concerns may be too tightly coupled.**



---
[[Back-End]]