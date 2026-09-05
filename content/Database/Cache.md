---
title: Cache
publish:
date created: 2026-09-05
tags:
  - database
  - codeless
---
**Definition:** A cache is a **fast, temporary storage layer** that keeps copies of frequently used or recently computed data so it can be returned faster than getting it from the original source. ([Amazon Web Services, Inc.](https://aws.amazon.com/caching/?utm_source=chatgpt.com "What is Caching and How it Works | AWS"))  
Its main purpose is to **reduce response time and reduce load** on slower systems such as databases, APIs, or disk storage. ([Microsoft Learn](https://learn.microsoft.com/en-us/microsoft-cloud/dev/dev-proxy/concepts/what-is-caching?utm_source=chatgpt.com "What Is Caching? - Dev Proxy | Microsoft Learn"))

### Simple example

Imagine your application frequently asks PostgreSQL:

```text
"Give me user #123"
```

Without cache:

```text
Application → PostgreSQL → User #123
```

With cache:

```text
Application → Cache → User #123
                  ↓
             PostgreSQL
             (only if cache doesn't have it)
```

The first request might get the data from PostgreSQL and put it in the cache. The next requests can get it directly from the much faster cache.

### 3 examples

1. **Website:** A frequently visited homepage is cached so the server doesn't generate it from scratch for every visitor.
    
2. **Database:**
    
    ```text
    product:123 → {name: "Laptop", price: 1200}
    ```
    
    The application can retrieve the product from the cache instead of querying the database every time.
    
3. **Browser:** Your browser caches images, CSS, and other website files so that when you revisit the site, it doesn't need to download everything again. ([TechTarget](https://www.techtarget.com/whatis/definition/caching?utm_source=chatgpt.com "What is caching and how does it work? – TechTarget Definition"))
    

### Cache hit vs. cache miss

**Cache hit:** The requested data is already in the cache → **fast** ⚡

**Cache miss:** The data isn't in the cache → get it from the original source, then potentially store it in the cache. ([Wikipedia](https://en.wikipedia.org/wiki/Cache_%28computing%29?utm_source=chatgpt.com "Cache (computing)"))

### Important

A cache is generally **not the source of truth**. It's a temporary copy of data that exists somewhere else, such as your database. If the cache disappears, the application should normally be able to retrieve the data again from the original source. ([Amazon Web Services, Inc.](https://aws.amazon.com/caching/?utm_source=chatgpt.com "What is Caching and How it Works | AWS"))

**Easy way to remember:**

> **Database = where the data lives.**  
> **Cache = a faster temporary copy of data you need frequently.**


---
[[My-Journey-In-Codeless]]
[[Database]]