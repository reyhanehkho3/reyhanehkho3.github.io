---
title: Replica
publish:
date created: 2026-10-07
tags:
  - database
---
A **database replica** is basically a **copy of a database** that is kept synchronized with the original database.

Imagine you have:

```text
             Primary DB
             ┌─────────┐
             │ Users   │
             │ Orders  │
             │ Messages│
             └────┬────┘
                  │
          replication
             ┌────┴────┐
             ↓         ↓
        Replica 1   Replica 2
```

### Why do we need replicas?

The most common reason is **scaling reads**.

Suppose your application gets:

- 10,000 requests that **read** data
    
- 500 requests that **write** data
    

You can have:

```text
                 ┌─────────────┐
                 │  Primary DB │
                 │   writes    │
                 └──────┬──────┘
                        │
                 replication
                 ┌──────┴──────┐
                 ↓             ↓
           ┌──────────┐   ┌──────────┐
           │ Replica 1│   │ Replica 2│
           │  reads   │   │  reads   │
           └──────────┘   └──────────┘
```

So:

```text
CREATE / UPDATE / DELETE  → Primary

SELECT                     → Replicas
```

This allows you to handle many more read requests.

---

### But a replica isn't necessarily up-to-date

This is an important concept.

Suppose you do:

```sql
UPDATE users
SET name = 'Reyhan'
WHERE id = 10;
```

The change happens on the **primary** first.

Then it gets replicated:

```text
Primary
  │
  │ "user 10 changed"
  ↓
Replica
```

There can be a small delay.

So immediately afterward:

```text
Primary → name = "Reyhan"
Replica → name = "Old Name"
```

This is called **replication lag**.

Therefore, you shouldn't blindly assume that every replica always has exactly the latest data.

---

### Replicas are also useful for availability

Suppose your primary database crashes:

```text
Primary ❌
```

You can potentially promote a replica:

```text
Replica 1
    ↓
becomes
Primary
```

So replicas can help with **high availability / disaster recovery** as well as read scaling.

---

### One important distinction

A **replica is not the same thing as a backup**.

A backup is usually a historical copy:

```text
Monday backup
Tuesday backup
Wednesday backup
```

A replica is intended to stay synchronized with the primary:

```text
Primary ─────────→ Replica
   current          almost current
```

If someone accidentally executes:

```sql
DROP TABLE users;
```

that destructive operation can also replicate to the replica. So the replica doesn't necessarily protect you from logical mistakes.

---

### In simple terms

Think of it like a Google Docs document:

**Primary DB:** the original document where edits happen.

**Replicas:** synchronized copies that people can read from.

**Backup:** a saved copy from an earlier point in time.

So when you hear:

> "We use PostgreSQL with read replicas"

it usually means:

> **We have one PostgreSQL instance handling writes and one or more synchronized PostgreSQL instances handling reads.**


---
[[Database]]