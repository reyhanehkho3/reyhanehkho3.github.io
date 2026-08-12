---
title: Risk, AI Error Control, and Testing
publish: true
date created: 2026-08-12
tags:
  - AI
---
**Before making a change, check the blast radius:**
- Which callers depend on this API?
- Is a schema migration or backward compatibility involved?
- Are retry conditions, race conditions, or duplicate actions possible?
- How do performance, privacy, auth, and cost change?
- How are failures and rollback handled?

**Hierarchy of evidence, from weakest to strongest:**
Agent's claim < reading code < diff < running targeted tests < build/lint < integration/e2e < observing real behavior

**Test Pyramid:**
- **Unit:** fast and focused on logic;
- **Integration:** component interactions and dependencies;
- **End-to-End:** real user flows;
- **Static checks:** type checking, linting, and security scanning.

A good test doesn't just cover the happy path; it covers invalid input, boundaries, permissions, dependency failures, and regressions. The goal is not a numeric coverage metric — it's risk reduction.


---
[[AI]]