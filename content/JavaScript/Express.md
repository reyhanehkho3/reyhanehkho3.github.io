---
title: Express
publish: true
date created: 2026-09-11
tags:
  - javaScript
---
**Express is a backend web framework for Node.js.**

Without Express, you can create a server directly with Node.js, but it can become tedious.

Express makes things like HTTP APIs much easier.

For example:

```javaScript
app.get("/users", (req, res) => {
    res.json([
        { name: "Alice" },
        { name: "Bob" }
    ]);
});
```

Now your backend can have:

```
GET    /users
POST   /users
GET    /users/123
DELETE /users/123
```

This is particularly useful for building **REST APIs**.

So:

```
JavaScript
    ↓
Node.js
    ↓
Express
    ↓
Backend/API
```

Think:

> **Express = tools for building a Node.js backend/server**



---
[[JavaScript]]