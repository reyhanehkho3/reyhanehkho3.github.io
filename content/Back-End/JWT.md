---
title: JWT
publish: true
date created: 2026-08-29
tags:
  - Backend
  - codeless
---
**Definition:** **JWT = JSON Web Token**, a compact token containing claims that can be digitally signed so a server can verify who/what the token represents.  
**It is commonly used for authentication and authorization between clients and APIs.**

**Examples:**

1. User logs in → server returns JWT → browser sends it with API requests.
2. JWT contains `userId=123` and `role=admin`.
3. Mobile app sends a JWT to access `/api/orders`.

Typical structure:

```
header.payload.signature
```


---
[[Back-End]]
[[JWT]]