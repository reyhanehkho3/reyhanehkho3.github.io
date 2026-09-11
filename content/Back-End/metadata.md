---
title: metadata
publish: true
date created: 2026-09-11
tags:
  - Backend
  - codeless
---
**Metadata** means **data about other data**.

It's extra information that describes something, rather than being the main content itself.

### Simple example

Suppose you have a photo:

```text
Photo = the actual data
```

Its metadata could be:

```text
filename: vacation.jpg
size: 3.2 MB
type: image/jpeg
created_at: 2026-09-11
width: 1920
height: 1080
```

The photo is the main data. The information **about the photo** is metadata.

---

## In your backend

Suppose you have an audit log:

```json
{
  "action": "UPDATE_USER_ROLE",
  "resource_id": 87,
  "metadata": {
    "oldRole": "USER",
    "newRole": "ADMIN"
  }
}
```

Here:

```text
action       → what happened
resource_id  → what was affected
metadata     → additional details about what happened
```

The metadata gives you information that isn't worth creating a separate column for every possible detail.

For example, another audit event could have:

```json
{
  "action": "CHANGE_TASK_STATUS",
  "resource_id": 15,
  "metadata": {
    "oldStatus": "TODO",
    "newStatus": "DONE"
  }
}
```

Different actions can have different metadata.

---

## Metadata appears everywhere

### HTTP

A response:

```http
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 1500
```

The actual response body is the data:

```json
{
  "name": "Reyhan"
}
```

While headers provide **metadata about the response**:

```text
Content-Type
Content-Length
Cache-Control
```

---

### Database

A database record:

```text
User:
    id: 42
    username: reyhan
```

Metadata might include:

```text
created_at
updated_at
created_by
```

These describe the record rather than being the core user information.

---

### Logs

```json
{
  "level": "ERROR",
  "message": "Database connection failed",
  "metadata": {
    "service": "user-service",
    "requestId": "abc123",
    "database": "postgres",
    "retryCount": 3
  }
}
```

The main data is:

```text
"Database connection failed"
```

The metadata tells you **where, when, and in what context** it happened.

---

### The easiest definition

> **Data = the thing.**  
> **Metadata = information about the thing.**

For example:

```text
Book
├── Data: the actual text of the book
└── Metadata:
    ├── title
    ├── author
    ├── publication date
    ├── page count
    └── ISBN
```

This concept is useful throughout backend development because you'll see **metadata in HTTP, databases, APIs, logs, files, authentication tokens, and audit logs**.

---
[[Back-End]]
[[My-Journey-In-Codeless]]