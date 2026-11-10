---
title: Alloy
publish: true
date created: 2026-11-09
tags:
  - backend
---
Grafana Alloy is an observability collector. Its job is to collect monitoring data from different sources and send that data to systems such as Prometheus, Loki, and Tempo.

In simple words:

- Exporter: Exposes information about a system.
    
- Alloy: Collects and forwards that information.
    
- Prometheus: Stores metrics.
    
- Grafana: Visualizes metrics.
    

## 1. What exactly does Alloy do?

Imagine you have PostgreSQL running on Ubuntu.

You want to monitor both PostgreSQL and your Ubuntu server.

Alloy can collect information from different sources:

- PostgreSQL exporter: Database connections, transactions, cache statistics, etc.
    
- Node Exporter: CPU, RAM, disk, network usage.
    
- Application metrics: Metrics exposed by your applications.
    

It can then forward those metrics to Prometheus.

## 2. How Alloy fits into your architecture

[Grafana Alloy | OpenTelemetry Collector distribution](https://images.openai.com/static-rsc-4/mhn3MlakS03sOrDEmM99m-pOXIULSP-5H2H4WldtccBqk4RKXDJ4cGbahno4SFhxz8g4Kdcb3zH1OAxkVAmKY2-NR4tri_zOIoGdhZ1X_fKW0mYqsuxWA_Yt5nVfTdWT-j4O0jBFjPF7OayIK-JbFVpwxvOSSesrYcaB9UnhWw0?purpose=inline)

[grafana.com](https://grafana.com/oss/alloy-opentelemetry-collector/?utm_source=chatgpt.com)

Your architecture looks approximately like this:

```
       PostgreSQL              Ubuntu Server
            |                       |
     PostgreSQL exporter       Node Exporter
            |                       |
            +-----------+-----------+
                        |
                      Alloy
                        |
                   Prometheus
                        |
                     Grafana
                        |
                 Monitoring UI
```

## 3. Is Alloy the same as Prometheus?

No. They have different responsibilities.

|Feature|Alloy|Prometheus|
|---|---|---|
|Collect metrics|Yes|Yes|
|Store time-series metrics|No|Yes|
|Forward metrics|Yes|Yes|
|Collect logs|Yes|No, not natively|
|Collect traces|Yes|No|
|Visualize dashboards|No|No|
|Alerting|Can participate in pipelines|Yes|

One important distinction: Prometheus can scrape exporters directly. Alloy is not mandatory.

## 4. Why are you using Alloy instead of connecting everything directly to Prometheus?

Alloy gives you a centralized collection layer.

For example, suppose later you want to monitor:

- PostgreSQL
    
- MySQL
    
- Redis
    
- Ubuntu server resources
    
- Your database-support agent
    

Instead of configuring every monitoring source independently in multiple systems, Alloy can collect and route telemetry from different sources.

It also supports processing, filtering, relabeling, and forwarding telemetry.

## 5. What does each component do in your current Docker setup?

Based on your monitoring project:

|Container|Purpose|
|---|---|
|`monitoring-alloy`|Collects and forwards metrics|
|`monitoring-prometheus`|Stores metrics|
|`monitoring-grafana`|Displays dashboards|
|`monitoring-node-exporter`|Exposes Ubuntu system metrics|

And your PostgreSQL exporter configuration inside Alloy collects PostgreSQL metrics.

My recommendation for your database-support agent:

Keep all four components for now.

Eventually, your agent could query Prometheus to answer questions such as:

- Why did CPU usage reach 100%?
    
- When did PostgreSQL become unavailable?
    
- How many active connections did we have before the slowdown?
    
- Was memory usage increasing before the database crashed?
    

This is where monitoring becomes particularly useful: your agent can use historical metrics to investigate the root cause instead of just reporting that something went wrong.


---
[[Backend]]