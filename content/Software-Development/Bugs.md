---
title: Bugs
publish: true
date created: 2026-08-12
tags:
  - software-development
---
Bug fixing is scientific, not random code tweaking.

**The process:**
Report → Reproduce → Isolate → Hypothesize → Observe → Fix → Test → Verify → Regression Test

**A good bug report includes:** expected behavior, actual behavior, reproduction steps, environment/version, sample input, and evidence.

**Rules:**
1. Before fixing a bug, reproduce it or gather sufficient evidence.
2. Distinguish between correlation and cause.
3. Test one hypothesis at a time, rejecting or confirming it with evidence.
4. Apply the smallest fix that addresses the root cause.
5. A regression test must fail before the fix and pass after it.
6. Verify that the fix doesn't break other behavior.

### **Advanced Root Cause Analysis (RCA)**

A **symptom** is what we observe; a **root cause** is the mechanism that, if fixed, prevents the issue from recurring.

**Example:** A timeout is a symptom; a missing index, lock contention, a query without a WHERE clause, or a retry storm could be the root cause.

**RCA tools:**
- **Five Whys,** grounded in evidence, not guesswork;
- **Event timeline;**
- **Diff** between a healthy and a broken version;
- **Logs, metrics, traces,** and correlation IDs;
- **Git bisect** to find the introducing commit;
- **Minimal reproduction;**
- **Fault tree** for multiple probable causes.

**A professional RCA output includes:**
1. Impact and scope;
2. Timeline;
3. Technical root cause and contributing factors;
4. Evidence;
5. Immediate fix;
6. Preventive actions;
7. Method for verifying the fix.

**Go beyond saying "fixed by adding a null check";** ask why the null reached that point and why the contract or a test didn't catch it earlier.



---
[[Software-Development]]

