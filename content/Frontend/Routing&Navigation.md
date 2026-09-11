---
title: Routing and Navigation
publish:
date created: 2026-09-10
tags:
  - frontend
  - basic
  - codeless
---
Routing determines:

> **Which UI should appear for a particular URL?**

For example:

```
/tasks
/users
/settings
/profile
```

Your frontend router maps URLs to components.

```
/tasks
   ↓
TaskPage

/users
   ↓
UsersPage

/settings
   ↓
SettingsPage
```

---

## Dynamic routes

A route where part of the URL changes.

For example:

```
/users/123
/users/456
/users/789
```

You don't create three routes.

You create:

```
/users/:id
```

Then:

```
/users/123
      ↓
id = 123
```

You can use that ID to fetch:

```
GET /api/users/123
```

## Protected routes

Some pages should only be accessible to authenticated users.

For example:

```
/dashboard
```

requires login.

Conceptually:

```
User visits /dashboard
        ↓
Is authenticated?
    /       \
  Yes       No
   ↓         ↓
Dashboard   Login
```

You can also have authorization:

```
/admin
```

might require:

```
role = ADMIN
```

## State through the URL

The URL can contain useful application state.

For example:

```
/tasks?status=done
```

means:

```
status = done
```

Or:

```
/products?page=3
```

means:

```
page = 3
```

This is useful because URLs are:

- bookmarkable
- shareable
- refresh-safe
- browser-history friendly

For example, you can send someone:

```
/tasks?status=done
```

and they see the same filter.


---
[[Frontend]]
[[My-Journey-In-Codeless]]