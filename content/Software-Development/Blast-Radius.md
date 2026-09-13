---
title: Blast Radius
publish: true
date created: 2026-09-11
tags:
  - codeless
  - software-development
---
**Blast radius** means **how much of a system is affected when something goes wrong**.

Think of dropping a stone into water:

```text
        💥
      (   )
    (       )
  (           )
```

The bigger the affected area, the bigger the **blast radius**.

### Software example

Suppose your application has:

```text
Auth
Users
Posts
Comments
Notifications
```

If a bug in the **Posts** module only breaks posts:

```text
Posts 💥
Users       ✅
Comments    ✅
Notifications ✅
```

→ **Small blast radius**

But if everything depends directly on one shared module and a bug there breaks the entire application:

```text
Auth          ❌
Users         ❌
Posts         ❌
Comments      ❌
Notifications ❌
```

→ **Large blast radius**

### Why developers care

A good architecture tries to **limit blast radius**.

For example:

- modular architecture → failures stay more isolated
    
- feature flags → disable one feature without taking down everything
    
- independent services → one service can fail while others continue
    
- retries/timeouts → prevent one failing dependency from taking down the whole system
    

**Simple definition:**

> **Blast radius = the scope of damage caused by a failure or change.**

You can also hear it in security: _“If this account is compromised, what's its blast radius?”_ — meaning **what can the attacker affect?**


---
[[Software-Development]]
[[My-Journey-In-Codeless]]