---
title: Eventual Consistency
publish:
date created: 2026-08-29
tags:
  - database
  - codeless
---
**Definition:** Eventual consistency means different copies of data may temporarily contain different values, but they will eventually converge to the same value.  
**You sacrifice immediate consistency in exchange for properties such as availability, scalability, or lower coupling.**

**Examples:**

1. You change your profile picture → another service sees the old picture for 2 seconds.
2. You purchase something → the recommendation system learns about it a few seconds later.
3. A social-media post → followers in different regions see it at slightly different times.

---
[[Database]]
[[My-Journey-In-Codeless]]