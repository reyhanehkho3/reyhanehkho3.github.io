---
title: Partition Tolerance
publish: true
date created: 2026-08-29
tags:
  - Backend
  - codeless
  - CAP
---
## Partition Tolerance — CAP
**Definition:** Partition tolerance means a distributed system continues operating despite a network failure that separates nodes into groups that cannot communicate.  
**In CAP, when a network partition occurs, a distributed system must choose between stronger consistency and availability.**

**Examples:**

1. Database node A cannot communicate with node B.
2. Two data centers temporarily lose their connection.
3. A network failure separates two Kubernetes regions.

> **P isn't something you normally "choose to have"; network partitions are a reality in distributed systems. The practical choice is often what the system does during a partition.**


---
[[Back-End]]
[[My-Journey-In-Codeless]]