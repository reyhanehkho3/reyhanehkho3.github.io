---
title: OpenTelemetry
publish: true
date created: 2026-09-11
tags:
  - Backend
---
**OpenTelemetry (OTel)** is a standard/toolset for **observability**. It helps your application collect **traces, metrics, and logs** and send them to monitoring systems.

It's a collector for traces.

Think of it as the **instrumentation layer** between your application and observability tools.

```text
Your application
      │
      │ OpenTelemetry
      ▼
┌─────────────────┐
│ Traces           │
│ Metrics          │
│ Logs             │
└─────────────────┘
      │
      ▼
Observability system
(OpenSearch, Jaeger, Grafana, etc.)
```

### For your tracing example

Suppose:

```text
POST /orders
```

OpenTelemetry can automatically create a trace:

```text
Trace ID: abc123

POST /orders
   │
   ├── authenticate user
   │
   ├── create order
   │     └── PostgreSQL query
   │
   ├── call payment API
   │
   └── publish notification
```

Each operation can become a **span**:

```text
Trace abc123
│
├── HTTP POST /orders       ← span
├── PostgreSQL INSERT       ← span
├── Payment API request     ← span
└── RabbitMQ publish        ← span
```

The important part is that OpenTelemetry can **propagate the trace context** between these operations/services, so you can connect them back to the original request.

### Why use it?

Without tracing, you might have:

```text
ERROR payment failed
ERROR database timeout
INFO order created
```

and wonder:

> "Are these related?"

With OpenTelemetry:

```text
trace_id = abc123
```

you can see that all those operations belong to the same request.

### OpenTelemetry vs OpenSearch

They are **not the same thing**:

|OpenTelemetry|OpenSearch|
|---|---|
|Collects/instruments telemetry|Stores and searches data|
|Creates traces/spans|Indexes data|
|Collects metrics|Lets you query/analyze it|
|Can collect logs|Provides dashboards|
|Sends data elsewhere|Receives/stores data|

So a typical setup could be:

```text
Express application
       │
       ▼
 OpenTelemetry
       │
       ▼
Telemetry Collector
       │
       ├──► OpenSearch
       ├──► Prometheus
       └──► Jaeger
```

**Mental model:**

> **OpenTelemetry = "How do I observe what my application is doing?"**  
> **OpenSearch = "Where do I store/search/analyze that information?"**


---
[[Back-End]]