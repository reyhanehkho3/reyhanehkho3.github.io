---
title: VACUUM
publish: true
date created: 2026-11-10
tags:
  - database
  - dba-agent
---
Very important in PostgreSQL

Imagine you have this table:

|id|name|
|---|---|
|1|Ali|
|2|Sara|
|3|Reza|

You execute:

```
DELETE FROM users WHERE id = 2;
```

You might expect PostgreSQL to immediately remove the physical data from the disk.

But PostgreSQL uses a mechanism called MVCC (Multi-Version Concurrency Control).

Instead of immediately removing old rows, PostgreSQL marks their versions as no longer visible to new transactions.

This is important because another transaction might still need to see an older version of the row.

Over time, these obsolete row versions accumulate. They are called dead tuples.


VACUUM cleans up dead tuples when they are no longer needed.

Example:

```
VACUUM users;
```

There are several variations:

|Command|Purpose|
|---|---|
|`VACUUM`|Reclaims space for reuse|
|`VACUUM FULL`|Rewrites the table and returns space to the OS|
|`VACUUM ANALYZE`|Cleans dead tuples and updates statistics|
|`ANALYZE`|Updates statistics used by the query planner|

One important distinction:

- `VACUUM` usually doesn't shrink the physical table file.
    
- `VACUUM FULL` can shrink it, but requires an exclusive lock and can be disruptive.
    

What is autovacuum?

PostgreSQL has an automatic background process called `autovacuum`.

It periodically performs VACUUM and ANALYZE when necessary.

You generally shouldn't need to run VACUUM manually all the time.

---
[[Database]]