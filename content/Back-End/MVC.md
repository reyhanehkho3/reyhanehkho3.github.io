---
title: MVC
publish:
date created: 2026-09-11
tags:
  - Backend
  - Architecture
  - codeless
---
**MVC** stands for **Model–View–Controller**. It is a way to organize an application by separating responsibilities into three parts.

```text
        User
         ↓
    Controller
      ↙     ↘
 Model       View
  ↓           ↓
Database    User sees UI
```

### 1. Model

The **Model** handles the application's **data and business rules**.

For example:

```js
User
- id
- name
- email
```

It might communicate with the database:

```text
Model → PostgreSQL
```

---

### 2. View

The **View** is what the user sees.

For a web application:

```text
HTML
CSS
UI components
```

For example:

```text
┌─────────────────────┐
│ Welcome, Reyhaneh   │
│                     │
│ [ View Profile ]    │
└─────────────────────┘
```

---

### 3. Controller

The **Controller** handles the request/action and coordinates the other parts.

For example:

```http
GET /users/123
```

The controller might:

```text
Request
  ↓
UserController
  ↓
UserModel
  ↓
Database
  ↓
UserController
  ↓
Response
```

Example:

```js
async function getUser(req, res) {
    const user = await User.findById(req.params.id);

    res.json(user);
}
```

---

## In a backend application

You might have:

```text
src/
├── controllers/
│   └── userController.js
├── models/
│   └── userModel.js
├── routes/
│   └── userRoutes.js
└── app.js
```

The flow could be:

```text
HTTP Request
     ↓
   Route
     ↓
 Controller
     ↓
   Model
     ↓
 Database
     ↓
 Controller
     ↓
 HTTP Response
```

### Important distinction

MVC is mainly about **separation of responsibilities**.

Instead of putting everything here:

```js
app.get("/users/:id", async (req, res) => {
    // validation
    // business logic
    // database query
    // formatting response
    // ...
});
```

you separate those responsibilities into appropriate parts.

Also, **MVC is an architectural pattern**, not a requirement for REST APIs. You can build a REST API using MVC, but REST itself doesn't require MVC.


---
[[Back-End]]
[[My-Journey-In-Codeless]]