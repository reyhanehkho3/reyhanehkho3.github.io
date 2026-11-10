---
title: AUDIT
publish: true
date created: 2026-11-10
tags:
  - database
  - dba-agent
---
Imagine someone executes:

```
UPDATE employees
SET salary = 5000
WHERE id = 10;
```

Later, your manager asks:

- Who changed this employee's salary?
    
- When did they change it?
    
- What was the old value?
    
- What is the new value?
    
- Was the change authorized?
    

This is where Database Auditing comes in.

Auditing means recording database activities so you can investigate what happened.

Common things to audit:

|Activity|Example|
|---|---|
|Login attempts|Who connected to the database?|
|SQL execution|Who executed a DELETE?|
|Schema changes|Who dropped a table?|
|Permission changes|Who granted SUPERUSER?|
|Data changes|Who changed an employee's salary?|

### How does PostgreSQL auditing work?

PostgreSQL has several approaches.

1. PostgreSQL logging

You can configure PostgreSQL to log SQL statements.

For example, in `postgresql.conf`:

```
log_statement = 'ddl'
```

This logs DDL statements such as `CREATE`, `ALTER`, and `DROP`.

Other options:

```
log_statement = 'none'
log_statement = 'ddl'
log_statement = 'mod'
log_statement = 'all'
```

Be careful with `all`: it can generate huge amounts of logs and potentially expose sensitive data.

2. pgAudit

pgAudit is a PostgreSQL extension specifically designed for auditing.

It can record activities such as:

- SELECT
    
- INSERT
    
- UPDATE
    
- DELETE
    
- DDL operations
    
- Role and permission changes
    

For example, you can configure it to audit read and write operations.

3. Audit triggers

You can create triggers that record changes to particular tables.

For example:

```
CREATE TABLE employee_audit (
    employee_id INT,
    old_salary NUMERIC,
    new_salary NUMERIC,
    changed_at TIMESTAMP DEFAULT NOW()
);
```

A trigger can insert a record into this table whenever an employee's salary changes.

Important distinction:

- Logging tells you what SQL was executed.
    
- Audit triggers can record old and new row values.
    
- pgAudit provides structured auditing of database activity, but doesn't automatically provide a complete old/new row history for every operation.

---
[[Database]]