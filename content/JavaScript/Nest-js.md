---
title: Nest.js
publish: true
date created: 2026-09-17
tags:
  - javascript

  - codeless

  - Nitros
  - nodejs

---
**NestJS** is a **Node.js backend framework** used to build scalable, structured server-side applications, especially APIs and web services.

Think of it like this:

> **NestJS = a framework for building backends with Node.js + TypeScript**

### Where does NestJS fit?

If you're building a web application:

```text
Frontend
  ↓
Vue / React / Next.js
  ↓ HTTP requests
Backend
  ↓
NestJS
  ↓
Database
PostgreSQL / MySQL / MongoDB
```

NestJS runs on the **server**, not in the browser.

### Why use NestJS?

NestJS gives you a predefined architecture for organizing your backend.

For example:

```text
src/
├── users/
│   ├── users.controller.ts
│   ├── users.service.ts
│   ├── users.module.ts
│   └── dto/
├── auth/
│   ├── auth.controller.ts
│   ├── auth.service.ts
│   └── auth.module.ts
└── app.module.ts
```

Instead of putting all your backend code into a few large files, NestJS encourages you to divide the application into **modules, controllers, services, DTOs, guards, pipes**, etc.

### The main concepts

**1. Controller**

Handles incoming HTTP requests.

```typescript
@Controller('users')
export class UsersController {
  @Get()
  getUsers() {
    return ['Alice', 'Bob'];
  }
}
```

So:

```text
GET /users
      ↓
UsersController
      ↓
getUsers()
```

---

**2. Service**

Contains the business logic.

```typescript
@Injectable()
export class UsersService {
  getUsers() {
    // get users from database
  }
}
```

Usually the controller calls the service:

```text
Request
   ↓
Controller
   ↓
Service
   ↓
Database
```

---

**3. Module**

Groups related functionality.

```typescript
@Module({
  controllers: [UsersController],
  providers: [UsersService],
})
export class UsersModule {}
```

For example:

```text
UsersModule
 ├── UsersController
 └── UsersService
```

---

**4. DTO**

A **Data Transfer Object** defines the structure of data being sent to your API.

For example:

```typescript
export class CreateUserDto {
  name: string;
  email: string;
  password: string;
}
```

A request might look like:

```json
{
  "name": "Alice",
  "email": "alice@example.com",
  "password": "123456"
}
```

NestJS can also validate DTOs.

---

### NestJS vs Node.js

This distinction is important:

**Node.js** is the runtime.

**NestJS** is a framework running on Node.js.

```text
Node.js
   ↓
NestJS
   ↓
Your backend application
```

A similar analogy:

```text
JavaScript → Node.js → NestJS
```

You can build a backend directly with Node.js, but NestJS gives you a lot of structure and tools.

### NestJS vs Next.js

The names are confusing:

| |**Next.js**|**NestJS**|
|---|---|---|
|Main purpose|Build **web applications / frontend**|Build **backend / APIs**|
|Based on|React|Node.js|
|Runs primarily|Server + browser|Server|
|UI components|✅ Yes|❌ No|
|REST APIs|✅ Can|✅ Yes|
|Database access|Possible|Common|
|Routing|Pages/app routes|Controllers|
|Rendering|SSR, SSG, CSR|Not its purpose|
|Typical use|Websites, web apps|APIs, backend services|

A common architecture could therefore be:

```text
             ┌── Vue.js / React
Browser ────┤
             │
             └── HTTP
                  ↓
              NestJS
                  ↓
              PostgreSQL
```

If your project has a **`backend/` directory containing things like `app.module.ts`, `auth.service.ts`, and `users.service.ts`**, that's very likely a NestJS backend.

---
[[JavaScript]]
[[My-Journey-In-Codeless]]