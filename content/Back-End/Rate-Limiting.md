---
title: Rate Limiting
publish: true
date created: 2026-09-05
tags:
  - Backend
  - codeless
---
**Definition:** Rate limiting is a technique that **limits how many requests or operations a client can make within a certain amount of time**.  
It protects a system from overload, excessive resource usage, abuse, and some denial-of-service attacks. ([MDN Web Docs](https://developer.mozilla.org/en-US/docs/Glossary/Rate_limit?utm_source=chatgpt.com "Rate limit - Glossary | MDN"))

### Simple example

Suppose your API has:

```text
Maximum: 100 requests / minute / user
```

A user sends:

```text
Request 1   ✓
Request 2   ✓
...
Request 100 ✓
Request 101 ❌
```

The server can respond with:

```text
HTTP 429 Too Many Requests
```

and may include `Retry-After` to tell the client when to try again. ([MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Status/429?utm_source=chatgpt.com "429 Too Many Requests - HTTP | MDN"))

### 3 examples

**1. Login**

```text
5 login attempts / minute
```

This prevents someone from continuously trying passwords against an account.

**2. API**

```text
1000 requests / hour / user
```

If a user exceeds the limit, additional requests are rejected or delayed.

**3. SMS verification**

```text
3 OTP requests / 10 minutes / phone number
```

This prevents someone from repeatedly requesting SMS messages and potentially abusing the service.

### Where can it be applied?

Rate limits can be based on different things:

```text
IP address
     ↓
User
     ↓
API key
     ↓
Endpoint
     ↓
Resource
```

For example, you might allow a normal user **100 requests/minute**, but allow only **5 password-reset requests/hour**. OWASP recommends tuning limits according to the specific operation and business requirements. ([GitHub](https://github.com/OWASP/API-Security/blob/master/editions/2023/en/0xa4-unrestricted-resource-consumption.md?utm_source=chatgpt.com "API-Security/editions/2023/en/0xa4-unrestricted-resource-consumption.md at master · OWASP/API-Security · GitHub"))

### Rate limiting vs. throttling

You'll often hear these terms together. **Rate limiting** defines how much traffic/operation is allowed; **throttling** generally means slowing or restricting activity when the limit is approached or exceeded. In practice, the terms are often used interchangeably. ([MDN Web Docs](https://developer.mozilla.org/en-US/docs/Glossary/Rate_limit?utm_source=chatgpt.com "Rate limit - Glossary | MDN"))

**Easy way to remember:**

> **Rate limiting = “You can do this X times within Y time.”**  
> Example: **100 API requests per minute per user.**