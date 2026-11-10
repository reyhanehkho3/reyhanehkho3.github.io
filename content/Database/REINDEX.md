---
title: REINDEX
publish: true
date created: 2026-10-11
tags:
  - database
  - dba-agent
---
Indexes can become inefficient or corrupted.

`REINDEX` rebuilds an index.

```
REINDEX TABLE orders;
```

You might use it when investigating index corruption or certain types of index bloat.

It isn't something you should run routinely without a reason.

---
[[Database]]