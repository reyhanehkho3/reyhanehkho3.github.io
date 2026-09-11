---
title: Module
publish: true
date created: 2026-09-11
tags:
  - Backend
  - codeless
---
A **module** is a **self-contained part of a program that handles one specific responsibility**.

Think of it as a small box inside your application:

```text
Application
│
├── Auth Module
├── User Module
├── Task Module
└── Notification Module
```

Each module contains the code needed for its particular feature.

### Example

Suppose you have a task manager.

The **Task module** might contain:

```text
tasks/
├── task.controller.js
├── task.service.js
├── task.routes.js
└── task.validation.js
```

Together, these files form the **Task module**.

It might be responsible for:

- creating tasks
    
- deleting tasks
    
- updating tasks
    
- getting tasks
    
- validating task data
    

### Why call it a "module"?

Because you can think about it independently:

```text
Task Module
     ↓
"Everything related to tasks"
```

instead of having task-related code scattered throughout the entire application.

### Module vs file

They're not necessarily the same thing.

A **file** is one source-code file:

```text
task.service.js
```

A **module** is a logical unit of functionality and can contain **one or many files**:

```text
tasks/
├── task.controller.js
├── task.service.js
├── task.routes.js
└── task.validation.js
        ↑
   Task module
```

So the easiest definition is:

> **A module is a self-contained piece of an application that groups code belonging to one functionality or responsibility.**

And **modular architecture** simply means building the application out of these modules.


---
[[Back-End]]
[[My-Journey-In-Codeless]]