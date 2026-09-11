---
title: Prometheus
publish: true
date created: 2026-09-11
tags:
  - Backend
  - codeless
---
**Prometheus** is a system for **collecting and storing metrics** from your applications and infrastructure.

The easiest mental model:

> **Prometheus = a database + monitoring system for numbers over time.**

### Example

Your backend might expose metrics like:

```text
http_requests_total 152340
http_errors_total 342
http_request_duration_seconds 0.18
active_users 57
```

Prometheus periodically collects these metrics and stores them.

```text
Your application
      │
      │ metrics
      ▼
  Prometheus
      │
      │ query
      ▼
   Grafana
      │
      ▼
   Dashboard
```

### What is a metric?

A **metric** is a measurable number.

For example:

```text
CPU usage        → 72%
Memory usage     → 4.2 GB
Requests         → 850/sec
Errors           → 12/sec
Response time    → 180 ms
```

Prometheus is particularly good at storing these **time-series data**:

```text
10:00 → 120 requests/sec
10:01 → 145 requests/sec
10:02 → 190 requests/sec
10:03 → 850 requests/sec  ← something happened
```

### Prometheus + Grafana

They're often used together:

```text
              Application
                   │
                   │ metrics
                   ▼
              Prometheus
                   │
                   │ PromQL
                   ▼
                Grafana
                   │
                   ▼
              📊 Dashboard
```

**Prometheus** stores and queries the metrics.

**Grafana** displays them nicely.

For example, Grafana might ask Prometheus:

```text
"What was the HTTP error rate during the last hour?"
```

using **PromQL** (Prometheus Query Language).

### Prometheus vs OpenSearch

This distinction is important:

|                       | Prometheus  | OpenSearch                      |
| --------------------- | ----------- | ------------------------------- |
| Main data             | Metrics     | Logs / searchable events        |
| Example               | `CPU = 72%` | `"Database connection failed"`  |
| Data type             | Time series | Documents                       |
| Query                 | PromQL      | OpenSearch query                |
| Typical visualization | Grafana     | OpenSearch Dashboards / Grafana |

So your monitoring stack could look like:

```text
                    Application
                         │
                 OpenTelemetry
                         │
          ┌──────────────┼──────────────┐
          ▼              ▼              ▼
        Logs          Metrics         Traces
          │              │              │
          ▼              ▼              ▼
     OpenSearch      Prometheus      Tempo/Jaeger
          │              │              │
          └──────────────┼──────────────┘
                         ▼
                      Grafana
```

**Mental shortcut:**

- **Prometheus** → "How many? How fast? How often?"
    
- **OpenSearch** → "What happened?"
    
- **Tracing** → "What happened during this particular request?"
    
- **Grafana** → "Show me all of this."


---
[[Back-End]]
[[My-Journey-In-Codeless]]