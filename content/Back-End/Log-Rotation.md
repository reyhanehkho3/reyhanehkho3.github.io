---
title: Log Rotation
publish: true
date created: 2026-09-11
tags:
  - Backend
  - log
  - codeless
---
### Log rotation

Log rotation means **periodically closing the current log file and creating a new one**.

For example:

```text
app.log
```

After rotation:

```text
app.log        ← new logs
app.log.1      ← previous logs
app.log.2      ← older logs
app.log.3      ← even older
```

Usually you rotate based on:

- **Size** — rotate when `app.log` reaches 100 MB
    
- **Time** — rotate every day
    
- **Both** — every day or when it reaches a certain size
    

### Why do it?

Without rotation, one log file could become enormous:

```text
app.log
  ↓
  500 MB
  ↓
  5 GB
  ↓
  50 GB 😨
```

Rotation keeps logs manageable and allows you to delete/archive old logs.

---

### What makes logs readable by OpenSearch?

That's a different concept: **structured logging**.

For example, instead of:

```text
User reyhan logged in successfully
```

you might write JSON:

```json
{
  "timestamp": "2026-09-11T10:30:00Z",
  "level": "INFO",
  "message": "User logged in successfully",
  "user": "reyhan"
}
```

OpenSearch can easily parse fields such as:

```text
level = INFO
user = reyhan
timestamp = ...
```

So the distinction is:

```text
Structured logging
        ↓
makes logs easy for OpenSearch to parse/search

Log rotation
        ↓
keeps log files from becoming huge
```

If someone said **"rotate the logs so OpenSearch can read them"**, they may actually be talking about **log rotation + a log shipper/collector** (such as Fluent Bit/Filebeat) rather than rotation itself.


---
[[Back-End]]
[[My-Journey-In-Codeless]]