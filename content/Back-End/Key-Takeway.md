---
title: Key Takeway
publish: true
date created: 2026-09-05
tags:
  - codeless
  - Backend
  - AI
---
### Key takeaway

When you ask an AI agent to add a new endpoint, **don't just tell it what endpoint to create; tell it what it is allowed to change and what it must not change**.

For example:

> **Task:** Add `POST /users`.  
> **Boundaries:** Only modify the User module, controller, service, repository, routes, and related tests. Do not change the database schema, authentication system, existing endpoints, or project architecture. Reuse the existing validation and error-handling patterns.

This is important because modern coding agents can inspect repositories, edit files, run commands, and interact with development tools; explicit instructions and guardrails help keep that autonomy within the intended scope. ([OpenAI](https://openai.com/index/running-codex-safely/?utm_source=chatgpt.com "Running Codex safely at OpenAI | OpenAI"))

### Think of it like this

```text
                 AI Agent
                    │
          ┌─────────┴─────────┐
          │                   │
       ALLOWED              FORBIDDEN
          │                   │
          ▼                   ▼
  User controller       Change DB schema
  User service          Rewrite auth
  User repository       Modify other modules
  User routes           Change architecture
  User tests             Delete existing API
```

So a good prompt has **three parts**:

1. **What to build** → `POST /users`
    
2. **Where it may work** → `User` module + tests
    
3. **What it must not touch** → authentication, schema, unrelated modules
    

OpenAI's guidance for coding agents similarly emphasizes **clear technical boundaries, constrained execution, permissions, and guardrails**, while its agent guidance recommends explicit actions and handling edge cases. ([OpenAI](https://openai.com/index/running-codex-safely/?utm_source=chatgpt.com "Running Codex safely at OpenAI | OpenAI"))

**The concept you're looking for is usually called _scope_, _boundaries_, or _guardrails_ for an AI coding agent.**


---
[[Back-End]]
[[AI]]
[[My-Journey-In-Codeless]]