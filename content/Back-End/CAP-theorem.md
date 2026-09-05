---
title: CAP theorem
publish:
date created: 2026-09-05
tags:
  - codeless
  - Backend
  - CAP
---
**Definition:** The CAP theorem says that a distributed system cannot guarantee **Consistency, Availability, and Partition Tolerance all at the same time** when a network partition occurs. ([AWS Documentation](https://docs.aws.amazon.com/whitepapers/latest/availability-and-beyond-improving-resilience/cap-theorem.html?utm_source=chatgpt.com "CAP theorem - Availability and Beyond: Understanding and Improving the Resilience of Distributed Systems on AWS"))  
In practice, because network failures can happen, you usually have to choose whether to favor **Consistency (C)** or **Availability (A)** during a partition. ([AWS Documentation](https://docs.aws.amazon.com/whitepapers/latest/availability-and-beyond-improving-resilience/cap-theorem.html?utm_source=chatgpt.com "CAP theorem - Availability and Beyond: Understanding and Improving the Resilience of Distributed Systems on AWS"))

### First, understand the 3 letters

- **C — Consistency:** Every read gets the latest correct value (or an error).
    
- **A — Availability:** Every request gets a response, even if some nodes can't communicate.
    
- **P — Partition Tolerance:** The system continues operating even when nodes **cannot communicate with each other** because of a network failure. ([AWS Documentation](https://docs.aws.amazon.com/whitepapers/latest/availability-and-beyond-improving-resilience/cap-theorem.html?utm_source=chatgpt.com "CAP theorem - Availability and Beyond: Understanding and Improving the Resilience of Distributed Systems on AWS"))
    

### Simple example

Imagine you have two database servers:

```text
        Network
   ┌───────────────┐
   │               │
Server A         Server B
  $100             $100
```

Now the network connection between them breaks:

```text
Server A    ❌    Server B
  $100             $100
```

A user changes the balance on Server A to `$50`.

Now the system has a problem:

**Option 1 — Consistency**

Server B cannot confirm the new value, so the system **refuses/blocks the operation**.

```text
User → Server A → "Sorry, cannot complete"
```

You preserve **C**, but sacrifice **A** during the partition.

**Option 2 — Availability**

Server A accepts the change and responds immediately:

```text
User → Server A → "Success"
```

But Server B might still think the balance is `$100`.

You preserve **A**, but sacrifice **C** during the partition.

That's the core idea of CAP. ([AWS Documentation](https://docs.aws.amazon.com/whitepapers/latest/availability-and-beyond-improving-resilience/cap-theorem.html?utm_source=chatgpt.com "CAP theorem - Availability and Beyond: Understanding and Improving the Resilience of Distributed Systems on AWS"))

### 3 practical examples

**1. Banking system — favor Consistency**

If your bank's servers cannot communicate, you'd rather temporarily reject a transaction than allow two servers to show different account balances.

```text
Network failure
      ↓
Reject transaction
      ↓
Keep balance correct
```

**2. Social media — favor Availability**

If Instagram-like servers can't communicate, you may still want users to post and view content, even if some information temporarily isn't synchronized.

```text
Network failure
      ↓
Keep serving users
      ↓
Synchronize later
```

**3. Shopping cart — favor Availability**

If you add an item to a shopping cart while one server is temporarily disconnected, the system may accept the change and synchronize it later rather than completely preventing you from using the shop.

---

### CP vs AP

This is where you'll often hear:

**CP — Consistency + Partition Tolerance**

```text
Network partition
       ↓
Can't guarantee consistency
       ↓
Reject/delay some requests
```

**AP — Availability + Partition Tolerance**

```text
Network partition
       ↓
Keep accepting requests
       ↓
Data may temporarily differ
```

You will sometimes hear people say **“pick any two of C, A, and P.”** That's a useful beginner mnemonic, but technically the important trade-off happens **when a partition occurs**: you generally choose between consistency and availability. ([AWS Documentation](https://docs.aws.amazon.com/whitepapers/latest/availability-and-beyond-improving-resilience/cap-theorem.html?utm_source=chatgpt.com "CAP theorem - Availability and Beyond: Understanding and Improving the Resilience of Distributed Systems on AWS"))

### ⚠️ One important clarification

CAP's **Consistency** is not the same thing as the **C in ACID**. In the formal CAP definition, consistency refers specifically to a strong guarantee called **linearizability**. ([Martin Kleppmann](https://martin.kleppmann.com/2015/05/11/please-stop-calling-databases-cp-or-ap.html?utm_source=chatgpt.com "Please stop calling databases CP or AP — Martin Kleppmann’s blog"))

**Easy way to remember:**

> **C:** “Give me the correct/latest answer.”  
> **A:** “Give me an answer.”  
> **P:** “Keep working even when servers can't talk to each other.”



---
[[Back-End]]
[[My-Journey-In-Codeless]]