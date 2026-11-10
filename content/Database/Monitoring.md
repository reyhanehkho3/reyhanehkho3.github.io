---
title: Monitoring
publish: true
date created: 2026-11-10
tags:
  - database
  - dba-agent
---
Monitoring is about continuously observing database health.

This is especially relevant when you're using Grafana and Prometheus.

Here are some important metrics:

|Metric|What it tells you|
|---|---|
|CPU usage|How much CPU the database workload consumes|
|Memory usage|Memory consumption|
|Disk usage|How much storage is occupied|
|Connections|Number of active database connections|
|Transactions per second|Database workload|
|Cache hit ratio|How often requested data is served from cache|
|Query duration|How long queries take|
|Deadlocks|Number of deadlock events|
|Replication lag|How far a replica is behind|
|Database availability|Whether the database can be reached|

For example, imagine your Grafana dashboard shows:

Example PostgreSQL monitoring dashboard

## CPU usage:

# 95% 

High

## Connections:

# 85 / 100

 Warning

## Cache hit ratio:

# 98.5%

Healthy

## Deadlocks:

# 3

Investigate



Monitoring tools:

- Prometheus
    
- Grafana
    
- Grafana Alloy
    
- pg_stat_statements
    

An important distinction:

Monitoring tells you something is wrong. Diagnosis tells you why it's wrong.

For example, Prometheus might detect that CPU usage is 100%, but you need to investigate which queries, transactions, or processes are responsible.

---
[[Database]]