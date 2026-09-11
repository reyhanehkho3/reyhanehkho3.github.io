---
title: Vertical Scaling
publish: true
date created: 2026-09-11
tags:
  - Backend
  - Architecture
  - codeless
---
Also called **scaling up**.

You have one server:

```
             ┌───────────────┐
Users ──────►│    Server     │
             │               │
             │  4 CPU        │
             │  8 GB RAM     │
             │  100 GB SSD   │
             └───────────────┘
```

Your application runs there.

If your application becomes too slow, you upgrade the server:

```
             ┌──────────────────────┐
Users ──────►│       Server         │
             │                      │
             │      32 CPU          │
             │      128 GB RAM      │
             │      2 TB SSD        │
             └──────────────────────┘
```

You're making the **same machine more powerful**.

### Example

You have:

```
8 GB RAM
4 CPU
```

and upgrade to:

```
64 GB RAM
16 CPU
```

That's vertical scaling.


---
[[Back-End]]
[[My-Journey-In-Codeless]]