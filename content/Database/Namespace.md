---
title: Namespace
publish: true
date created: 2026-10-20
tags:
  - database
---
A namespace in a database is a way to group and organize database objects (like tables, views, and functions) under a specific name.

Think of it like a folder on your computer.

## 1. Simple example

Imagine you have a database for an online store. It contains tables for users, products, and orders.

Without namespaces, things can get messy as your project grows. With namespaces, you can organize tables into groups.

Online Store Database

users namespace

customers

profiles

sales namespace

orders

payments

The namespace helps you identify which group an object belongs to.

## 2. What does it look like in SQL?

In PostgreSQL, a namespace is commonly represented by a schema.

For example:

```
SELECT * FROM users.customers;
SELECT * FROM sales.orders;
```

Here:

- `users` is the schema (namespace).
    
- `customers` is the table.
    
- `sales` is another schema.
    
- `orders` is another table.
    

Two schemas can even contain tables with the same name:

```
SELECT * FROM sales.orders;
SELECT * FROM support.orders;
```

Both tables are called `orders`, but they belong to different schemas.

## 3. Namespace vs. database vs. schema

|Term|Meaning|
|---|---|
|Database|The overall container holding data and database objects|
|Schema / namespace|A logical group of database objects inside a database|
|Table|Stores data in rows and columns|
|Column|Stores a particular field of data|

For PostgreSQL, the typical hierarchy is:

`Database → Schema → Table → Column`

## 4. Why is a namespace useful?

- Organization: Groups related tables together.
    
- Avoiding name conflicts: Different schemas can contain tables with identical names.
    
- Permissions: You can control access to particular schemas and their objects.
    
- Multi-tenant applications: You can sometimes isolate different customers' data into separate schemas.
    

One important detail: namespace doesn't always mean schema. In PostgreSQL, it often does, but in other database systems or tools, it may have a different meaning.

In short: A namespace is a naming and organizational boundary that helps distinguish database objects from one another.

---
[[Database]]