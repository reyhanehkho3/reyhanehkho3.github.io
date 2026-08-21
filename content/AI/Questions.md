---
title: Questions
publish: true
date created: 2026-08-03
tags:
  - AI
  - Agent
  - RAG
---
**1. When do you NOT build an Agent?**
When the workflow is fixed, deterministic, and expressible with rules; or when the risk of action is high and the benefit of autonomy is low. I start with the simplest pipeline and only make ambiguous decision points agentic.

**2. How does Memory differ from RAG?**
Memory holds interaction information and the user/agent state; RAG retrieves relevant knowledge from an external corpus. Both provide context, but the source, lifecycle, and access policies are different.

**3. Why does an Agent loop stop?**
A valid final answer, reaching the goal, max iterations/timeout/budget, no-progress repetition, unrecoverable error, or need for human approval.

**4. How do you reduce hallucinations to zero?**
Zero is not realistic. I reduce and manage it with grounding, deterministic tools, evaluation, abstention, citation, validation, and human review for high-risk cases.

**5. Why might an Agent choose the wrong tool?**
Vague descriptions, tool overlap, too many tools, weak context, poor schema, or mismatched model. Solution: small and dynamic tool sets, precise schemas, routing, and tool selection evaluation.

**6. When is retry dangerous?**
When the action is not idempotent, e.g., a payment or email might be duplicated. Idempotency keys, deduplication, and checking previous results are necessary.
(An idempotent action or operation, gives the exact same result no matter how many times you do it.)

**7. Fine-tuning or RAG?**
RAG is for variable, private, and attributable knowledge; fine-tuning is more for behavior, style, or task patterns. They are not full substitutes and can be combined.

**8. How do you choose the similarity threshold?**
With a real validation set and a precision/recall trade-off; not a single fixed number. Scores from different models and indexes are not directly comparable.

**9. When does multi-agent make sense?**
When specialties, permissions, or contexts are genuinely separate and decomposition is clear. Otherwise, coordination overhead outweighs the benefit.

**10. Where do you put Human-in-the-loop?**
Before high-risk actions, when confidence is low, when evidence conflicts, when budget is exceeded, or upon user escalation. The approval must clearly show the action and its effect.