---
title: Outbox
publish:
date created: 2026-08-29
tags:
  - database
  - codeless
---
**Definition:** The Outbox Pattern solves the problem of reliably updating a database **and** publishing an event/message.  
**The service stores the business change and an "outbox event" in the same database transaction, then a separate process publishes the event.**

### Without Outbox

```
Update DB ✅
Publish Kafka message ❌
```

Now the database changed but nobody knows about it.

### With Outbox

```
DB transaction:
    Update Order
    Insert Outbox Event
          ↓
    Commit ✅
          ↓
Outbox Publisher
          ↓
Kafka
```

**Examples:**

1. Create order + `OrderCreated` event.
2. Register user + `UserRegistered` event.
3. Change payment status + `PaymentCompleted` event.

---
[[Database]]
[[My-Journey-In-Codeless]]