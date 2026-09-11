---
title: Payload
publish: true
date created: 2026-09-11
tags:
  - Backend
  - codeless
---
**Payload** means the **actual data being carried inside a message/request/response**.

The word comes from transportation:

```text
Truck
 └── Payload = the actual goods being transported
```

In software:

```text
HTTP Request
 ├── Headers (metadata)
 └── Payload (actual data)
```

---

## Example: HTTP request

Imagine creating a user:

```http
POST /api/users
```

Headers:

```http
Authorization: Bearer abc123
Content-Type: application/json
```

Payload (body):

```json
{
  "username": "reyhan",
  "email": "reyhan@example.com",
  "password": "123456"
}
```

The payload is the information you actually want to send.

---

## Payload vs Headers

### Headers

Metadata about the request:

```http
Content-Type: application/json
Authorization: Bearer token
Accept: application/json
```

Meaning:

> "How should this request be handled?"

---

### Payload

The content:

```json
{
  "title": "Learn APIs",
  "status": "TODO"
}
```

Meaning:

> "What data am I sending?"

---

## Example: Response payload

Backend response:

```http
200 OK
```

Response payload:

```json
{
  "id": 15,
  "name": "Task 1",
  "status": "DONE"
}
```

The frontend receives this payload and displays it.

---

## Payload in JWT

You may also hear about a JWT payload.

A JWT has three parts:

```text
JWT
 |
 ├── Header
 ├── Payload
 └── Signature
```

Example payload:

```json
{
  "userId": 123,
  "role": "ADMIN",
  "exp": 1750000000
}
```

This contains **claims** about the user.

Important:

- JWT payload is **encoded**, not encrypted.
    
- Don't put secrets like passwords inside it.
    

---

## Payload in messaging systems

Example with RabbitMQ:

```text
Message
 ├── Metadata
 │     └── timestamp, routing key
 │
 └── Payload
       └── "Send email to user 123"
```

---

### Simple definition:

> **Payload = the meaningful data being transported, not the information about the transport.**

A good mental shortcut:

- **Headers = information about the message**
    
- **Payload = the message itself**

---
[[Back-End]]
[[My-Journey-In-Codeless]]