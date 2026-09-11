---
title: Grafana
publish: true
date created: 2026-09-11
tags:
  - Backend
  - codeless
---
**Grafana** is a tool for **visualizing and monitoring your application's data**.

The easiest mental model is:

> **Grafana = a dashboard for your monitoring data.**

### Example

Your application produces metrics:

```text
CPU usage:       72%
Memory usage:    4.2 GB
Requests/sec:    850
Error rate:      2.3%
Response time:   180 ms
```

Grafana can turn these into dashboards:

```text
┌──────────────────────────────────────┐
│        Application Dashboard         │
├──────────────┬──────────────┬────────┤
│ CPU          │ Memory       │ Errors │
│   72%        │   4.2 GB     │  2.3% │
├──────────────┴──────────────┴────────┤
│ Requests/sec                         │
│     /\      /\                       │
│ ___/  \____/  \___                   │
├──────────────────────────────────────┤
│ Response time                        │
│ 120ms ───────── 180ms ─── 250ms      │
└──────────────────────────────────────┘
```

### Grafana doesn't usually collect the data itself

It connects to **data sources**.

For example:

```text
Application
    │
    ├── metrics ──────► Prometheus
    │                      │
    │                      ▼
    │                   Grafana
    │
    ├── logs ─────────► OpenSearch
    │                      │
    │                      ▼
    │                   Grafana
    │
    └── traces ───────► Tempo/Jaeger
                           │
                           ▼
                        Grafana
```

So:

- **OpenTelemetry** → collects/instruments telemetry.
    
- **Prometheus** → commonly stores metrics.
    
- **OpenSearch** → stores/searches logs.
    
- **Jaeger/Tempo** → stores traces.
    
- **Grafana** → visualizes and queries these sources.
    

### Grafana can also do alerts

For example:

```text
IF
error_rate > 5%
FOR
5 minutes

THEN
send alert
```

You could get:

> 🚨 API error rate is above 5%.

### The big picture

For the monitoring concepts you've been asking about:

```text
                 Your Application
                       │
                 OpenTelemetry
                       │
          ┌────────────┼────────────┐
          ▼            ▼            ▼
        Logs        Metrics       Traces
          │            │            │
          ▼            ▼            ▼
     OpenSearch    Prometheus   Tempo/Jaeger
          │            │            │
          └────────────┼────────────┘
                       ▼
                    Grafana
                       │
                       ▼
             Dashboards + Alerts
```

**In one sentence:** Grafana is the **visualization and monitoring interface** where you look at your application's logs, metrics, traces, and alerts.


---
[[Back-End]]
[[My-Journey-In-Codeless]]