---
title: Agentic Systems
publish: true
date created: 2026-08-12
tags:
  - AI
  - Agent
  - orchestrator
---
An **Agentic System** is a combination of state, policies, tools, agents, and a loop that operates in an environment to achieve an outcome.

- **Trigger:** An event that initiates a workflow, for example, a user message, a schedule, a webhook, a record change, or an alert.

- **Orchestrator:** A coordinator that maintains state and lifecycle, routes tasks, and manages approvals, timeouts, retries, dependencies, and the final result.

- **Agent:** Makes decisions at non-deterministic points.

- **Worker/Tool:** Executes a specific, bounded piece of work.

**Sample flow:**
Trigger → Validate/Deduplicate → Orchestrator → Agent/Worker Steps → Approval (if needed) → Result → Audit

An Orchestrator does not necessarily have to be an LLM. Often it's better for the lifecycle and deterministic policies to be hardcoded, with only ambiguous decisions delegated to the model.

**Trigger considerations:** authentication, rate limiting, ordering, idempotency, deduplication, webhook verification, and the ability to replay.


---
[[AI]]