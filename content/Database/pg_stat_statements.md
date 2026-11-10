---
title: pg_stat_statements
publish: true
date created: 2026-11-10
tags:
  - database
  - dba-agent
---
## pg_stat_statements

`pg_stat_statements` is a PostgreSQL extension for collecting **aggregate planning and execution statistics for SQL statements**. It is one of PostgreSQL’s most useful built-in performance-diagnostics facilities because it shows which query patterns consume database time and resources across repeated executions, rather than examining only one execution at a time. [PostgreSQL](https://www.postgresql.org/docs/current/pgstatstatements.html?utm_source=chatgpt.com)

### What it measures

The extension **normalizes similar queries** so statements differing mainly in literal constants can be aggregated under the same `queryid`. For each entry it records metrics including call count, total and average execution time, rows processed, shared/local/temp block activity, WAL generation, and—when enabled—planning statistics. This makes expensive high-frequency queries particularly easy to identify. [PostgreSQL](https://www.postgresql.org/docs/current/pgstatstatements.html?utm_source=chatgpt.com)

### How it is enabled

Because collection requires shared memory, `pg_stat_statements` must be included in `shared_preload_libraries`, which requires a PostgreSQL restart when adding or removing it. Query-ID calculation must also be active; access to the views in an individual database is then enabled with `CREATE EXTENSION pg_stat_statements`. The collector itself operates across databases on the server. [PostgreSQL](https://www.postgresql.org/docs/current/pgstatstatements.html?utm_source=chatgpt.com)

### Typical performance analysis

A common first analysis sorts the view by **`total_exec_time`** to find queries responsible for the greatest cumulative workload. `mean_exec_time` highlights individually slow statements, `calls` exposes high-frequency queries, while block and temporary-file statistics help distinguish CPU-heavy work from I/O or spilling. Combining these dimensions is generally more informative than simply looking for the single slowest query. [PostgreSQL](https://www.postgresql.org/docs/current/pgstatstatements.html?utm_source=chatgpt.com)

### Operational considerations

Statistics are cumulative until reset, so the **measurement interval matters** when interpreting them; `pg_stat_statements_info` exposes information such as the last statistics reset and deallocation activity. The configurable `pg_stat_statements.max` limits how many distinct statements are retained, and enabling planning-time collection can impose a noticeable performance penalty under some workloads. [PostgreSQL](https://www.postgresql.org/docs/current/pgstatstatements.html?utm_source=chatgpt.com)



---
[[Database]]