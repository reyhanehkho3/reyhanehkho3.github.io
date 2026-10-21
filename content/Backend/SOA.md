---
title: SOA
publish: true
date created: 2026-10-20
tags:
  - backend
  - architecture
---
# What is SOA?

SOA stands for Service-Oriented Architecture.

It is a software architecture approach where an application is built from separate, reusable services that communicate with each other over a network.

Think of each service as a specialist responsible for a particular job.

## 1. Simple real-world example

Imagine an online shopping application.

Online Shopping Application

A user places an order

Order Service

Manages orders

Payment Service

Processes payments

Inventory Service

Tracks product stock

Notification Service

Sends emails or SMS

Each service has its own responsibility and can communicate with the others.

For example, when a customer places an order:

1. The Order Service creates the order.
    
2. The Payment Service processes the payment.
    
3. The Inventory Service updates the stock.
    
4. The Notification Service sends a confirmation.
    

Each service focuses on its own job instead of putting all the business logic into one place.

## 2. How do services communicate?

Services need a way to exchange information. Common approaches include:

- REST APIs: One service sends an HTTP request to another.
    
- SOAP: Services exchange structured XML messages using the SOAP protocol.
    
- Message queues: Services communicate asynchronously through tools such as RabbitMQ.
    

For example:

```
Order Service
     |
     | HTTP request
     v
Payment Service
     |
     | Payment result
     v
Order Service
```

SOA is the overall architectural approach, not a specific communication protocol.

## 3. SOA vs. monolith vs. microservices

These three concepts are related, but they are not the same.

|Feature|Monolith|SOA|Microservices|
|---|---|---|---|
|Structure|One application|Separate services|Small, independent services|
|Communication|Mostly internal function calls|Often network-based|Often network-based|
|Reuse|Usually within the application|Strong emphasis on reusable services|Usually focused on specific business capabilities|
|Deployment|Usually together|Depends on the architecture|Independently deployable|
|Typical infrastructure|Simpler|May use enterprise service infrastructure|Often uses lightweight APIs and messaging|

Important: SOA and microservices overlap. The distinction is not absolute. Traditional SOA often emphasizes enterprise-wide service reuse and centralized integration, while microservices emphasize smaller services, independent deployment, and team autonomy.

## 4. What is the difference between SOA and an API?

An API is an interface that lets software communicate with another piece of software.

SOA is an architectural approach that organizes software around services.

For example, a Payment Service might expose a REST API:

```
POST /payments
```

Another service can call that API to request a payment.

- SOA describes how the system is organized around services.
    
- API describes how a service can be accessed.
    
- REST describes a style for designing network APIs.
    
- SOAP is a protocol for exchanging structured messages.
    

These concepts can be used together.

## 5. When should you use SOA?

SOA can be useful when:

- Multiple applications need to share the same business capabilities.
    
- An organization has many different systems that must work together.
    
- Services need clear responsibilities and well-defined interfaces.
    
- Business functionality should be reused across multiple applications.
    

However, SOA can introduce network failures, integration complexity, security concerns, and operational overhead. A small application may be better served by a well-structured monolith.

Remember it this way: SOA means organizing software around services that provide specific capabilities and communicate through defined interfaces.


---
[[Backend]]
