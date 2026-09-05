---
title: Distributed Consistency Patterns
publish:
date created: 2026-09-05
tags:
  - codeless
  - database
---
**Definition:** Distributed consistency patterns are techniques for keeping data **correct and coordinated when it is spread across multiple services, databases, or servers**.  
Because you usually cannot use one normal database transaction across all of them, patterns such as **Saga, Outbox, replication, and locking** are used instead.

### Example

Imagine an online shop:

```
Order Service
      ↓
Inventory Service
      ↓
Payment Service
      ↓
Shipping Service
```

A single business action — **"buy a product"** — affects several services.

The question is:

> What happens if Payment succeeds but Shipping fails?

Distributed consistency patterns are the different strategies for dealing with situations like this.

**Important:** There isn't one single "distributed consistency pattern." It's a **category of solutions**.


---
[[Database]]
[[My-Journey-In-Codeless]]