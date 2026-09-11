---
title: MCP Inspector
publish:
date created: 2026-09-11
tags:
  - MCP
  - Agent
  - codeless
---
**MCP Inspector** is a **developer tool for testing and debugging MCP (Model Context Protocol) servers**.

Think of it like **Postman, but for MCP servers**.

```text
Postman
   ↓
Test HTTP APIs

MCP Inspector
   ↓
Test MCP servers
```

### What can you do with it?

Suppose you built an MCP server with tools:

```text
My MCP Server
├── get_weather
├── search_files
├── create_task
└── send_email
```

MCP Inspector lets you connect to that server and inspect/test things like:

- 🔧 **Tools** — what tools the server exposes
    
- 📋 **Tool inputs** — what arguments a tool expects
    
- 📤 **Tool results** — what the tool returns
    
- 📚 **Resources** — resources exposed by the server
    
- 💬 **Prompts** — prompts exposed by the server
    
- 🔌 **Connection/protocol behavior**
    
- ❌ Errors and debugging information
    

### Example

Imagine your MCP tool is:

```text
calculate_sum
```

with:

```json
{
  "a": 10,
  "b": 20
}
```

You can use Inspector to call it manually:

```text
Tool: calculate_sum

a: 10
b: 20

        ↓

Result: 30
```

This is useful because you can verify that **your MCP server works correctly before connecting it to Claude, Cursor, OpenCode, etc.**

### Mental model

```text
             MCP Inspector
                  │
                  ↓
          ┌───────────────┐
          │   MCP Server  │
          ├───────────────┤
          │ Tools         │
          │ Resources     │
          │ Prompts       │
          └───────────────┘
```

So if you're developing an MCP server, **Inspector is basically a debugging/testing UI for the MCP protocol**.


---
[[MCP]]
[[Agent]]
[[My-Journey-In-Codeless]]