---
title: EXPLAIN
publish: true
date created: 2026-11-10
tags:
  - database
  - dba-agent
---
You probably know how to write queries. But how do you know how PostgreSQL executes them?

```
EXPLAIN ANALYZE
SELECT *
FROM orders
WHERE customer_id = 100;
```

It shows the actual execution plan and execution statistics.

You can investigate:

- Sequential scans.
    
- Index scans.
    
- Join strategies.
    
- Execution time.
    
- Estimated versus actual row counts.

---
[[Database]]