---
title: Durability
publish:
date created: 2026-08-29
tags:
  - database
  - codeless
  - ACID
---
**Definition:** Durability means that once a transaction successfully commits, its changes survive failures such as a database/server crash.  
**The database uses mechanisms such as logs and persistent storage to recover committed data.**

**Examples:**

1. You successfully transfer €100 → server crashes → transfer is still recorded.
2. You place an order → database crashes → committed order isn't lost.
3. You create a user → power failure → user still exists after recovery.


---
[[Database]]
[[My-Journey-In-Codeless]]