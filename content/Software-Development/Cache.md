---
title: Cache
publish:
date created: 2026-08-23
tags:
  - DB
  - software-development
  - codeless
---
## Cache Vs. DB
This is one of the most fundamental trade-offs in software engineering. 

The short answer: **A database is your source of truth (permanent storage). A cache is a speed-of-light shortcut (temporary storage).** 

You don't choose *between* them; you choose *how* they work together. Here is the breakdown.

### 1. The Core Definitions
- **Database (DB)**: A persistent, durable, and usually authoritative storage system. Data is written to disk (SSD/HDD). It is optimized for **integrity, relationships, and complex queries** (ACID compliance, indexing, joins).
- **Cache**: A temporary, high-speed storage layer (usually stored in RAM). It stores a subset of data so that future requests for that data are served **faster**. It is optimized for **speed and throughput**.

### 2. The Head-to-Head Comparison

| Feature | Database (e.g., PostgreSQL, MySQL, MongoDB) | Cache (e.g., Redis, Memcached, CPU L1/L2) |
| :--- | :--- | :--- |
| **Primary Goal** | Durability & Consistency | Speed & Latency reduction |
| **Storage** | Disk (persistent) + RAM | RAM (volatile) |
| **Data Size** | Terabytes to Petabytes (entire dataset) | Gigabytes (subset of hot data) |
| **Read Speed** | Milliseconds (disk I/O) | Microseconds to Nanoseconds (memory I/O) |
| **Write Speed** | Slower (must write to disk, enforce constraints) | Blazing fast (just writes to RAM) |
| **Data Stale?** | Never. Always the absolute source of truth. | **Yes.** Data is frequently out-of-date (stale) by design. |
| **Query Power** | Complex (JOINs, aggregations, full-text search) | Extremely simple (Key-Value lookups, basic sets/sorted sets) |

---

### 3. The Golden Rule: "Cache Aside"
In 95% of applications, you use the **Cache-Aside** strategy:

1. When reading, **check the cache first**.
2. If found (a **"cache hit"**), return it instantly. **Do not touch the DB.**
3. If not found (a **"cache miss"**), query the database, save the result into the cache, and return it to the user.

*This means your cache is always a **copy** of what is in the DB, never the master.*

---

### 4. When to use a Cache (and when NOT to)

**✅ USE a cache when:**

- You have **read-heavy** workloads (e.g., social media feeds, product catalogs).
- The same data is requested repeatedly (e.g., a celebrity's profile, top 10 bestselling items).
- Computations are expensive (e.g., a complex ML inference result or a heavy SQL aggregate query).
- You need to absorb **traffic spikes** (a cache protects your DB from dying under load).

**❌ DO NOT use a cache when:**

- Data changes **every millisecond** (e.g., a stock ticker—the cache would be invalidated before you even use it).
- You need **absolute 100% accuracy** (e.g., bank account balances, medical records).
- Your dataset is tiny (e.g., a config file with 100 rows—just query the DB directly).

---

### 5. The Hardest Problem: Cache Invalidation
There are only two hard things in Computer Science: **cache invalidation** and naming things. 

Because the cache is a copy, when you `UPDATE` or `DELETE` data in the Database, the cache now holds **stale (old) data**. 

You have three strategies to handle this:

1. **Write-Through**: Write to the DB *and* the cache at the same time (slower writes, but cache is always fresh).
2. **Write-Around**: Write only to the DB. When the cache expires (TTL - Time To Live), it fetches the new data (simplest, most common).
3. **Write-Back**: Write only to the cache, and asynchronously flush to the DB later (fastest writes, **risky**—if the cache crashes, you lose data).

---

### 6. The Real-World Architecture
In modern microservices, this looks like:

```
[User Request]
      |
      v
[Application Server]
      |
      v
[Redis Cache]  <--- If miss --->  [PostgreSQL Database]
      |                                  |
      |--- Return Data -------------------|
```

*But wait!* There is also a **Database Cache** (built-in buffer pool). Postgres and MySQL keep a "cache" of frequently accessed disk pages in RAM internally. So even when you "query the DB," you might be reading from RAM, not the physical disk.

---

### The Ultimate Summary for Developers

| Scenario | What to do |
| :--- | :--- |
| **User logs in** | Query DB directly (auth requires authority). |
| **User views their order history** | Check Cache first (Redis), fallback to DB. |
| **User places a new order** | Write to DB **and** delete the old cache entry (so next read fetches fresh data). |
| **User views the "Trending Products" page** | Cache this for 5 minutes. Even if it's 1 second stale, nobody cares, and you save the DB from 10,000 queries. |

**The Pro-Tip:** Never cache *everything*. Only cache data that is **expensive to compute** and **slow to change**. Your database is your fortress; the cache is your moat. Protect the fortress, but don't try to live in the moat.



---

[[Back-End]]
[[My-Journey-In-Codeless]]
[[Database]]