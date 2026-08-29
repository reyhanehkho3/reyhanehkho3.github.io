---
title: Isolation Level
publish:
date created: 2026-08-29
tags:
  - database
  - codeless
---
**Definition:** An isolation level defines how much one database transaction is protected from changes made by other concurrent transactions.  
**Common levels include Read Uncommitted, Read Committed, Repeatable Read, and Serializable.**

**Examples:**

1. **Read Committed:** You don't read another transaction's uncommitted changes.
2. **Repeatable Read:** Reading the same row twice within a transaction gives a stable result.
3. **Serializable:** Concurrent transactions behave as if they were executed one after another.

---
[[Database]]
[[My-Journey-In-Codeless]]