---
title: Redis
publish: true
date created: 2026-08-31
tags:
  - database
  - codeless
---
**Definition:** **Redis** is a fast, in-memory **NoSQL data store** that stores data primarily in RAM using key-value structures; it can be used as a database, cache, message broker, and more.  
Because data is kept in memory, Redis can provide very low-latency access, while it also supports persistence to disk when needed.

### 3 good examples

1. **Caching**
    
    ```
    User → API → Redis → Product information
                    ↓
                 PostgreSQL
    ```
    
    Frequently requested products can be kept in Redis so the application doesn't query PostgreSQL every time.
    
2. **Session storage**
    
    ```
    session:abc123 → {
        userId: 42,
        role: "customer"
    }
    ```
    
    Redis can store login/session information with an expiration time (TTL).
    
3. **Rate limiting**
    
    ```
    user:42:requests → 57
    ```
    
    You can count how many API requests a user has made and reject requests after, for example, 100 requests per minute. Redis's atomic operations and expiration make this pattern useful.


---
[[Database]]
[[My-Journey-In-Codeless]]