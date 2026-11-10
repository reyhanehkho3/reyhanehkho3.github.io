---
title: CHECKPOINT
publish: true
date created: 2026-11-10
tags:
  - database
  - dba-agent
---
PostgreSQL changes data in memory before those changes are necessarily written to their final data-file locations.

A CHECKPOINT ensures that modified data pages are flushed to disk and establishes a recovery point in the WAL sequence.

```
CHECKPOINT;
```

PostgreSQL performs checkpoints automatically. Manual checkpoints are mainly useful for administration and specific operational situations.


---
[[Database]]