---
title: Load Balancer
publish:
date created: 2026-09-05
tags:
  - codeless
  - Backend
---
**Definition:** A load balancer is a component that receives incoming traffic and **distributes it across multiple servers/instances** instead of sending everything to one server.  
It helps applications handle more traffic, improve performance, and remain available when one server becomes unhealthy. ([Microsoft Learn](https://learn.microsoft.com/en-us/azure/load-balancer/load-balancer-overview?utm_source=chatgpt.com "What is Azure Load Balancer? - Azure Load Balancer | Microsoft Learn"))

### Simple example

Without a load balancer:

```text
Users
  │
  ▼
Server 1
```

If 10,000 users arrive, **Server 1 has to handle everyone**.

With a load balancer:

```text
                 ┌──→ Server 1
Users → Load ────┼──→ Server 2
        Balancer └──→ Server 3
```

The load balancer decides where each incoming request should go. It can also check server health and stop sending traffic to an unhealthy server. ([AWS Documentation](https://docs.aws.amazon.com/elasticloadbalancing/latest/userguide/how-elastic-load-balancing-works.html?utm_source=chatgpt.com "How Elastic Load Balancing works - Elastic Load Balancing"))

### 3 examples

**1. E-commerce website**

```text
1000 requests
      ↓
Load Balancer
 ┌────┼────┐
 ↓    ↓    ↓
S1   S2   S3
```

Instead of one server becoming overloaded during a sale, requests are distributed across several servers.

**2. Server failure**

```text
Load Balancer
 ├── Server 1 ✓
 ├── Server 2 ❌
 └── Server 3 ✓
```

If Server 2 becomes unhealthy, the load balancer can stop sending requests to it and continue using the healthy servers. ([AWS Documentation](https://docs.aws.amazon.com/elasticloadbalancing/latest/userguide/how-elastic-load-balancing-works.html?utm_source=chatgpt.com "How Elastic Load Balancing works - Elastic Load Balancing"))

**3. Scaling**

You have:

```text
Load Balancer
   ├── Server 1
   └── Server 2
```

Traffic increases, so you add Server 3:

```text
Load Balancer
   ├── Server 1
   ├── Server 2
   └── Server 3
```

You can add/remove backend resources as demand changes without changing how clients reach the application. ([AWS Documentation](https://docs.aws.amazon.com/elasticloadbalancing/latest/userguide/what-is-load-balancing.html?utm_source=chatgpt.com "What is Elastic Load Balancing? - Elastic Load Balancing"))

### How does it decide where to send requests?

Common strategies include:

- **Round Robin:** Server 1 → Server 2 → Server 3 → Server 1...
    
- **Least Connections:** Send the request to the server currently handling the fewest connections.
    
- **Health-based:** Don't send traffic to unhealthy servers.
    
- **Weighted:** Give more traffic to more powerful servers. ([Amazon Web Services, Inc.](https://aws.amazon.com/what-is/load-balancing/?utm_source=chatgpt.com "What is Load Balancing? - Load Balancing Algorithm Explained - AWS"))
    

**Easy way to remember:**

> **Load balancer = traffic manager for your servers.**  
> Instead of **1000 users → 1 server**, it makes **1000 users → multiple servers**.


---
[[Back-End]]
[[My-Journey-In-Codeless]]