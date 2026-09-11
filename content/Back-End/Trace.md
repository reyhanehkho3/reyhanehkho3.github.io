---
title: Trace
publish: true
date created: 2026-08-27
tags:
  - codeless
  - Backend
---
## Trace — in Monitoring

**Definition:** A trace represents the **journey of one request through a system**, especially when it passes through multiple services.  
It lets you see which operations happened, how long they took, and where a problem occurred.

**Examples:**

1. `User → API → Payment Service → Bank → Database`.
2. A page takes 5 seconds, and the trace shows the database query took 4.5 seconds.
3. An order fails in the Payment Service, and the trace identifies exactly where it failed.

## **trace / tracing** in **observability**.

A **trace** follows one request through the whole system.

### Simple example

A user sends:

```text
POST /orders
```

The backend gives that request a unique **trace ID**:

```text
trace_id = abc123
```

Then everything caused by that request carries the same trace ID:

```text
Request
  │
  ├── Controller
  │      trace_id = abc123
  │
  ├── Service
  │      trace_id = abc123
  │
  ├── Database query
  │      trace_id = abc123
  │
  ├── Call payment service
  │      trace_id = abc123
  │
  └── Send notification
         trace_id = abc123
```

So later you can say:

> "Show me everything that happened during request `abc123`."

### Trace vs log

A **log** is an individual event:

```text
ERROR Payment service failed
```

A **trace** connects many events together:

```text
Request abc123
    ↓
Auth
    ↓
Create order
    ↓
Database
    ↓
Payment API
    ↓
Error
```

### What are callbacks?

If your request triggers asynchronous work, you generally want that work to remain associated with the original operation where appropriate.

For example:

```text
HTTP Request
    │ trace_id=abc123
    ▼
Create Order
    │
    ├── DB query
    │
    └── Queue message
          │
          ▼
       Worker
          │ trace/context propagated
          ▼
       Send Email
```

This lets you investigate **the entire chain**, rather than seeing unrelated logs from different requests.

### One important terminology detail

A **trace** usually contains multiple **spans**:

```text
Trace: abc123
│
├── Span: HTTP request
├── Span: database query
├── Span: payment API call
└── Span: email operation
```

So:

- **Trace** = the whole journey of one request/operation.
    
- **Span** = one operation within that journey.
    
- **Trace ID** = identifier connecting the spans.
    
- **Tracing** = the practice of recording and following this journey.
    

This is commonly implemented with **OpenTelemetry** and is one of the three major observability signals:

**Logs + Metrics + Traces**.



---
[[My-Journey-In-Codeless]]
[[Back-End]]