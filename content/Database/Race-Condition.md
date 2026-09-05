---
title: Race Condition
publish:
date created: 2026-09-05
tags:
  - database
  - codeless
---
**Definition:** A race condition happens when **two or more operations run at the same time and the final result depends on which one happens first**.  
It usually occurs when they access shared data without proper synchronization, potentially producing incorrect or inconsistent results. ([CWE](https://cwe.mitre.org/data/definitions/362.html?utm_source=chatgpt.com "CWE - CWE-362: Concurrent Execution using Shared Resource with Improper Synchronization ('Race Condition') (4.20)"))

### Simple example

Imagine your bank account has **$100**:

```text
Request A: Read $100
Request B: Read $100

Request A: subtract $80 → $20
Request B: subtract $80 → $20

Final balance: $20 ❌
```

It should have been **-$60** (or one transaction should have been rejected), but both requests read the old `$100` before either update happened. That's a race condition. ([OWASP](https://owasp.org/www-community/pages/vulnerabilities/race_conditions?utm_source=chatgpt.com "Race Conditions | OWASP Foundation"))

### 3 examples

**1. Limited-stock product**

```text
Stock = 1

User A → checks stock → 1 available ✅
User B → checks stock → 1 available ✅

Both buy it → 2 orders ❌
```

Two requests checked the same shared state before either changed it. ([OWASP Cheat Sheet Series](https://cheatsheetseries.owasp.org/cheatsheets/Business_Logic_Security_Cheat_Sheet.html?utm_source=chatgpt.com "Business Logic Security - OWASP Cheat Sheet Series"))

**2. Single-use coupon**

```text
Coupon: "WELCOME50"
        ↓
User sends two requests almost simultaneously
        ↓
Both check → "coupon unused" ✅
        ↓
Both receive the discount ❌
```

The check and the use weren't performed as one atomic operation. ([OWASP Cheat Sheet Series](https://cheatsheetseries.owasp.org/cheatsheets/Business_Logic_Security_Cheat_Sheet.html?utm_source=chatgpt.com "Business Logic Security - OWASP Cheat Sheet Series"))

**3. Counter**

```text
counter = 5

Thread A reads 5
Thread B reads 5
Thread A writes 6
Thread B writes 6

Expected: 7
Actual:   6 ❌
```

Both threads read the same old value, so one update effectively gets lost. ([OWASP](https://owasp.org/www-project-code-review-guide/assets/OWASP_Code_Review_Guide_v2.pdf?utm_source=chatgpt.com "RACE CONDITIONS"))

### How do you prevent it?

You need to make the critical operation **atomic or properly synchronized**. Common approaches include:

- 🔒 **Locks / mutexes** — only one operation can modify the shared resource at a time.
    
- 🗄️ **Database transactions / row locks** — the database controls concurrent modifications.
    
- ⚡ **Atomic operations** — e.g. an atomic increment instead of separate read → modify → write steps. ([OWASP](https://owasp.org/www-community/pages/vulnerabilities/race_conditions?utm_source=chatgpt.com "Race Conditions | OWASP Foundation"))
    

**Easy way to remember:**

> 🏎️ **Race condition = two things are racing to change the same thing, and whoever gets there first affects the result.**


---
[[Database]]
[[My-Journey-In-Codeless]]