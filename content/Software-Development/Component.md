---
title: Component
publish: true
date created: 2026-08-28
tags:
  - software-development
  - codeless
---
**Definition:** A component is a **distinct, reusable part of a software system** that performs a specific responsibility.  
A component usually has a defined interface through which other parts of the system interact with it.

**Examples:**

1. A `PaymentService` component processes payments.
2. A React `LoginForm` component displays and handles login.
3. A database component stores and retrieves customer information.

### Module vs Component

A simple way to remember it:

**Module = organizational unit of code**  
**Component = functional building block that interacts with other parts**

For example:

```
E-commerce System
│
├── Payment Module
│   ├── Payment Component
│   ├── Refund Component
│   └── Invoice Component
│
└── User Module
    ├── Login Component
    └── Profile Component
```

The exact distinction can vary depending on the architecture/framework.


---
[[Software-Development]]
[[My-Journey-In-Codeless]]