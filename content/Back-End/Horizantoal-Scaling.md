---
title: Horizontal Scaling
publish: true
date created: 2026-09-11
tags:
  - Backend
  - Architecture
  - codeless
---
Also called **scaling out**.

Instead of making one server bigger, you add more servers.

```
                 ┌──────────────┐
             ┌──►│   Server 1   │
             │   └──────────────┘
             │
Users ────────┤   ┌──────────────┐
             ├──►│   Server 2   │
             │   └──────────────┘
             │
             │   ┌──────────────┐
             └──►│   Server 3   │
                 └──────────────┘
```

Now requests can be distributed between the servers.

Usually you'd put a **load balancer** in front:

```
                       ┌──────────────┐
                       │ Load Balancer│
                       └───────┬──────┘
                               │
                 ┌─────────────┼─────────────┐
                 ▼             ▼             ▼
            ┌─────────┐  ┌─────────┐  ┌─────────┐
            │ Server 1│  │ Server 2│  │ Server 3│
            └─────────┘  └─────────┘  └─────────┘
```

The load balancer decides where requests go.

# Why would you use horizontal scaling?

Imagine you have:

```
100 users
     ↓
  Server 1
```

Everything is fine.

Then you get:

```
100,000 users
```

One server might not be enough.

You could make it much bigger:

```
One giant server
128 CPU
512 GB RAM
```

That's vertical scaling.

Or:

```
Server 1
Server 2
Server 3
Server 4
Server 5
...
```

That's horizontal scaling.


- horizontally scaled applications generally need shared/external state for things that must be visible across instances.For example:

```
             ┌─────────────┐
             │Load Balancer│
             └──────┬──────┘
                    │
          ┌─────────┼─────────┐
          ▼         ▼         ▼
       Server 1  Server 2  Server 3
          │         │         │
          └─────────┼─────────┘
                    ▼
                Database
```

And possibly:

```
                    ┌──────────┐
                    │  Redis   │
                    └──────────┘
                         ▲
                         │
       ┌─────────────────┼─────────────────┐
       │                 │                 │
   Server 1          Server 2          Server 3
```

Redis might hold shared sessions/cache, while PostgreSQL holds persistent application data.

---
[[Back-End]]
[[My-Journey-In-Codeless]]