---
title: Winston
publish: true
date created: 2026-09-17
tags:
  - nodejs

  - javascript

  - codeless

  - Nitros
---
**Winston** is a **logging library for Node.js**. It is used to record what is happening inside your application.

For example, instead of:

```ts
console.log("User logged in");
```

you can use Winston:

```ts
logger.info("User logged in");
```

### Why use Winston?

The main advantage is that Winston gives you a structured and configurable logging system.

```text
Your application
       │
       ▼
     Winston
       │
       ├── Console
       ├── Log file
       ├── Database
       └── External logging system
```

### Different log levels

Winston supports different severity levels:

```ts
logger.error("Database connection failed");
logger.warn("Login attempt failed");
logger.info("User logged in");
logger.debug("Request payload: ...");
```

This lets you distinguish between normal application activity and problems.

### Logging to files

You can configure Winston to save logs:

```text
logs/
├── error.log
└── combined.log
```

For example:

```ts
new winston.transports.File({
  filename: "logs/error.log",
  level: "error"
})
```

So errors can be persisted rather than disappearing when the terminal closes.

### Winston vs `console.log`

|`console.log`|Winston|
|---|---|
|Simple|Configurable|
|Mainly console|Console, files, external systems, etc.|
|No standard log levels by default|`error`, `warn`, `info`, `debug`, etc.|
|Harder to manage in production|Designed for production logging|
|Basic formatting|Structured/custom formatting|

### In a NestJS application

Since you've been working with **NestJS**, Winston is particularly relevant. You can use it as the application's logger:

```text
NestJS application
       │
       ▼
     Winston
       │
       ├── Console logs
       ├── Error logs
       └── Log files / monitoring system
```

So, in one sentence:

> **Winston is used to create, format, store, and manage application logs in Node.js applications.**


---
[[JavaScript]]
[[My-Journey-In-Codeless]]