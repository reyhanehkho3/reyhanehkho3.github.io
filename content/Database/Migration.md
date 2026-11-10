---
title: Migration
publish: true
date created: 2026-11-10
tags:
  - dba-agent
  - database
---
Migration means moving a database from one state or environment to another.

There are two particularly important meanings of database migration.

## A. Schema migration

This means changing the structure of an existing database over time.

Imagine your application initially has:

```
CREATE TABLE users (
    id SERIAL PRIMARY KEY,
    name VARCHAR(100)
);
```

Later, your application needs an email column.

You create a migration:

```
ALTER TABLE users
ADD COLUMN email VARCHAR(255);
```

Later, you want email to be unique:

```
ALTER TABLE users
ADD CONSTRAINT unique_user_email UNIQUE(email);
```

Each change represents a migration step.

Instead of manually changing production databases, developers use migration tools to manage these changes.

Popular tools:

- Flyway
    
- Liquibase
    
- Alembic
    
- Prisma Migrate


### How does it work?

Imagine your application has three migration files:

V1 — Create users table

`CREATE TABLE users (...)`

V2 — Add email column

`ALTER TABLE users ADD COLUMN email ...`

V3 — Add unique constraint

`ALTER TABLE users ADD CONSTRAINT ...`

Current database schema:

Users table

id · name · email (unique)

Migration tools track which migration files have already been executed.

This means you can deploy your application to different environments and keep their database schemas synchronized.

For example:

- Development database
    
- Testing database
    
- Staging database
    
- Production database
    

## B. Database migration between servers

This is a different meaning.

Imagine your company currently has PostgreSQL running on Server A, but wants to move to Server B.

You need to migrate:

- Database structures.
    
- Table data.
    
- Indexes.
    
- Constraints.
    
- Roles and permissions.
    
- Other relevant database objects.
    
- Potentially ongoing changes during the transition.
    

This can involve logical backups, physical backups, replication, or specialized migration tools.


A migration might happen because:

- The company is changing its infrastructure.
    
- The database is moving to another server.
    
- The company is upgrading PostgreSQL.
    
- The company is moving from one database engine to another.
    

Important distinction:

|Schema migration|Server/database migration|
|---|---|
|Changes database structure|Moves a database or workload|
|Adds columns, indexes, constraints|Moves data and database objects|
|Usually part of application development|Usually part of infrastructure or DBA work|


---
[[Database]]