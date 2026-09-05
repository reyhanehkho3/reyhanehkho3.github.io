---
title: Document Database
publish: true
date created: 2026-09-05
tags:
  - database
  - codeless
---
**Definition:** A document database is a type of **NoSQL database** that stores data as flexible documents, usually in a JSON-like format, instead of fixed rows and columns.  
Each document can have a different structure, which makes it useful when your data changes or contains nested information. 

### Simple example

Instead of this relational structure:

```text
Users
----------------
id | name | email
1  | Ali  | ali@mail.com

Orders
----------------
id | user_id | product
10 | 1       | Laptop
```

A document database could store the user and their related information together:

```json
{
  "id": 1,
  "name": "Ali",
  "email": "ali@mail.com",
  "orders": [
    {
      "product": "Laptop",
      "price": 1200
    }
  ]
}
```

So the idea is basically:

**Relational DB → tables → rows → columns → relationships**

**Document DB → collections → documents → fields/values** ([MongoDB University](https://learn.mongodb.com/learn/course/relational-to-document-model/?utm_source=chatgpt.com "Relational (SQL) to Document Model | MongoDB University"))

### 3 examples

1. **E-commerce:** Store a product with its specifications, images, reviews, and different variants inside a flexible document.
    
2. **Social media:** Store a user's profile together with preferences, interests, and settings that may differ from user to user.
    
3. **IoT:** Store sensor readings where different devices may produce different types of data. ([MongoDB](https://www.mongodb.com/resources/basics/databases/document-databases?msockid=115c3f6ec0d96edf225129cec1a26fac&utm_source=chatgpt.com "Document Database - NoSQL | MongoDB"))
    

### Common example

**MongoDB** is a popular document database. It stores documents in a JSON-like format called **BSON**. ([Google Cloud](https://cloud.google.com/discover/what-is-mongodb?utm_source=chatgpt.com "What is MongoDB? | Google Cloud"))

**Easy way to remember:**

> **Relational database = spreadsheet-like tables.**  
> **Document database = JSON-like objects.**



---
[[Database]]
[[My-Journey-In-Codeless]]