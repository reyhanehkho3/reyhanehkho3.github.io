---
title: Replication
publish: true
date created: 2026-11-10
tags:
  - database
  - dba-agent
---
Replication means maintaining copies of database data on other servers.

For example:

- Primary database: handles writes.
    
- Standby database: receives changes from the primary.
    
- Read replicas: can potentially serve read queries.
    

PostgreSQL supports streaming replication.

---
[[Database]]