---
title: Interceptor
publish:
date created: 2026-08-27
tags:
  - codeless
  - Backend
---
**Definition:** An interceptor is code that **automatically runs before, after, or around another operation** without changing the operation itself.  
It is commonly used for things such as authentication, logging, validation, and error handling.

**Examples:**

1. Every API request passes through an interceptor that checks the user's token.
2. An interceptor records how long every HTTP request takes.
3. An interceptor catches exceptions and converts them into standard error responses.


**Interceptor can be considered a design pattern/concept**, but it depends on the context.

An **interceptor** is mainly a way to **run code before, after, or around another operation without changing the operation itself**.

### Simple example

Imagine every API request needs logging:

```text
Request
   ↓
Interceptor
   ↓
Controller
   ↓
Response
```

The interceptor can do:

```text
before:
  log "request started"

controller:
  handle request

after:
  log "request finished"
```

The controller doesn't need to contain the logging code.

### Common uses

Interceptors are often used for:

- Logging
    
- Authentication
    
- Authorization
    
- Metrics
    
- Tracing
    
- Adding headers
    
- Error handling
    
- Request/response transformation
    
- Performance measurement
    

For example, with tracing:

```text
HTTP request
    ↓
Interceptor
    ↓
create/get trace ID
    ↓
Controller
    ↓
Service
    ↓
Database
```

### Is it a GoF design pattern?

**Not exactly.**

The classic **Gang of Four (GoF)** design patterns don't have a pattern simply called "Interceptor."

But **Interceptor Pattern** is a recognized architectural/design pattern, especially in frameworks and middleware-based systems.

It's closely related to concepts like:

- **Middleware**
    
- **Decorator**
    
- **Proxy**
    
- **Aspect-Oriented Programming (AOP)**
    

### Interceptor vs middleware

They're very similar.

For example, in Express you commonly use **middleware**:

```js
app.use((req, res, next) => {
    console.log("request started");
    next();
});
```

In frameworks such as Spring, NestJS, or Axios, you may encounter something explicitly called an **interceptor**.

So a useful mental model is:

> **Interceptor = a mechanism that intercepts an operation so you can execute cross-cutting logic around it.**

And **logging, authentication, tracing, metrics** are examples of _why_ you'd use one.

For example, suppose your frontend calls:

```text
GET /api/profile
GET /api/tasks
GET /api/projects
```

Without an interceptor, you might have to repeat:

```js
fetch("/api/profile", {
  headers: {
    Authorization: `Bearer ${token}`
  }
});

fetch("/api/tasks", {
  headers: {
    Authorization: `Bearer ${token}`
  }
});
```

That's repetitive.

With an **HTTP client interceptor**, you configure it once:

```text
Request
   ↓
Interceptor
   │
   ├── get token
   ├── add Authorization header
   └── send request
        ↓
     Backend
```

So your code can simply do:

```js
api.get("/profile");
api.get("/tasks");
api.get("/projects");
```

and the interceptor automatically adds:

```http
Authorization: Bearer <token>
```

to each request.

### Axios example

```js
const api = axios.create({
  baseURL: "/api"
});

api.interceptors.request.use((config) => {
  const token = localStorage.getItem("accessToken");

  if (token) {
    config.headers.Authorization = `Bearer ${token}`;
  }

  return config;
});
```

Now every request made through `api` automatically gets the token.

### Important distinction

The **interceptor doesn't store the token by itself**.

Usually:

```text
Token storage
     ↓
Interceptor reads token
     ↓
Interceptor adds token to request
     ↓
Backend
```

And interceptors can also handle responses. For example, if the backend returns:

```text
401 Unauthorized
```

the response interceptor can attempt to **refresh the access token** and retry the original request.


> **Interceptors are useful when you have common request/response behavior that you don't want to repeat manually for every request.**

---
[[Back-End]]
[[My-Journey-In-Codeless]]