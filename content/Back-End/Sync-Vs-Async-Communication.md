---
title: Sync vs async communication
publish: true
date created: 2026-09-05
tags:
  - codeless
  - Backend
---
### Sync vs Async Communication

This describes **whether the sender has to wait for the receiver to respond before continuing**.

### 1. Synchronous (Sync)

The sender **waits for a response** before continuing.

**Mental model:** 📞 Phone call

```text
Client ── request ──> Server
Client <── response ── Server
        ↓
   continue working
```

Example:

```text
Frontend → GET /users → Backend
Frontend ← user data ← Backend
```

The frontend waits for the response before it can use that data.

**Common examples:**

- REST API request/response
    
- Database query
    
- Function call
    

---

### 2. Asynchronous (Async)

The sender **doesn't have to wait**. It can continue doing other work while the operation happens.

**Mental model:** 📧 Email

```text
Client ── message ──> Server
   ↓
continue working

          ...later...

Server ── result/event ──> Client
```

Example:

```text
User uploads a video
        ↓
Backend puts job in RabbitMQ
        ↓
Backend immediately says "Upload accepted"
        ↓
Worker processes video in background
        ↓
Worker sends notification when finished
```

The user doesn't have to keep waiting for the video processing to finish.

---

### Quick comparison

| |Sync|Async|
|---|---|---|
|Sender waits?|✅ Yes|❌ No|
|Response|Usually immediate|May come later|
|Good for|Simple request/response|Long-running/background work|
|Example|REST API|RabbitMQ job|
|Mental model|Phone call|Email|

### Important distinction

**Async doesn't necessarily mean "no response."**  
It means the sender **doesn't block while waiting for the response**.

For example:

```text
Frontend → POST /video
Frontend ← 202 Accepted
```

The backend can process the video later and eventually notify the frontend through a WebSocket, SSE, email, polling, etc.

So in a typical application you might use **both**:

```text
REST → synchronous request/response
RabbitMQ → asynchronous background processing
WebSocket → asynchronous real-time notification
```
---
[[Back-End]]
[[My-Journey-In-Codeless]]