---
title: Lock management
publish: true
date created: 2026-11-10
tags:
  - database
  - dba-agent
---
Imagine transaction A updates a row but doesn't commit.

Transaction B tries to update the same row.

Transaction B might have to wait.

This is called lock contention.

DBAs investigate:

- Blocking queries.
    
- Long-running transactions.
    
- Deadlocks.
    
- Lock waits.
    

Useful PostgreSQL views include:

```
SELECT *
FROM pg_stat_activity;
```

And:

```
SELECT *
FROM pg_locks;
```

---
[[Database]]