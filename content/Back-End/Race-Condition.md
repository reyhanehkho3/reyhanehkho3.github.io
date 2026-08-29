---
title: Race Condition
publish:
date created: 2026-08-29
tags:
  - Backend
  - codeless
---
**Definition:** A race condition happens when multiple operations access/change shared data concurrently and the final result depends on the order in which they execute.  
**The dangerous part is that each operation can look correct individually, while their combination produces an incorrect result.**

**Examples:**

1. Two customers buy the **last product** simultaneously.
2. Two users receive the **last available discount code**.
3. Two bank withdrawals happen simultaneously and both read the same account balance.

**Typical solution:** transactions, locks, atomic database operations, optimistic concurrency, etc.


---
[[Back-End]]
[[My-Journey-In-Codeless]]