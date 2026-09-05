---
title: Relational Database
publish: true
date created: 2026-09-05
tags:
  - database
  - codeless
---
**Definition:** A relational database stores data in **tables made of rows and columns**, where each table represents a type of thing, such as users, products, or orders.  
The tables can be **connected to each other through relationships**, usually using primary keys and foreign keys, and SQL is commonly used to work with the data.

### Simple example

Imagine an online shop:

**Users table**

|id|name|
|---|---|
|1|Alice|
|2|Bob|

**Orders table**

|id|user_id|product|
|---|---|---|
|101|1|Laptop|
|102|1|Mouse|
|103|2|Keyboard|

Here:

- `Users.id` → **Primary Key**: uniquely identifies each user.
    
- `Orders.user_id` → **Foreign Key**: points to a user.
    
- Because `Orders.user_id = Users.id`, we know **which user made which order**. ([Microsoft Learn](https://learn.microsoft.com/en-us/sql/relational-databases/tables/primary-and-foreign-key-constraints?view=sql-server-ver17&utm_source=chatgpt.com "Primary and foreign key constraints - SQL Server | Microsoft Learn"))
    

### Why is it called "relational"?

Because the important idea is that **data in different tables has relationships**.

```text
Users
  │
  │ user_id
  ▼
Orders
  │
  │ product_id
  ▼
Products
```

So instead of putting everything into one giant table, you separate related information into logical tables and connect them.

### 3 examples

1. **Banking:** `Customers` ↔ `Accounts` ↔ `Transactions`
    
2. **University:** `Students` ↔ `Courses` ↔ `Enrollments`
    
3. **E-commerce:** `Users` ↔ `Orders` ↔ `Products`
    

Common relational databases include **PostgreSQL, MySQL, Microsoft SQL Server, and Oracle Database**.

**In one sentence:**

> A relational database is basically **organized tables + relationships between those tables**. 


---
[[Database]]
[[My-Journey-In-Codeless]]