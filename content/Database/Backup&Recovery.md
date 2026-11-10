---
title: Backup and Recovery
publish: true
date created: 2026-11-10
tags:
  - database
  - dba-agent
---
This category is about protecting data against failures.

Imagine your database server crashes, or someone accidentally executes:

```
DROP TABLE orders;
```

How do you recover?

## 4.1 Backup

A backup is a copy of your database that you can use to restore data.

PostgreSQL has several backup approaches.

|Method|Explanation|
|---|---|
|Logical backup|Exports database objects and data|
|Physical backup|Copies database files|
|Continuous archiving|Saves WAL files for recovery|

Example of a logical backup:

```
pg_dump -U postgres -d mydb -F c -f mydb.backup
```

## 4.2 Restore

Restore means recovering a database from a backup.

```
pg_restore -U postgres -d mydb mydb.backup
```

A backup is only useful if you know it can actually be restored. DBAs should regularly test restoration.

## 4.3 WAL (Write-Ahead Logging)

This is a very important PostgreSQL concept.

Before PostgreSQL considers certain changes safely committed, it records the necessary information in its WAL.

Think of WAL as a sequential record of database changes that PostgreSQL uses for crash recovery and replication.

WAL is useful for:

- Crash recovery.
    
- Replication.
    
- Point-in-Time Recovery.
    

## 4.4 PITR (Point-in-Time Recovery)

Imagine:

- You took a backup at 02:00.
    
- Someone accidentally deleted important records at 14:30.
    
- You discovered the problem at 14:45.
    

Can you recover the database to 14:29?

Yes, if you have a valid base backup and the required WAL archive.

This is called Point-in-Time Recovery (PITR).

Instead of restoring only the last backup, you replay WAL records until the desired recovery time.

---
[[Database]]