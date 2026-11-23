---
title: PRD
publish: true
date created: 2026-11-22
tags:
  - product
---
**PRD** stands for **Product Requirements Document**.

It's a document that describes **what a product should do, why we're building it, and what requirements it must satisfy.**

Think of it as a blueprint for building a product. Before developers start implementing features, they should understand what they're building and what problem they're solving.

## **1. What does a PRD contain?**

A typical PRD includes these sections:

|Section|Description|
|---|---|
|**1. Overview**|What is the product?|
|**2. Problem Statement**|What problem are we trying to solve?|
|**3. Goals & Objectives**|What do we want to achieve?|
|**4. Target Users**|Who will use this product?|
|**5. Features**|What should the product do?|
|**6. Functional Requirements**|How should each feature behave?|
|**7. Non-Functional Requirements**|Performance, security, scalability, etc.|
|**8. User Stories**|What do users want to accomplish?|
|**9. Acceptance Criteria**|How do we know a feature is correctly implemented?|
|**10. Constraints & Assumptions**|What limitations or assumptions exist?|

## **2. A practical example**

Imagine we're building a **Database Monitoring Agent**.

A simplified PRD might look like this:

**Product:** AI Database Monitoring Agent

**Problem Statement:**

Database administrators need to continuously monitor databases and manually investigate performance issues. This process is time-consuming.

**Goal:**

Build an AI agent that monitors PostgreSQL databases, detects problems, and helps identify their root causes.

**Functional Requirements:**

1. Connect to a PostgreSQL database.
    
2. Collect database metrics.
    
3. Detect slow queries.
    
4. Identify potential performance bottlenecks.
    
5. Analyze alerts and suggest possible root causes.
    
6. Generate optimization recommendations.
    

**Non-Functional Requirements:**

- Must support self-hosted deployment.
    
- Must work without an internet connection for database monitoring.
    
- Must protect database credentials.
    
- Must not execute destructive SQL without authorization.
    

**Acceptance Criteria:**

For example:

- When PostgreSQL becomes unavailable, the monitoring system must detect it.
    
- When a slow query exceeds the configured threshold, an alert must be generated.
    
- The agent must provide an explanation of the detected issue.
    

## **3. PRD vs. Technical Design Document (TDD)**

These two documents are related but have different purposes.

|PRD|Technical Design Document|
|---|---|
|Describes WHAT to build|Describes HOW to build it|
|Focuses on product requirements|Focuses on technical architecture|
|Defines features and behavior|Defines components and interactions|
|Usually written before implementation|Usually follows requirements analysis|

For example:

- **PRD:** The system must detect slow database queries.
    
- **TDD:** Use PostgreSQL `pg_stat_activity`, Prometheus metrics, and Grafana alerts to detect slow queries.
    

## **4. Where does PRD fit in the development process?**

**PRD**

What and why should we build?

**Technical Design (TDD)**

How should we build it?

**Tasks & Implementation Plan**

What steps should developers take?

**Development & Testing**

Build, test, and validate.

**One important point:** A PRD should focus on requirements, not prematurely decide the technical implementation.

For example, don't immediately write "We must use LangGraph." Instead, write "The system must support multi-step agent workflows with controlled database access."

This keeps product requirements independent of technology choices.

---
[[Product]]