---
title: Pressure Test
publish: true
date created: 2026-10-07
tags:
  - devops
---
# What is a pressure test?

People often use **pressure test** to mean putting your system under significant load and seeing how it behaves.

For example, imagine your API normally gets:

```
10 requests/second
```

You gradually increase it:

```
10 req/s
  ↓
50 req/s
  ↓
100 req/s
  ↓
500 req/s
  ↓
1000 req/s
```

You're essentially asking:

> **"How much traffic can my system handle before performance becomes unacceptable or it starts failing?"**

---

## There are several types of tests

### 1. Load test

Test your expected normal traffic.

```
Expected traffic
       ↓
     100 users
       ↓
    Does it work well?
```

Example:

> Our application normally has 500 concurrent users. Let's simulate 500 users.

---

### 2. Stress test

Push beyond the expected capacity.

```
100 users
   ↓
500
   ↓
1000
   ↓
2000
   ↓
5000
```

You're trying to find the breaking point.

For example:

```
              Performance
                  │
                  │ ███
                  │ ███
                  │ ███
                  │  ██
                  │   █
                  └──────────────
                       Traffic
                           ↑
                     system struggles
```

---

### 3. Spike test

Suddenly throw a huge amount of traffic at the system.

Normal:

```
100 req/s
100 req/s
100 req/s
```

Then suddenly:

```
              ↓
           5000 req/s
```

This tests things like:

- Can the application recover?
- Do requests time out?
- Does the database become overloaded?
- Does the queue handle the spike?

---

### 4. Soak test

Run a relatively high load for a **long time**.

For example:

```
500 users
─────────────── 6 hours ───────────────
```

This can reveal problems that don't appear during a 5-minute test:

- memory leaks
- connection leaks
- gradually increasing latency
- database connection exhaustion
- resource exhaustion

---

# Why do we care about p95 and p99?

Suppose you have 10,000 requests.

Maybe most requests are very fast:

```
50ms
60ms
70ms
80ms
...
```

But some are extremely slow.

The **percentiles** help you see that.

### p95

95% of requests were **faster than this value**.

For example:

```
p95 = 400ms
```

means roughly:

> 95% of requests completed in 400ms or less.

The slowest 5% took longer.

### p99

99% completed within that time.

```
p99 = 1.2s
```

means the slowest ~1% are taking more than 1.2 seconds.

This is often more useful than just saying:

```
average = 150ms
```

because averages can hide slow requests.

---

# A realistic k6 example

Suppose your AI chat platform has:

```
POST /sessions
GET  /sessions
POST /sessions/:id/messages
```

You could create a k6 test:

```
import http from 'k6/http';
import { check } from 'k6';

export const options = {
  vus: 50,
  duration: '30s',
};

export default function () {
  const response = http.get('http://localhost:3000/v1/sessions');

  check(response, {
    'status is 200': (r) => r.status === 200,
  });
}
```

This means roughly:

> Run 50 virtual users for 30 seconds and have them request `/v1/sessions`.

Then k6 gives you performance metrics.

---

## One thing to remember

**k6 doesn't make your application faster.**

It's a **measuring tool**.

The workflow is:

```
Build API
   ↓
Run k6
   ↓
Find slow/failing endpoint
   ↓
Investigate
   ↓
Optimize
   ↓
Run k6 again
   ↓
Compare
```

For example, you might discover:

```
GET /sessions
p95 = 200ms
```

Then after adding a database index:

```
GET /sessions
p95 = 40ms
```

That's where load testing becomes really useful.



---
[[DevOps]]