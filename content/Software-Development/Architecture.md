---
title: Architecture
publish: true
date created: 2026-08-12
tags:
  - "#software-development"
---
**Architecture** means the components, the responsibility of each component, the communication between them, and the decisions that shape the system's flexibility.

**Typical path of a web request:**
Client → DNS/CDN/LB → Web/API → Auth → Validation → Business Logic → Response
And on the backend: DB/Cache/Queue

In a large system, the path may also include a search engine, object storage, event bus, workers, and external services.

**Example responsibility boundaries:**
- **Controller/Handler:** receives the request and builds the response
- **Service / Use Case:** contains the business logic
- **Repository / Data Access:** handles access to persistence (database, etc.)
- **Domain Model:** defines the core rules and concepts of the business domain
- **Infrastructure:** covers databases, queues, network, and external providers

**The key principle is Separation of Concerns:** changing the UI should not break payment logic; changing the database should not contaminate the entire system. Good architecture makes dependencies understandable and limits the impact of changes to specific localized areas.

**To analyze a real project, trace a specific request end-to-end:** handler → middleware → route → service → repository → schema/migration → response → test. Folder structure alone is not architecture; the runtime flow is much more important.