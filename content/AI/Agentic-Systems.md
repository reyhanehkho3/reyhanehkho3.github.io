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

### **Designing a Human-in-the-Loop with an Agentic System**

**Example: An Agent handling an Issue and proposing a patch**

1. **Trigger:** New issue or user command.
2. **Intake:** Validate input, permissions, and scope.
3. **Discovery:** Read relevant rules, repo, tests, and history.
4. **Planning:** Build a hypothesis or plan with specific change points.
5. **Approval 1 (Human):** A human reviews the scope and approves the riskier parts of the plan.
6. **Execution:** Apply the change in an isolated branch or workspace.
7. **Verification:** Run tests, lint, security checks, and review the diff.
8. **Evaluation:** Assess acceptance criteria and confidence level.
9. **Approval 2 (Human):** A human approves the merge, release, or irreversible action.
10. **Delivery/Report:** Open a PR with evidence and an audit trail.

**Human-in-the-Loop should not be just an "OK" button on something vague.** At the approval point, the system must clearly show: the exact action, the reasoning, the data and system state, the effect, the cost, the rollback strategy, and the evidence.

**Control pattern:**
- **Low risk + high confidence** → auto-execute and log
- **Medium risk or low confidence** → ask, clarify, or review
- **High risk or irreversible** → explicit human approval
- **Policy violation** → block

**Evaluation metrics:** task success rate, need for manual correction, tool errors, safety violations, latency, cost, rate of escalation, and quality of evidence.

---
[[AI]]