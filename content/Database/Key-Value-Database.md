---
title: Key-Value Database
publish: true
date created: 2026-09-05
tags:
  - database
  - codeless
---
**Definition:** A key-value database is a type of **NoSQL database** that stores information as pairs: a unique **key** points directly to a **value**. 

It is especially useful when you already know the key and need to **retrieve data very quickly**, rather than performing complex queries or joins. ([AWS Builder Center](https://builder.aws.com/learn/topics/nosql?utm_source=chatgpt.com "#nosql | Topic | Learn | AWS Builder Center"))

### Simple example

Think of a dictionary:

```text
"username:123" → "Reyhaneh"
"session:abc"  → "user_id=123"
"cart:123"     → ["laptop", "mouse"]
```

You give the database the key:

```text
GET "session:abc"
```

and it gives you the value:

```text
"user_id=123"
```

The database doesn't need to search through lots of rows to find it—the **key directly identifies the value**. 

### 3 examples

1. **User sessions**
    
    ```text
    session:8f92 → {user_id: 42, logged_in: true}
    ```
    
    When the user makes a request, you can quickly retrieve their session.
    
2. **Caching**
    
    ```text
    product:123 → {name: "Laptop", price: 1200}
    ```
    
    Instead of repeatedly querying PostgreSQL, you can temporarily keep frequently used data in a key-value store. ([Couchbase](https://www.couchbase.com/resources/concepts/key-value-database/?utm_source=chatgpt.com "Key-Value Database | Concepts | Couchbase"))
    
3. **Gaming leaderboard**
    
    ```text
    player:987 → score: 15420
    ```
    
    The application can quickly retrieve or update a player's score. ([Dragonfly](https://www.dragonflydb.io/faq/key-value-database-use-cases?utm_source=chatgpt.com "[Answered] What are common use cases for key-value databases?"))
    

### Common examples

- **Redis** — very fast, commonly used for caching, sessions, and real-time data. ([Redis](https://redis.io/tutorials/what-is-redis/?utm_source=chatgpt.com "What is Redis? In-memory database, cache, and message broker"))
    
- **Amazon DynamoDB** — a managed database supporting key-value and document models. ([Amazon Web Services, Inc.](https://aws.amazon.com/nosql/key-value/?utm_source=chatgpt.com "What is a Key Value Database? - Key Value DB and Pairs Explained - AWS"))
    
- **Memcached** — commonly used for simple in-memory caching. ([techtarget.com](https://www.techtarget.com/data-technologies/tip/NoSQL-database-types-explained-Key-value-store?utm_source=chatgpt.com "NoSQL database types explained: Key-value store | TechTarget"))
    

**Easy way to remember:**

> **Relational DB:** “Find all users whose age is greater than 20.”  
> **Document DB:** “Give me this user's document.”  
> **Key-Value DB:** **“I know the key → just give me its value.”**



---
[[Database]]
[[My-Journey-In-Codeless]]