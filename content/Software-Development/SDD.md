---
title: SDD
publish: true
date created: 2026-08-23
tags:
  - software-development
  - codeless
---
**SDD (Service-Oriented Development)** is a **software architecture and design strategy** used to build massive, scalable enterprise systems.

However, **SDD** is a less common acronym today. In modern software, it is almost always referred to as **SOA (Service-Oriented Architecture)**

### SDD / SOA (Service-Oriented Development/Architecture): "Building with LEGOs"

**SDD (Service-Oriented Development)** is not about how you _write_ a single function; it is about how you _structure_ an entire enterprise software system.

Instead of building one giant, monolithic application (a single massive block of code), SDD breaks the system down into a collection of small, independent, and loosely coupled **"services."** Each service does one specific business job (e.g., "Processing Payments," "Sending Emails," or "Managing User Logins").

These services communicate with each other over a network (using APIs) to form the complete application.

**Why do companies use SDD/SOA?**

- **Scalability:** If the "Payment" service gets too busy, you can upgrade just that one service without touching the rest of the system.
    
- **Reusability:** The "User Login" service can be built once and reused by the company's website, mobile app, and internal admin panel simultaneously.
    
- **Team independence:** One team can work on the "Shipping" service, while another team works on the "Inventory" service, without stepping on each other's toes.
    

_(Note: Today, this concept has evolved into **Microservices**, which is essentially a more modern, lightweight version of SDD/SOA)._


---
[[Software-Development]]
[[My-Journey-In-Codeless]]