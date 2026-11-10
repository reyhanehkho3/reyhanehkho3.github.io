---
title: ANALYSE
publish: true
date created: 2026-11-10
tags:
  - database
  - dba-agent
---
Imagine PostgreSQL needs to execute:

```
SELECT * FROM orders WHERE customer_id = 100;
```

Should it:

- Scan the entire table?
    
- Use an index?
    

PostgreSQL's query planner makes this decision using statistics about the data.

`ANALYZE` collects these statistics.

```
ANALYZE orders;
```

For example, it collects information about:

- Number of rows.
    
- Distribution of values.
    
- Frequency of particular values.
    
- Data characteristics.
    

If statistics are outdated, PostgreSQL might choose a poor execution plan.

---
[[Database]]