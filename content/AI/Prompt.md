---
title: Prompt
publish: true
date created: 2026-08-12
tags:
  - AI
---
### Structure
A prompt usually has:
- Goal.
- Context.
- Constraints.
- Acceptance Criteria.
- Output Contract.
- Verification.


### Example
**Goal:** Make the account deletion endpoint idempotent.

**Context:** The API is located in `src/account`; the project pattern follows the billing endpoints.

**Constraint:** The public API contract and the database schema must not change.

**Acceptance Criteria:** A repeated request should not return an error, and a regression test must be added.

**Before editing, report the request path and the points of change.**



- Note: More context isn't always better. Use progressive disclosure. First the plan, then the related files, then necessary details.