---
title: Atomic Transaction
publish: true
date created: 2026-08-29
tags:
  - database
  - codeless
---
**Definition:** An **atomic transaction** is a group of database operations that is treated as **one indivisible unit: either all operations succeed, or none of them take effect**.

Think of it as **"all or nothing."** If something fails halfway through, the database rolls back the changes so you don't end up with partial results.

### Example  — Bank transfer

```
Transfer €100 from Alice → Bob

1. Alice balance: -€100  ✅
2. Bob balance:   +€100  ❌ ← failure
```

Without atomicity, Alice could lose €100 while Bob receives nothing.

With an atomic transaction:

```
BEGIN

Alice -= €100
Bob   += €100

COMMIT
```

If step 2 fails:

```
ROLLBACK
```

Alice's €100 is restored. **Either both changes happen or neither happens.**



---
[[Database]]
[[My-Journey-In-Codeless]]