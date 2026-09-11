---
title: Log Levels
publish:
date created: 2026-09-11
tags:
  - Backend
  - log
  - codeless
---
**Log levels** tell you how important or severe a log message is.

Think of them as a way to classify what your backend is reporting.

A common hierarchy is:

```text
TRACE
  ↓
DEBUG
  ↓
INFO
  ↓
WARN
  ↓
ERROR
  ↓
FATAL
```

Not every logging library supports all of these.

---

## 1. TRACE

**Very detailed information for tracing exactly what the program is doing.**

Example:

```text
TRACE Entering TaskService.createTask()
TRACE taskId = 42
TRACE Checking project membership
TRACE Query completed in 12ms
```

Usually only useful when debugging complicated problems.

---

## 2. DEBUG

Information useful to **developers while debugging**.

Example:

```text
DEBUG User 42 requested project 10
DEBUG Querying tasks for project 10
DEBUG Found 15 tasks
```

You generally don't want huge amounts of DEBUG logs in production.

---

## 3. INFO

Normal, meaningful events that show that the system is working.

Examples:

```text
INFO Server started on port 3000
INFO User 42 logged in
INFO Task 15 created
INFO Database connection established
```

Think:

> **"Something happened, and it's useful to know."**

This is often your default production log level.

---

## 4. WARN

Something unusual or potentially problematic happened, **but the application can continue working**.

Examples:

```text
WARN Login failed for user 42
WARN API request took 2.5 seconds
WARN Database connection pool is 80% full
WARN Refresh token is close to expiration
```

Think:

> **"Something isn't quite right."**

A warning isn't necessarily an error.

---

## 5. ERROR

Something failed and an operation couldn't be completed correctly.

Examples:

```text
ERROR Failed to create task
ERROR Database query failed
ERROR Payment processing failed
ERROR Unable to send notification
```

The application might still be running.

For example:

```text
Request A → ERROR
Request B → works
Request C → works
```

One operation failed, but the entire server isn't necessarily dead.

---

## 6. FATAL

A **critical error that prevents the application from continuing**.

Example:

```text
FATAL Database connection cannot be established
FATAL Application configuration is invalid
```

For example:

```text
Application starts
      ↓
Cannot connect to database
      ↓
Cannot function
      ↓
FATAL
      ↓
Process exits
```

Some logging libraries don't use `FATAL` and simply use `ERROR`.

---

# How filtering works

This is one of the most useful things to understand.

Suppose your configured log level is:

```text
INFO
```

You generally see:

```text
INFO
WARN
ERROR
FATAL
```

but not:

```text
DEBUG
TRACE
```

Because DEBUG and TRACE are considered less severe/detailed than INFO.

For example:

```text
Configured level: INFO

TRACE  ❌
DEBUG  ❌
INFO   ✅
WARN   ✅
ERROR  ✅
FATAL  ✅
```

If you configure:

```text
DEBUG
```

you get:

```text
DEBUG  ✅
INFO   ✅
WARN   ✅
ERROR  ✅
FATAL  ✅
```

---

# In a backend

Imagine your API receives:

```http
POST /api/tasks
```

Your logs might look like:

```text
INFO  POST /api/tasks
DEBUG Request body validated
DEBUG User 42 has ADMIN role
INFO  Task created: id=15
```

If something goes wrong:

```text
INFO  POST /api/tasks
DEBUG User 42 has ADMIN role
ERROR Failed to insert task into database
```

---

# Log level vs log message

These are different things.

```text
INFO: User logged in
```

Here:

```text
INFO
```

is the **log level**.

And:

```text
User logged in
```

is the **log message**.

A structured logger might produce:

```json
{
  "level": "info",
  "message": "User logged in",
  "userId": 42
}
```

This is called **structured logging**, and it's very useful in production.

---

# The levels I'd focus on

For your backend projects, you don't need to worry about every possible level initially.

Learn these four very well:

```text
DEBUG → Developer details

INFO  → Normal important events

WARN  → Something unusual/problematic

ERROR → Something failed
```

A simple rule:

> **DEBUG = "What is the code doing?"**  
> **INFO = "What happened normally?"**  
> **WARN = "Something might be wrong."**  
> **ERROR = "Something went wrong."**


---
[[Back-End]]
[[My-Journey-In-Codeless]]