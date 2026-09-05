---
title: Graph Database
publish: true
date created: 2026-09-05
tags:
  - database
  - codeless
---
**Definition:** A graph database stores data as **nodes (things)** and **relationships (connections between things)** instead of mainly using tables and rows.  
It is especially useful when the **relationships between data are important**, such as people connected to friends, products, or transactions. ([Neo4j Graph Intelligence Platform](https://neo4j.com/docs/getting-started/graph-database/?utm_source=chatgpt.com "What is a graph database - Getting Started"))

### Simple example

Imagine a social network:

```text
(Alice) ──FRIENDS_WITH──> (Bob)
   │                         │
   │ FOLLOWS                 │ FOLLOWS
   ▼                         ▼
(Charlie) <────────────── (David)
```

Here:

- **Nodes** = Alice, Bob, Charlie, David
    
- **Relationships** = `FRIENDS_WITH`, `FOLLOWS`
    
- **Properties** = things like `name`, `age`, `location`
    

The important thing is that the **connections themselves are stored as part of the database**, making it easy to traverse from one entity to another. ([Neo4j Graph Intelligence Platform](https://neo4j.com/docs/getting-started/appendix/graphdb-concepts/?utm_source=chatgpt.com "Graph database concepts - Getting Started"))

### 3 examples

1. **Social network:**  
    `Alice → FRIENDS_WITH → Bob → FOLLOWS → Charlie`  
    You can quickly find connections between users.
    
2. **Recommendation system:**  
    `User → BOUGHT → Product → BELONGS_TO → Category`  
    You can find products related to things a user already bought.
    
3. **Fraud detection:**  
    `Person → OWNS → Account → USED_AT → Device`  
    If many suspicious accounts are connected to the same device, the relationships can reveal a possible fraud network.
    

### Common example

**Neo4j** is a popular graph database. Its basic model is:

```text
Node ── Relationship ── Node
```

For example:

```text
(Reyhaneh) ──WORKS_AT──> (Company)
```

Neo4j uses this **property graph** model, where both nodes and relationships can contain properties. ([Neo4j Graph Intelligence Platform](https://neo4j.com/docs/getting-started/graph-database/?utm_source=chatgpt.com "What is a graph database - Getting Started"))

**Easy way to remember:**

> **Relational DB:** “What data do I have?” → Tables  
> **Document DB:** “What does this object look like?” → Documents  
> **Key-Value DB:** “I know the key; give me the value.”  
> **Graph DB:** **“How are these things connected?”**


---
[[Database]]
[[My-Journey-In-Codeless]]