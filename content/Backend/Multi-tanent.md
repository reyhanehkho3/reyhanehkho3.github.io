---
title: Multi tanent
publish: true
date created: 2026-10-07
tags:
  - backend
---
A **multi-tenant architecture** is an architecture where **one application serves multiple separate customers (tenants)** while keeping their data and access isolated.

The easiest example is something like **Slack**.

Imagine Slack has:

```text
                    Slack Application
                           │
          ┌────────────────┼────────────────┐
          ↓                ↓                ↓
       Company A        Company B        Company C
       "Google"         "Acme"           "Startup X"
```

All three companies use the **same application**, but:

- Google's users shouldn't see Acme's messages.
    
- Acme shouldn't see Startup X's data.
    
- Each company has its own users, settings, projects, etc.
    

Each company is a **tenant**.

---

## The simplest database example

Suppose you have:

```text
users
--------------------------------
id | name   | tenant_id
1  | Alice  | 10
2  | Bob    | 10
3  | John   | 20
4  | Sara   | 20
```

Here:

```text
tenant_id = 10 → Company A
tenant_id = 20 → Company B
```

When Alice requests users:

```http
GET /users
```

the backend knows Alice belongs to tenant `10`, so it effectively does:

```sql
SELECT *
FROM users
WHERE tenant_id = 10;
```

Alice sees:

```text
Alice
Bob
```

She **must not** see:

```text
John
Sara
```

---

# Why is it called "multi-tenant"?

Think of an apartment building:

```text
             Apartment Building
          ┌─────────────────────┐
          │                     │
          │  Apartment 101      │ ← Tenant A
          │                     │
          │  Apartment 102      │ ← Tenant B
          │                     │
          │  Apartment 103      │ ← Tenant C
          │                     │
          └─────────────────────┘
```

They share the same building:

> **one application/infrastructure**

but have separate spaces:

> **separate tenant data**

That's the basic idea.

---

# There are several ways to implement it

This is where things get interesting.

### 1. Shared database + shared tables

Probably the simplest:

```text
PostgreSQL
│
├── users
├── projects
├── messages
└── ...
```

Every relevant row has:

```text
tenant_id
```

Example:

```text
messages
-------------------------------------
id | tenant_id | user_id | message
1  | 10        | 1       | Hello
2  | 10        | 2       | Hi
3  | 20        | 3       | Hello
```

This is often called **shared-schema multi-tenancy**.

It's cheap and relatively simple, but you have to be **very careful about data isolation**.

A bug like:

```sql
SELECT * FROM messages;
```

could accidentally expose data from every tenant.

---

### 2. Shared database + separate schemas

You could have:

```text
PostgreSQL
│
├── company_a schema
│   ├── users
│   └── messages
│
├── company_b schema
│   ├── users
│   └── messages
│
└── company_c schema
    ├── users
    └── messages
```

Now each tenant gets its own PostgreSQL schema.

This gives stronger separation, but managing lots of tenants becomes more complicated.

---

### 3. Separate database per tenant

You could even do:

```text
PostgreSQL DB: company_a
PostgreSQL DB: company_b
PostgreSQL DB: company_c
```

Now Company A's data is physically separate from Company B's.

This provides stronger isolation, but is much more expensive and operationally complicated.

---

# So what's the trade-off?

|Architecture|Isolation|Complexity|Cost|
|---|---|---|---|
|Shared tables|Low/medium|Low|Low|
|Separate schemas|Medium/high|Medium|Medium|
|Separate DB|High|High|High|

There isn't one universally correct choice.

For example, a SaaS startup with **10,000 small customers** probably doesn't want 10,000 completely separate databases.

But a company handling highly sensitive enterprise data might prefer stronger isolation.

---

## One REALLY important part: authentication

Imagine this request:

```http
GET /projects/123
Authorization: Bearer <token>
```

It's **not enough** to check:

```text
Does this user have permission?
```

You also need to check:

```text
Does this project belong to the user's tenant?
```

Conceptually:

```text
User
 │
 ├── tenant_id = 10
 │
 ↓
Request project 123
 │
 ↓
Does project 123 belong to tenant 10?
 │
 ├── YES → allow
 │
 └── NO  → 403 / 404
```

This is one of the biggest concerns in multi-tenant systems:

> **Tenant isolation must be enforced at every relevant data-access boundary.**

You don't want a developer accidentally writing:

```sql
SELECT * FROM projects WHERE id = 123;
```

when they should effectively be doing:

```sql
SELECT *
FROM projects
WHERE id = 123
  AND tenant_id = 10;
```

---

## And multi-tenant ≠ multi-user

These are easy to confuse.

**Multi-user:**

```text
One application
    ↓
Alice
Bob
Sara
```

**Multi-tenant:**

```text
One application
    ↓
Company A
 ├── Alice
 └── Bob

Company B
 ├── Sara
 └── John
```

So a **tenant is usually an organization/customer/account boundary**, while users belong to a tenant.

For something like your AI chat platform, if later you wanted **different companies to use the same platform**, each company could be a tenant:

```text
AI Chat Platform
│
├── Company A
│   ├── users
│   ├── sessions
│   └── messages
│
├── Company B
│   ├── users
│   ├── sessions
│   └── messages
│
└── Company C
    ├── users
    ├── sessions
    └── messages
```

That's when you'd start thinking about **multi-tenant architecture**.



---
[[Back-End]]