---
title: Adding Features
publish: true
date created: 2026-08-12
tags:
  - software-development
  - git
---
### **Mental Model Discovery & Feature Implementation**

**Turn the requirement into change points:**
Requirement → Domain Logic → Validation → UI/API Contract → Persistence → Tests → Integration → Docs/Telemetry

**Feature steps:**
1. Clarify the requirement and acceptance criteria.
2. Reconstruct the current path.
3. Find a similar feature and the project's convention.
4. Build an impact map and a file-based plan.
5. Implement the smallest coherent change.
6. Run targeted tests first, then broader tests.
7. Review the diff for unintended changes.
8. Update the mental model and documentation to reflect the new reality.

**Architectural fit principle:** Code that works but bypasses the project's conventions and boundaries does not count as a complete Feature.

### **Implementing a Real Feature on an Existing Product**

**The complete cycle:**
Discovery → Problem Statement → Acceptance Criteria → Design → Implementation → Verification → Review → Release → Monitor → Feedback

A feature must be a usable vertical slice, not a collection of half-finished layers. In the PR, explain:
- Why this change is necessary;
- What has changed and what has been intentionally left unchanged;
- How it has been tested;
- What the risks, rollout plan, migration, and rollback strategy are;
- A log, screenshot, or API sample if needed.

**Definition of Done:** Code is written, tests pass, acceptance criteria are confirmed, review is complete, necessary documentation and telemetry are updated, and the behavior is ready to be released.

---
[[Software-Development]]