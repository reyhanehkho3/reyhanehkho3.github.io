---
title: Row-Level locking
publish: true
date created: 2026-09-05
tags:
  - codeless
  - database
---
**Definition:** Row-level locking means the database temporarily **locks a specific row while a transaction is working with it**, preventing conflicting changes to that row at the same time.  
It is useful when multiple users/processes might try to modify the **same piece of data simultaneously**. PostgreSQL, for example, supports `SELECT ... FOR UPDATE` for explicitly locking selected rows.

### Example

Suppose:

```
Products

id | name   | stock
1  | Laptop | 1
```

Two users try to buy the **last laptop** simultaneously.

Without proper concurrency control:

```
User A → reads stock = 1
User B → reads stock = 1

User A → buys it
User B → buys it

❌ 2 sales for 1 laptop
```

With row locking:

```
User A → locks product row
             ↓
        stock = 1
             ↓
        buys laptop
             ↓
        stock = 0
             ↓
        unlocks

User B → waits
             ↓
        sees stock = 0
             ↓
        purchase rejected
```

So:

> **Row-level locking = “Only one transaction can safely modify this particular row at a time.”**

It's mainly a **database-level concurrency technique**, not a solution for coordinating multiple independent services.


---
[[My-Journey-In-Codeless]]
[[Database]]
[[Distributed-Consistency-Patterns]]