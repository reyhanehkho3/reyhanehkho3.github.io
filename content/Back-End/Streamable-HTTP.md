---
title: Streamable HTTP
publish:
date created: 2026-09-11
tags:
  - Backend
  - codeless
---
**Streamable HTTP** is a way for a client and server to communicate over **HTTP while allowing the server to send data progressively as it becomes available**.

You’ll especially see this term in the **MCP (Model Context Protocol)** world.

### First: normal HTTP

With a traditional request:

```text
Client ── request ──> Server
Client <─ response ── Server
```

The server processes the request and returns a response.

### Streaming HTTP

With streaming:

```text
Client ── request ──> Server
                 ←── data 1
                 ←── data 2
                 ←── data 3
                 ←── data 4
```

The connection can remain open while the server sends pieces of the response.

For example, an AI server might produce:

```text
"Hello"
"Hello, how"
"Hello, how are"
"Hello, how are you?"
```

instead of waiting until the entire response is finished.

---

## What does "Streamable HTTP" mean in MCP?

MCP originally had different transport approaches, including **stdio** and older HTTP-based approaches.

**Streamable HTTP** is an MCP transport designed for communication between:

```text
MCP Client
    ↕
HTTP
    ↕
MCP Server
```

It allows MCP clients to communicate with a remote MCP server using HTTP and supports **streaming when needed**.

For example:

```text
Claude / OpenCode
       │
       │ HTTP
       ↓
  MCP Server
       │
       ├── tools
       ├── resources
       └── prompts
```

This is particularly useful when the MCP server is **remote**, rather than running as a local process.

### Streamable HTTP vs stdio

| |stdio|Streamable HTTP|
|---|---|---|
|Typical use|Local MCP server|Local or remote|
|Communication|stdin/stdout|HTTP|
|Network-friendly|❌|✅|
|Remote server|Not typical|✅|
|Streaming|Through stdio|Through HTTP|
|Example|Agent launches server process|Agent connects to server URL|

### Simple mental model

Think of:

**stdio**

> "Start this MCP program on my computer and talk to it through stdin/stdout."

**Streamable HTTP**

> "Connect to this MCP server over HTTP and communicate with it, including streaming responses when appropriate."

So when you see **“MCP server using Streamable HTTP”**, think:

> **An MCP server that communicates with clients over HTTP and can stream MCP messages/results instead of requiring everything to be returned as one completed response.**


---
[[My-Journey-In-Codeless]]
[[HTTP-HTTPS-SSL]]
[[Back-End]]