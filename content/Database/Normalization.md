---
title: Normalization
publish: true
date created: 2026-09-05
tags:
  - database
  - codeless
---
**Definition:** Normalization is the process of **organizing data into separate, related tables** to reduce unnecessary duplication and keep data consistent. 

It uses a set of rules called **normal forms** (such as 1NF, 2NF, and 3NF) to decide how the data should be structured. 

### Simple example

Suppose you start with this:

|Order|Customer|Customer Email|Product|
|---|---|---|---|
|1|Ali|[ali@mail.com](mailto:ali@mail.com)|Laptop|
|2|Ali|[ali@mail.com](mailto:ali@mail.com)|Mouse|
|3|Sara|[sara@mail.com](mailto:sara@mail.com)|Phone|

Notice that **Ali's email is stored twice**.

With normalization, you separate the data:

**Customers**

|id|name|email|
|---|---|---|
|1|Ali|[ali@mail.com](mailto:ali@mail.com)|
|2|Sara|[sara@mail.com](mailto:sara@mail.com)|

**Orders**

|id|customer_id|product|
|---|---|---|
|1|1|Laptop|
|2|1|Mouse|
|3|2|Phone|

Now Ali's email is stored **only once**, and `customer_id` connects the order to the customer. This reduces redundancy and helps prevent update, insertion, and deletion anomalies. ([IBM](https://www.ibm.com/think/topics/database-normalization?utm_source=chatgpt.com "What Is Database Normalization? | IBM"))

### The main normal forms

You don't need to memorize the formal definitions yet. Think of them progressively:

- **1NF:** Each field contains a single value; don't put lists/repeating groups inside columns.
    
- **2NF:** Every non-key field must depend on the **whole primary key**, especially when the key has multiple columns.
    
- **3NF:** Non-key fields should depend on the **key, not on another non-key field**. ([IBM](https://www.ibm.com/think/topics/database-normalization?utm_source=chatgpt.com "What Is Database Normalization? | IBM"))
    

### 3 good examples

1. **E-commerce:** Instead of storing a customer's name and address in every order, have `Customers` and `Orders` tables connected by `customer_id`.
    
2. **University:** Instead of putting course information into every student's record, have `Students`, `Courses`, and `Enrollments` tables.
    
3. **Company:** Instead of storing `"Engineering"` repeatedly for every employee, create a `Departments` table and store `department_id` in `Employees`.
    

### Easy way to remember

> **Normalization = Don't repeat information unnecessarily; store it once and connect it with keys.**

One important point: **normalization isn't simply "make as many tables as possible."** Too much normalization can mean more joins and potentially more complex queries, so real systems sometimes deliberately use **denormalization** for performance. ([IBM](https://www.ibm.com/think/topics/database-normalization?utm_source=chatgpt.com "What Is Database Normalization? | IBM"))


---
[[Database]]
[[My-Journey-In-Codeless]]