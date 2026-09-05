---
title: SAGA Pattern
publish: true
date created: 2026-09-05
tags:
  - codeless
  - database
---
**Definition:** The Saga pattern handles a business operation that spans **multiple services** by breaking it into a sequence of local transactions.  
If a later step fails, the system performs **compensating transactions** to undo or compensate for the earlier successful steps.

### Example

An online purchase:

```
1. Order Service
      ↓
   Create Order ✓

2. Inventory Service
      ↓
   Reserve Product ✓

3. Payment Service
      ↓
   Charge Customer ✓

4. Shipping Service
      ↓
   ❌ FAILED
```

You can't simply do:

```
ROLLBACK EVERYTHING
```

because these are **different services/databases**.

Instead, Saga performs compensating actions:

```
Shipping ❌
    ↓
Refund Payment
    ↓
Release Inventory
    ↓
Cancel Order
```

So:

> **Saga = “If my distributed business process fails halfway, perform compensating actions to reach a valid final state.”**

### Two common ways to implement Saga

**Choreography:**

```
Order
  ↓ event
Inventory
  ↓ event
Payment
  ↓ event
Shipping
```

Services react to each other's events.

**Orchestration:**

```
        Saga Orchestrator
        /       |       \
       ↓        ↓        ↓
    Order   Inventory  Payment
```

A central orchestrator tells each service what to do.


---
[[Database]]
[[My-Journey-In-Codeless]]
[[Distributed-Consistency-Patterns]]
