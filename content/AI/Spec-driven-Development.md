---
title: Spec-driven Development
publish: true
date created: 2026-08-25
tags:
  - AI
  - Agent
  - codeless
---
**Definition:** A development approach in which the system's behavior and requirements are precisely defined in a Specification before implementation.

**Simply put:** Instead of saying **“go write the code,”** you first specify exactly **what should be built and what requirements it must satisfy**.

**Examples:**

1. Write the API Contract first, then build the API.
2. Write Acceptance Criteria first, then implement the feature.
3. Define Login behavior first, then start coding.


**STD = Spec-Driven Development / Specification-Driven Development**

It means:

> **Define the expected behavior/specification first, then implement the code to satisfy that specification.**

A simple flow is:

```text
Specification
     ↓
Tests
     ↓
Implementation
     ↓
Run tests
     ↓
Refine
```

### Example

Suppose you're building a login API.

First, define the specification:

```text
POST /login

Given:
- valid email
- valid password

Then:
- return 200
- return an access token

Given:
- wrong password

Then:
- return 401
```

Then you can write tests for those requirements:

```text
✓ valid credentials → 200
✓ wrong password → 401
✓ missing email → 400
```

Then implement the login functionality until the tests pass.

### STD vs TDD

They're related but **not exactly the same**.

**TDD — Test-Driven Development**

```text
Test
 ↓
Code
 ↓
Refactor
```

You write a test **before** the implementation.

**Spec-Driven Development**

```text
Specification
 ↓
Implementation
 ↓
Tests/verification
```

The **specification is the source of truth**. Tests are often derived from or used to verify the specification.

So if you're working with an AI coding agent, STD can be particularly useful:

```text
Requirements/spec
      ↓
Agent understands what must be built
      ↓
Agent implements
      ↓
Agent writes/runs tests
      ↓
Verify against spec
```

**Short version:**

> **STD = build according to a clearly defined specification, rather than starting by writing code and figuring out the requirements afterward.**

---
[[AI]]
[[Agent]]
[[My-Journey-In-Codeless]]