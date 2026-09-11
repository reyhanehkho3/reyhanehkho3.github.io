---
title: HTTP SSE
publish:
date created: 2026-09-11
tags:
  - codeless
  - Backend
---
If you mean **HTTP SSE**, it stands for **HTTP Server-Sent Events (SSE)**.

It is a way for a **server to continuously send updates to a client over a normal HTTP connection**.

### Normal HTTP

```text
Client ── request ──> Server
Client <─ response ── Server
       connection ends
```

### SSE

```text
Client ── request ──> Server
Client <──── event 1 ── Server
Client <──── event 2 ── Server
Client <──── event 3 ── Server
Client <──── event 4 ── Server
       connection stays open
```

For example, a live notification system:

```text
Server
  │
  ├── "New message"
  ↓
Browser

  │
  ├── "Someone liked your post"
  ↓
Browser

  │
  ├── "New follower"
  ↓
Browser
```

### SSE vs WebSocket

The important difference is **direction**:

```text
SSE:

Server ──────────> Client
       one-way


WebSocket:

Server <─────────> Client
       two-way
```

With SSE, the **client doesn't send messages back through the SSE connection**. It normally uses regular HTTP requests for that.

### Example SSE endpoint

Server:

```js
app.get("/events", (req, res) => {
  res.setHeader("Content-Type", "text/event-stream");
  res.setHeader("Cache-Control", "no-cache");

  res.write(`data: Hello\n\n`);
});
```

Client:

```js
const events = new EventSource("/events");

events.onmessage = (event) => {
  console.log(event.data);
};
```

### SSE vs Streamable HTTP

They're related, but **not the same thing**.

```text
SSE
└── HTTP mechanism for server → client event streams

Streamable HTTP
└── HTTP transport approach that can support streaming
    and is used by MCP
```

So if you're learning MCP, you may encounter **SSE as an older MCP HTTP transport approach**, while **Streamable HTTP is the newer MCP transport approach**.

**Mental model:**

> **SSE = "Keep an HTTP connection open so the server can push events to me."**  
> **WebSocket = "Keep a connection open so both sides can communicate."**


---
[[Back-End]]
[[HTTP-HTTPS-SSL]]
[[My-Journey-In-Codeless]]