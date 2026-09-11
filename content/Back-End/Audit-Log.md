---
title: Audit Log
publish:
date created: 2026-09-11
tags:
  - Backend
  - log
  - codeless
---
An **audit log** is a record of **important actions performed in your system**.

Think of it as the application's **history book**:

> **Who did what, to which resource, when, and what happened?**

---

## Example

Suppose an admin deletes a user.

Your normal application log might say:

```text
INFO User deleted successfully
```

An **audit log** contains much more context:

```text
Actor:       user 42
Action:      DELETE_USER
Target:      user 87
Time:        2026-09-11 13:20:15
Result:      SUCCESS
IP:          192.168.1.20
```

So later you can answer:

> "Who deleted user 87?"

---

# Audit log vs normal log

This distinction is important.

### Normal application log

Used mainly for **debugging and monitoring**.

```text
INFO Task created
ERROR Database connection failed
WARN Request took 3 seconds
```

### Audit log

Used for **tracking important actions and accountability**.

```text
User 42
→ changed User 87's role
→ from USER to ADMIN
→ at 13:20
```

Think:

```text
Application logs → "What is the system doing?"

Audit logs       → "Who did what?"
```

---

# What should an audit log contain?

A typical audit record might have:

```text
id
actor_id
action
resource_type
resource_id
timestamp
result
metadata
```

For example:

```json
{
  "id": 1523,
  "actor_id": 42,
  "action": "UPDATE_USER_ROLE",
  "resource_type": "USER",
  "resource_id": 87,
  "timestamp": "2026-09-11T13:20:15Z",
  "result": "SUCCESS",
  "metadata": {
    "oldRole": "USER",
    "newRole": "ADMIN"
  }
}
```

---

# What actions should be audited?

Usually **security-sensitive or important business actions**.

For example:

### User management

```text
CREATE_USER
DELETE_USER
DEACTIVATE_USER
ACTIVATE_USER
CHANGE_USER_ROLE
```

### Authentication

```text
LOGIN_SUCCESS
LOGIN_FAILURE
LOGOUT
PASSWORD_CHANGED
```

### Projects

```text
CREATE_PROJECT
DELETE_PROJECT
ADD_PROJECT_MEMBER
REMOVE_PROJECT_MEMBER
```

### Tasks

```text
CREATE_TASK
DELETE_TASK
ASSIGN_TASK
CHANGE_TASK_STATUS
```

---

# Audit logs are often append-only

This is a very important concept.

Suppose:

```text
User 42 deleted User 87
```

You don't want someone to simply modify that audit record afterward.

So audit logs are commonly designed as:

```text
INSERT → INSERT → INSERT → INSERT
```

rather than:

```text
INSERT
UPDATE
DELETE
```

In other words:

> **You add new audit events, but don't modify old ones.**

For example:

```text
1. User 42 → created project
2. User 42 → added user 87
3. User 87 → changed task status
4. Admin 5 → removed user 87
```

The history remains.

---

# Where does the audit log live?

It can be stored in a database.

For example, PostgreSQL:

```text
users
projects
tasks
audit_logs
```

An `audit_logs` table might look like:

```text
audit_logs
────────────────────────────
id
actor_id
action
resource_type
resource_id
timestamp
metadata
```

---

# Audit log in your backend flow

Imagine:

```http
DELETE /api/users/87
```

The flow could be:

```text
Frontend
   ↓
HTTP Request
   ↓
Authentication
   ↓
Authorization
   ↓
Controller
   ↓
Service
   ↓
Delete user
   ↓
Create audit log
   ↓
HTTP Response
```

The database might perform:

```text
DELETE FROM users WHERE id = 87

INSERT INTO audit_logs (...)
```

Ideally, if both operations must succeed together, you can put them in a **transaction**:

```text
BEGIN

Delete user 87

Create audit record

COMMIT
```

If something fails:

```text
ROLLBACK
```

---

# Audit log vs logging

A simple comparison:

| Application Log                   | Audit Log             |                        |
| --------------------------------- | --------------------- | ---------------------- |
| Main purpose                      | Debug/monitor         | Accountability/history |
| Example                           | Database query failed | Admin deleted user     |
| Usually temporary?                | Often                 | Usually long-lived     |
| Important history?                | Not necessarily       | Yes                    |
| Who did it?                       | Sometimes             | Usually                |
| Append-only?                      | Not necessarily       | Commonly               |
| Used for security investigations? | Sometimes             | Very often             |

---

## One important rule

Don't confuse:

```text
"Something happened"
```

with:

```text
"Someone performed an important action"
```

For example:

```text
INFO: GET /api/tasks took 200ms
```

→ **application log**

But:

```text
User 42 assigned Task 15 to User 87
```

→ **audit log**

A good mental model is:

> **Logs tell you what the system was doing. Audit logs tell you what important actions people/systems performed.**


---
[[Back-End]]
[[My-Journey-In-Codeless]]