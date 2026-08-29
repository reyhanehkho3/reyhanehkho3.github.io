---
title: Isolation
publish: true
date created: 2026-08-29
tags:
  - database
  - codeless
  - ACID
---
**Definition:** Isolation means concurrent transactions should behave according to the database's chosen isolation guarantees rather than improperly seeing/interfering with each other's intermediate work.  
**The isolation level determines exactly how much interference is allowed.**

**Examples:**

1. Transaction A hasn't committed its salary update → B shouldn't see an invalid intermediate state.
2. Two customers try to buy the same item.
3. Two transactions update the same bank account simultaneously.

---
[[Database]]
[[My-Journey-In-Codeless]]