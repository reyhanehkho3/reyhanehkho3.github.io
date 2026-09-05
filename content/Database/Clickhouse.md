---
title: Clickhouse
publish: true
date created: 2026-08-31
tags:
  - database
  - codeless
---
**Definition:** **ClickHouse** is an open-source, column-oriented **OLAP database** designed for very fast analytical queries over huge amounts of data.  
**Instead of storing data primarily row-by-row like PostgreSQL/MySQL, it stores values column-by-column, which makes operations such as filtering, grouping, and aggregation over millions or billions of rows very efficient.**

### 3 good examples

**1. E-commerce analytics**

Suppose you have 500 million orders:

```
"What was our revenue for each country
 during the last 12 months?"
```

ClickHouse can scan the relevant columns and aggregate a huge number of rows efficiently.

---

**2. Application logs**

You have billions of logs:

```
timestamp | service | status | response_time | message
```

You can ask:

```
"How many 500 errors did Payment Service
 have yesterday?"
```

ClickHouse is commonly used for **observability**, including logs, metrics, and traces.

---

**3. Real-time dashboard**

Imagine an online shop dashboard:

```
Sales today:       €152,430
Orders today:       8,421
Average order:      €18.10
Top country:        Germany
```

ClickHouse is designed for real-time analytics and can analyze very large datasets with low query latency.

### ClickHouse vs PostgreSQL

A simple way to remember the difference:

```
PostgreSQL
    ↓
OLTP
    ↓
"Give me order #12345"
"Create this new order"
"Update this user's address"


ClickHouse
    ↓
OLAP
    ↓
"What were our sales by country?"
"What are our top 100 products?"
"How many requests did we receive per hour?"
```

ClickHouse **can support SQL and joins**, but its main strength is **large-scale analytical workloads**, rather than being the primary transactional database for things like user accounts, orders, and payments.

**Mental model:**

> **PostgreSQL = run the business.**  
> **ClickHouse = analyze what the business is doing.**


---
[[Database]]
[[My-Journey-In-Codeless]]