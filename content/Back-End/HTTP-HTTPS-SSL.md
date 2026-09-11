---
title: HTTP/HTTPS/SSL
publish: true
date created: 2026-09-11
tags:
  - protocol
  - Backend
  - codeless
---
### HTTP

**HTTP = HyperText Transfer Protocol**

It's the protocol used for communication between a client and a server.

```text
Browser
   │
   │ HTTP request
   ▼
Server
   │
   │ HTTP response
   ▼
Browser
```

Example:

```text
GET /users
```

The browser asks the server for users, and the server responds.

---

### HTTPS

**HTTPS = HTTP + encryption**

The `S` means **Secure**.

```text
HTTP
  ↓
HTTP + TLS encryption
  ↓
HTTPS
```

So instead of:

```text
GET /login
password=123456
```

being sent in plain text, the communication is encrypted.

You see it in URLs like:

```text
https://example.com
```

---

### SSL

**SSL = Secure Sockets Layer**

SSL was the older technology used to secure network communication.

Today, **TLS (Transport Layer Security)** is used instead. People still commonly say "SSL" even when they actually mean TLS.

So technically:

```text
HTTPS
  ↓
HTTP
  +
TLS
```

### The easiest mental model

Think of sending a letter:

```text
HTTP
📄 ───────────────→ Server
   readable letter


HTTPS
🔒📄 ─────────────→ Server
    locked/encrypted letter
```

|Term|What it is|
|---|---|
|**HTTP**|Protocol for communicating over the web|
|**HTTPS**|HTTP secured with TLS|
|**SSL**|Older security technology; replaced by TLS|
|**TLS**|Modern encryption/security protocol used by HTTPS|

So when you see **HTTPS**, think:

> **"HTTP communication, but protected by TLS encryption."**


---
[[Back-End]]
[[My-Journey-In-Codeless]]