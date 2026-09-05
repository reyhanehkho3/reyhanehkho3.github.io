---
title: idempotency
publish: true
date created: 2026-09-05
tags:
  - database
  - codeless
---
**Definition:** Idempotency means that performing the **same operation multiple times has the same intended effect as performing it once**. ([RFC Editor](https://www.rfc-editor.org/rfc/rfc9110.html?utm_source=chatgpt.com "RFC 9110: HTTP Semantics"))  
It is especially important in APIs because if a request times out, you can **retry it without accidentally performing the action twice**. ([Stripe Docs](https://docs.stripe.com/api/idempotent_requests?lang=curl&utm_source=chatgpt.com "Idempotent requests | Stripe API Reference"))

### Simple example

Imagine you want to **delete user #123**:

```text
DELETE /users/123
```

You send it once → user is deleted.

You accidentally send it 5 times → user is **still just deleted**, not deleted 5 times.

That's idempotency.

---

### 3 examples

**1. Payment**

You click **Pay €100**, but the network times out.

```text
Client → Server
        "Pay €100"
           ↓
       Payment succeeds
           ↓
      Response lost ❌
```

The client retries the request. With an **idempotency key**, the server recognizes that this is the same payment and doesn't charge you twice. Stripe uses this approach for API retries. ([Stripe Docs](https://docs.stripe.com/api/idempotent_requests?lang=curl&utm_source=chatgpt.com "Idempotent requests | Stripe API Reference"))

```text
Idempotency-Key: abc123
```

---

**2. Updating a user's profile**

```text
PUT /users/123

{
  "name": "Reyhaneh"
}
```

Send it once → name becomes `Reyhaneh`.

Send it 10 times → name is still `Reyhaneh`.

So the operation is idempotent. HTTP defines `PUT` as an idempotent method. ([RFC Editor](https://www.rfc-editor.org/rfc/rfc9110.html?utm_source=chatgpt.com "RFC 9110: HTTP Semantics"))

---

**3. Creating an order**

Suppose:

```text
POST /orders
```

creates an order.

If the client sends it twice:

```text
Request 1 → Order #100 created
Request 2 → Order #101 created ❌
```

That's **not idempotent**.

You can make it safely retryable by giving both requests the same idempotency key:

```text
Idempotency-Key: order-abc123

Request 1 → Order #100 created
Request 2 → Return Order #100
```

No duplicate order is created. ([Stripe Docs](https://docs.stripe.com/api/idempotent_requests?lang=curl&utm_source=chatgpt.com "Idempotent requests | Stripe API Reference"))

### Easy way to remember

> **Idempotent = “I can safely do this again.”**

And an important distinction:

**Idempotency ≠ “the request only runs once.”**

The server may receive the request multiple times; **the important part is that repeating it doesn't produce an additional unintended effect**. ([RFC Editor](https://www.rfc-editor.org/rfc/rfc9110.html?utm_source=chatgpt.com "RFC 9110: HTTP Semantics"))


---
[[Database]]
[[My-Journey-In-Codeless]]