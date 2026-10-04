---
title: Decorator
publish: true
date created: 2026-09-19
tags:
  - javaScript
  - codeless
  - Nitros
---
A **decorator** in TypeScript is a special piece of syntax that lets you **attach information or behavior to a class, method, property, or parameter**.

You can think of it as a **label/instruction placed on code**.

### Simple example

```typescript
@Controller('users')
export class UsersController {
}
```

Here:

```typescript
@Controller('users')
```

is a **decorator**.

It tells NestJS:

> "This class is a controller, and its routes start with `/users`."

So:

```text
@Controller('users')
        ↓
UsersController
        ↓
GET /users
```

### Another NestJS example

```typescript
@Get()
getUsers() {
  return this.usersService.getUsers();
}
```

`@Get()` is also a decorator.

It tells NestJS:

> "When someone sends a GET request to this route, call `getUsers()`."

For example:

```text
GET /users
     ↓
@Get()
     ↓
getUsers()
```

### Decorators you will commonly see in NestJS

```typescript
@Controller('users')
```

Marks a class as a controller.

```typescript
@Get()
```

Handles GET requests.

```typescript
@Post()
```

Handles POST requests.

```typescript
@Injectable()
```

Tells NestJS that a class can be managed by its dependency-injection system.

```typescript
@Inject()
```

Tells NestJS what dependency to inject.

```typescript
@Body()
```

Gets the request body.

```typescript
@Param()
```

Gets URL parameters.

For example:

```typescript
@Get(':id')
getUser(@Param('id') id: string) {
  return this.usersService.findUser(id);
}
```

Here there are **two decorators**:

```text
@Get(':id')       → this method handles GET /users/:id

@Param('id')      → get the id from the URL
```

So a request like:

```text
GET /users/42
```

results in:

```text
@Get(':id')
     ↓
@Param('id')
     ↓
id = "42"
```

### The easiest way to remember it

Since you're learning NestJS, think of decorators as **instructions you attach to your code so NestJS knows what that code is supposed to do**.

```text
@Controller  → "I'm a controller"
@Get         → "I'm handling a GET request"
@Post        → "I'm handling a POST request"
@Injectable   → "NestJS can inject/manage me"
@Body        → "Give me the request body"
@Param       → "Give me a URL parameter"
```

The `@` symbol is the giveaway: **`@Something` is usually a decorator.**


---
[[JavaScript]]
[[My-Journey-In-Codeless]]