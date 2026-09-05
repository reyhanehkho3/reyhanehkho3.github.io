---
title: Out-box Pattern
publish: true
date created: 2026-09-05
tags:
  - codeless
  - database
---
**Definition:** The Outbox pattern solves the problem of needing to **update a database and publish a message reliably** without using a distributed transaction.  
The application writes both the business change and an **outbox message in the same database transaction**, then a separate process publishes the message.

### The problem

Imagine:

```
Create Order
    ↓
Update Database ✓
    ↓
Publish Event ❌
```

The database says:

```
Order = CREATED
```

but other services never receive:

```
OrderCreated
```

Now your system is inconsistent.

### Outbox solution

Instead:

```
Database Transaction
┌───────────────────────────┐
│ Create Order               │
│                            │
│ Insert OrderCreated event  │
│ into OUTBOX table          │
└───────────────────────────┘
             ↓
          COMMIT ✓
             ↓
      Outbox Publisher
             ↓
        Message Broker
             ↓
       Other Services
```

The important part is that **the order and the outbox message are committed together**.

So:

> **Outbox = “Save my database change and the message I need to publish in the same transaction, then publish the message afterward.”**


---
[[Database]]
[[Distributed-Consistency-Patterns]]
[[My-Journey-In-Codeless]]