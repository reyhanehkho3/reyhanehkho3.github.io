---
title: Open Search
publish: true
date created: 2026-09-11
tags:
  - Backend
  - log
  - codeless
---
**OpenSearch** is a system for **storing, searching, and analyzing large amounts of data**, especially logs.

Think of it as a **search engine + database for logs and events**.

### Simple example

Your backend produces:

```json
{
  "level": "ERROR",
  "message": "Database connection failed",
  "service": "auth",
  "timestamp": "2026-09-11T10:30:00Z"
}
```

You send these logs to OpenSearch.

Then you can search:

```text
level: ERROR
```

or:

```text
service: auth AND level: ERROR
```

and quickly find all matching logs.

### Typical architecture

```text
Your application
      │
      │ logs
      ▼
Log collector
(Fluent Bit, Filebeat, etc.)
      │
      ▼
OpenSearch
      │
      ▼
OpenSearch Dashboards
```

**OpenSearch** stores and indexes the data.

**OpenSearch Dashboards** gives you a UI where you can search and visualize it:

```text
Errors today:       152
Failed logins:       43
Slow requests:       27
```

### Why not just use log files?

With a normal file:

```text
app.log
```

you might have millions of lines and searching/analyzing them becomes inconvenient.

OpenSearch **indexes** the data, so queries like:

```text
Find all ERROR logs
Find errors from the auth service
Find requests slower than 2 seconds
Find all errors between 10:00 and 11:00
```

can be performed efficiently.

### In your previous question

When someone talks about:

> "rotate the logs so they're readable by OpenSearch"

there are actually several separate pieces:

```text
Application
   ↓
Structured JSON logs
   ↓
Log rotation
   ↓
Log collector
   ↓
OpenSearch
   ↓
Dashboard
```

**Rotation** manages log files.  
**JSON/structured logging** makes the log data machine-readable.  
**The collector** sends logs to OpenSearch.  
**OpenSearch** stores/indexes/searches them.


---
[[Back-End]]
[[My-Journey-In-Codeless]]