---
title: Consistency
publish:
date created: 2026-08-29
tags:
  - database
  - codeless
  - ACID
---
# Consistency — ACID

**Definition:** In ACID, consistency means a transaction moves the database from one valid state to another valid state while respecting defined rules and constraints.  
**For example, a database constraint saying an account balance cannot be negative must remain satisfied after a successful transaction.**

**Examples:**

1. A foreign key cannot reference a nonexistent user.
2. An order cannot reference an invalid product.
3. A bank transaction cannot violate a database constraint.

---
[[Database]]
[[My-Journey-In-Codeless]]
