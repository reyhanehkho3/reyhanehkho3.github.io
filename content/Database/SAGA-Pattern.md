---
title: SAGA Pattern
publish:
date created: 2026-08-29
tags:
  - database
  - codeless
---
**Definition:** A Saga breaks a distributed business transaction into multiple local transactions, with each service committing its own database transaction.  
**In orchestration, a central Saga Orchestrator tells each service what to do and triggers compensating actions when something fails.**

### Example flow

```
Order Service
     ↓
Saga Orchestrator
     ↓
Payment Service
     ↓
Inventory Service
     ↓
Shipping Service
```

If Shipping fails:

```
Shipping ❌
    ↓
Orchestrator
    ↓
Cancel Inventory
    ↓
Refund Payment
    ↓
Cancel Order
```

**Examples:**

1. Online shop: Order → Payment → Inventory → Shipping.
2. Travel booking: Flight → Hotel → Car rental.
3. Food delivery: Order → Restaurant → Payment → Driver assignment.

---
[[Database]]
[[My-Journey-In-Codeless]]