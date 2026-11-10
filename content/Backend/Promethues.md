---
title:
publish: true
date created: 2026-11-09
tags:
  - backend
---
Prometheus is an open-source monitoring and metrics collection system. In simple words, it continuously collects numerical information about your servers, databases, and applications so you can understand how they are performing.

Since you're setting up Grafana to monitor PostgreSQL, let's look at how it fits into your setup.

## 1. What does Prometheus do?

Imagine you have a PostgreSQL database. You want to know:

- How much CPU is PostgreSQL using?
    
- How much RAM is being consumed?
    
- How many database connections are active?
    
- How many queries are running?
    
- Is the database available?
    
- Is disk usage increasing?
    

Prometheus collects and stores these measurements over time.

For example:

Example metrics collected by Prometheus

# 75%

CPU usage

# 62%

RAM usage

# 24

Active connections

# UP

Database status

Illustrative metrics, not live readings from your database.

## 2. How does Prometheus work with Grafana?

They have different responsibilities:

|Component|Responsibility|
|---|---|
|Prometheus|Collects and stores metrics|
|Grafana|Displays metrics in dashboards and graphs|
|Exporter|Exposes metrics from a system or database|
|Alloy|Collects and forwards telemetry data|

Think of it this way:

- Exporter: Provides the information.
    
- Prometheus: Collects and stores the information.
    
- Grafana: Shows you the information visually.
    

## 3. How they work together in your setup

[Prometheus Node Exporter ve Postgres Exporter Kurulumu | by Cihat Küçükbağrıaçık | Medium](https://images.openai.com/static-rsc-4/g0Ax4GGjgYA4Y2FiaTtSWk9licJynPmKPoN11_NLdAPK24tgo4TQ3dLTedb-hqXBRkSQIVzXGyyNjLWWu4gGwHV8ZNTdZwc7wrX1ND-6Zk_Y1G7E5Ot6NJixcuvU1x0kVtddQiUwKh06HWwbaouOH1PtkZa-n6iqi0Xb3gZl-bM?purpose=inline)

[cihadkba.medium.com](https://cihadkba.medium.com/prometheus-node-exporter-ve-postgres-exporter-kurulumu-4e6d7f96d57b?utm_source=chatgpt.com)

Your current architecture is approximately:

```
         PostgreSQL Database
                 |
          +------+------+
          |             |
     postgres       node-exporter
     exporter       (system metrics)
          |             |
          +------+------+
                 |
              Alloy
                 |
            Prometheus
                 |
              Grafana
                 |
          Monitoring Dashboard
```

One important detail: your actual Alloy configuration determines which metrics are collected and where they are sent. Prometheus can also scrape exporters directly without Alloy.

## 4. What happens when your database goes down?

For example, imagine you stop PostgreSQL:

```
sudo systemctl stop postgresql
```

Your monitoring setup can detect this:

1. The PostgreSQL exporter cannot connect to PostgreSQL.
    
2. It reports that the database is unavailable.
    
3. Prometheus records the availability metric.
    
4. Grafana displays the database as DOWN (if configured to visualize that metric).
    

You can also configure alerts to notify you when this happens.

## 5. Why do you need both Prometheus and Grafana?

You don't necessarily need both, but they complement each other.

- Prometheus is primarily a metrics collection and time-series storage system.
    
- Grafana is primarily a visualization and dashboard platform.
    

Grafana doesn't normally collect and store all those metrics itself. It queries Prometheus to retrieve them.

The most important thing to remember:

Prometheus is the data collector and storage system; Grafana is the visual interface that helps you understand that data.

For your database-support agent project, this combination is useful because your agent could eventually query monitoring metrics to investigate problems such as high CPU usage, connection exhaustion, or database downtime.


---
[[Backend]]