---
title: DDL
publish: true
date created: 2026-11-10
tags:
  - dba-agent
  - database
---
DDL stands for Data Definition Language.

It's a category of SQL statements used to define or modify database structures.

Remember that SQL statements are commonly divided into categories:

|Category|Full name|Purpose|
|---|---|---|
|DDL|Data Definition Language|Define database structures|
|DML|Data Manipulation Language|Insert, update, delete data|
|DQL|Data Query Language|Retrieve data|
|DCL|Data Control Language|Manage permissions|
|TCL|Transaction Control Language|Manage transactions|

### Examples of DDL operations

CREATE

Creates database objects.

```
CREATE TABLE employees (
    id SERIAL PRIMARY KEY,
    name VARCHAR(100),
    salary NUMERIC
);
```

ALTER

Modifies an existing database object.

```
ALTER TABLE employees
ADD COLUMN department VARCHAR(100);
```

DROP

Deletes a database object.

```
DROP TABLE employees;
```

TRUNCATE

Removes all rows from a table without dropping the table itself.

```
TRUNCATE TABLE employees;
```

CREATE INDEX

Creates an index.

```
CREATE INDEX idx_employee_name
ON employees(name);
```

### Why are DDL operations important for a DBA?

Imagine an application developer wants to change the structure of a production database.

They execute:

```
ALTER TABLE orders
ADD COLUMN status VARCHAR(50);
```

This is a schema change.

The DBA needs to consider:

- Will it lock the table?
    
- Will it affect running queries?
    
- Will it consume significant disk space?
    
- Will the application remain compatible?
    
- Is a backup or rollback strategy needed?
    

That's why DDL operations are important in database administration.

One detail: DDL is a classification of SQL operations, not a guarantee that every DDL statement is transactional or non-disruptive. PostgreSQL supports transactional DDL for many operations, but locking and operational impact still matter.

---
[[Database]]