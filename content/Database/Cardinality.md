---
title: Cardinality
publish:
date created: 2026-08-29
tags:
  - database
  - codeless
---
**Definition:** Cardinality means the number of **distinct values** in a column or dataset.  
**High-cardinality columns have many unique values; low-cardinality columns have relatively few unique values.**

**Examples:**

|Column|Example values|Cardinality|
|---|---|---|
|`gender`|M, F|Low|
|`country`|~200 countries|Low|
|`user_id`|Millions of users|High|

In ClickHouse, understanding cardinality is important because it affects storage, indexing, grouping, and query performance.


---
[[Database]]
[[My-Journey-In-Codeless]]