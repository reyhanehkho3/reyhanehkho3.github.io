---
title: Middleware
publish: true
date created: 2026-09-17
tags:
  - backend

  - codeless

  - Nitros
---
A **middleware** is a piece of code that runs **between an incoming request and the final request handler**.

Think of it as a checkpoint in the request pipeline:

```text
Client
  │
  │ GET /users
  ▼
Middleware
  │
  │ check / modify / log something
  ▼
Controller / Route Handler
  │
  ▼
Response
```

### A simple example

Suppose a user sends:

```http
GET /users
Authorization: Bearer abc123
```

You might have middleware that logs the request:

```typescript
function logger(req, res, next) {
  console.log(req.method, req.url);
  next();
}
```

The important part is:

```typescript
next();
```

It means:

> "I'm finished; continue to the next step."

So:

```text
GET /users
    ↓
Logger middleware
    ↓
UsersController
    ↓
Response
```

### What is middleware commonly used for?

Middleware can do things **before the request reaches your controller**:

- Logging requests
    
- Checking authentication
    
- Adding information to the request
    
- Parsing request data
    
- Handling CORS
    
- Measuring request duration
    
- Filtering certain requests
    

For example:

```typescript
function logger(req, res, next) {
  console.log(`${req.method} ${req.url}`);
  next();
}
```

Or middleware could add something:

```typescript
function addRequestId(req, res, next) {
  req.requestId = crypto.randomUUID();
  next();
}
```

Then the controller can access:

```typescript
req.requestId
```

### Middleware vs Controller

A useful distinction:

```text
Middleware
    ↓
"Should I do something before this request continues?"

Controller
    ↓
"What should I do for this specific endpoint?"
```

For example:

```text
GET /users
     ↓
Authentication middleware
     ↓
Logging middleware
     ↓
UsersController
     ↓
UsersService
     ↓
Database
```

### In NestJS

NestJS supports middleware too:

```typescript
@Injectable()
export class LoggerMiddleware implements NestMiddleware {
  use(req: Request, res: Response, next: NextFunction) {
    console.log(req.method, req.originalUrl);
    next();
  }
}
```

And you can apply it to routes:

```typescript
export class AppModule implements NestModule {
  configure(consumer: MiddlewareConsumer) {
    consumer
      .apply(LoggerMiddleware)
      .forRoutes('users');
  }
}
```

So whenever a request comes to `/users`, the middleware runs first.

One important NestJS distinction: **middleware isn't the only mechanism for things that run around a request**. NestJS also has **guards, pipes, interceptors, and exception filters**, each designed for different jobs.

---
[[My-Journey-In-Codeless]]
[[Back-End]]