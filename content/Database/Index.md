---
title: Index
publish: true
date created: 2026-11-10
tags:
  - database
  - dba-agent
---
Imagine you have a table containing 10 million orders.

```
SELECT *
FROM orders
WHERE customer_id = 150;
```

How does PostgreSQL find the orders belonging to customer 150?

Without an index, PostgreSQL might have to examine every row in the table.

This is called a Sequential Scan.

Without an index : PostgreSQL potentially checks every row until it finds the matching records.

With an index:‌ PostgreSQL uses the index to locate matching rows without scanning the entire table.


Think of an index like the index at the back of a book.

Instead of reading every page to find a particular topic, you look up the topic in the index and go directly to the relevant page.

### How do you create an index?

```
CREATE INDEX idx_orders_customer_id
ON orders(customer_id);
```

Now PostgreSQL has an index it can potentially use when searching by `customer_id`.

You can inspect the execution plan:

```
EXPLAIN ANALYZE
SELECT *
FROM orders
WHERE customer_id = 150;
```

You might see:

- `Seq Scan`: PostgreSQL scans the table.
    
- `Index Scan`: PostgreSQL uses an index to locate rows.
    
- `Bitmap Index Scan`: PostgreSQL uses an index to identify matching rows, then accesses the table pages efficiently.
    

### Types of indexes in PostgreSQL

|Index type|Common use|
|---|---|
|B-tree|Equality, range queries, sorting|
|Hash|Equality comparisons|
|GIN|JSONB, arrays, full-text search|
|GiST|Geometric data, ranges, specialized searches|
|BRIN|Very large tables with physically correlated data|

### Are indexes always good?

No!

Indexes have costs:

1. They consume disk space.
    
2. INSERT operations may become slower.
    
3. UPDATE operations may become slower.
    
4. DELETE operations may create dead index entries that need maintenance.
    

A DBA needs to decide which indexes are actually useful.

Important: PostgreSQL does not automatically create an index on every column you use in a WHERE clause.


Indexes help PostgreSQL find records faster.

But indexes aren't free.

They consume disk space and make INSERT, UPDATE, and DELETE operations more expensive.

A DBA needs to determine:

- Which columns need indexes?
    
- Which indexes are unused?
    
- Are indexes bloated?
    
- Are queries using the intended indexes?

---
[[Database]]