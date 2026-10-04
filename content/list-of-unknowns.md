---
title: List of Unknowns
publish: true
date created: 2026-09-10
tags:
---

# 1. Frontend

The frontend is the application the user interacts with.
### Core concepts

- HTML

- CSS

- [[JavaScript/JavaScript|JavaScript]]


- [[JavaScript/TypeScript|TypeScript]]


- DOM

- Browser

- Event

- Event handler

- [[Frontend/Component|Component]]


- State

- Props

- [[Frontend/Routing&Navigation|Routing]]


- [[Frontend/Forms&Validation|Form handling]]


- Client-side validation

- Client-side rendering

- SPA

- SSR

- CSR

### API communication

- [[Frontend/fetch-library|`fetch`]]


- Axios

- HTTP client

- Request

- Response

- JSON

- API client

- Loading state

- Error state

### Later

- [[Frontend/Vue|Vue]]


- [[JavaScript/React|React]]


- [[Frontend/Pinia|Pinia]] / state management

- [[Back-End/WebSocket|WebSockets]]


- Service workers

- Browser storage

- Cookies

- CORS

- SSG

---

# 2. HTTP

This is the **communication protocol** between frontend and backend.

### Core

- [[Network/HTTP|HTTP]]


- [[Back-End/HTTP-HTTPS-SSL|HTTPS]]


- Request

- Response

- Client

- Server

- URL

- URI

- HTTP method

- HTTP version

### Methods

- GET

- POST

- PUT

- PATCH

- DELETE

- HEAD

- OPTIONS

### Request

- URL

- Path

- Path parameter

- Query parameter

- Request body

- Header

- Cookie

- Authorization header

- Content-Type
    
- Accept
    

### Response

- Status code
    
- Response body
    
- Response headers
    
- Content-Type
    
- Set-Cookie
    

### Status codes

Learn these first:

```text
200 OK
201 Created
204 No Content

400 Bad Request
401 Unauthorized
403 Forbidden
404 Not Found
409 Conflict
422 Unprocessable Content

500 Internal Server Error
502 Bad Gateway
503 Service Unavailable
```

### Important later

- HTTP caching
    
- Cache-Control
    
- ETag
    
- Keep-Alive
    
- Compression
    
- Content negotiation
    
- HTTP/2
    
- HTTP/3
    
- [[Back-End/HTTP-HTTPS-SSL|TLS]]

    
- Connection pooling
    

---

# 3. API

This is the **interface/contract** that the backend exposes.

### Core

- [[Back-End/API|API]]

    
- API endpoint
    
- API route
    
- Resource
    
- Request
    
- Response
    
- API contract
    
- API design
    
- API versioning
    

### REST

- [[Back-End/REST-API|REST]]

    
- [[Back-End/REST-API|RESTful API]]

    
- Resource-oriented design
    
- [[Database/CRUD-Methods|CRUD]]

    
- Statelessness
    
- Resource representation
    

For example:

```text
GET    /users
GET    /users/42
POST   /users
PATCH  /users/42
DELETE /users/42
```

### API documentation

- OpenAPI
    
- Swagger
    
- Swagger UI
    
- API schema
    
- API specification
    
- Request schema
    
- Response schema
    

### Later

- GraphQL
    
- gRPC
    
- WebSocket API
    
- Webhooks
    
- [[Back-End/API-GW|API Gateway]]

    
- API versioning
    
- [[Back-End/Rate-Limiting|Rate limiting]]

    
- Pagination
    
- Filtering
    
- Sorting
    
- Searching
    

---

# 4. Backend / Server

This is where your application actually **processes requests and makes decisions**.

### Core

- Backend
    
- Server
    
- Application server
    
- Runtime
    
- Process
    
- Port
    
- Route
    
- Router

    
- Controller
    
- Service
    
- Repository
    
- Business logic
    

### Express concepts

Since you're working with Express, learn:

- [[JavaScript/Express|Express]]

    
- `app`
    
- Router

    
- Route handler
    
- `req`
    
- `res`
    
- `next`
    
- [[Back-End/Middleware|Middleware]]

    
- Error middleware
    
- `express.json()`
    

Example:

```js
app.get("/api/tasks", authenticate, getTasks);
```

Learn to identify:

```text
app
 ↓
route
 ↓
middleware
 ↓
controller
 ↓
service
```

---

# 5. Middleware

Middleware is code that runs during the request pipeline.

Learn:

- [[Back-End/Middleware|Middleware]]

    
- Global middleware
    
- Route middleware
    
- Authentication middleware
    
- Authorization middleware
    
- Validation middleware
    
- Logging middleware
    
- Error-handling middleware
    
- `next()`
    
- Middleware chain
    

Mental model:

```text
Request
   ↓
Logger
   ↓
Authentication
   ↓
Authorization
   ↓
Validation
   ↓
Controller
   ↓
Response
```

---

# 6. Backend Logic / Business Logic

This is one of the **most important areas** to understand.

Learn:

- Business logic
    
- Business rules
    
- Domain logic
    
- Use case
    
- Invariant
    
- State
    
- State transition
    
- Preconditions
    
- Postconditions
    
- Decision logic
    
- Validation
    
- Authorization rules
    

For example:

```text
USER
 ↓
tries to delete task
 ↓
Is user authenticated?
 ↓
Does user own the task?
 ↓
Does user have permission?
 ↓
Delete task
```

The rules determining what happens are business logic.

---

# 7. Controllers

Controllers connect HTTP to your application logic.

Learn:

- Controller
    
- Controller function
    
- Request parsing
    
- Response formatting
    
- HTTP status handling
    
- [[Database/dto|DTO]]

    
- Serialization
    
- Deserialization
    

Typical flow:

```text
HTTP Request
     ↓
Controller
     ↓
Service
     ↓
Controller
     ↓
HTTP Response
```

A controller generally shouldn't contain your entire business logic.

---

# 8. Services

Services usually contain application/business operations.

Learn:

- Service
    
- Service layer
    
- Use case
    
- Business operation
    
- [[Back-End/Domain-Service|Domain service]]

    
- Dependency
    
- Dependency injection
    

For example:

```js
taskService.createTask(...)
taskService.assignTask(...)
taskService.deleteTask(...)
```

Think:

> "What does the application need to do?"

---

# 9. Database

This is where persistent data lives.

### Core

- [[Database/Database|Database]]

    
- Database server
    
- Database connection
    
- Table
    
- Row
    
- Column
    
- Record
    
- Primary key
    
- Foreign key
    
- Constraint
    
- Index

    
- Query
    

### SQL

Learn:

```text
SELECT
INSERT
UPDATE
DELETE

WHERE
JOIN
ORDER BY
GROUP BY
HAVING

LIMIT
OFFSET
```

### PostgreSQL

Since you're using PostgreSQL:

- [[Database/PostgreSQL|PostgreSQL]]

    
- Schema
    
- Table
    
- Sequence
    
- UUID
    
- [[Database/Atomic-Transaction|Transaction]]

    
- Connection pool
    
- [[Python/Migration|Migration]]

    
- PostgreSQL constraint
    

---

# 10. Database relationships

Learn:

- One-to-one
    
- One-to-many
    
- Many-to-many
    
- Foreign key
    
- Join table
    
- Referential integrity
    
- Cascade
    
- [[Database/Normalization|Normalization]]

    
- [[Database/Denormalization|Denormalization]]

    

Example:

```text
Project
   │
   ├── Task
   ├── Task
   └── Task
```

That's a one-to-many relationship.

---

# 11. ORM / Data Access

If you use Prisma:

- [[Database/ORM|ORM]]

    
- [[Database/Prisma|Prisma]]

    
- Prisma Client
    
- Model
    
- [[Python/Migration|Migration]]

    
- Repository
    
- Query
    
- [[Database/CRUD-Methods|CRUD]]

    
- Relation
    
- [[Database/Atomic-Transaction|Transaction]]

    

Understand the distinction:

```text
Service
   ↓
Repository / Prisma
   ↓
SQL
   ↓
PostgreSQL
```

---

# 12. Authentication

This answers:

> **Who is this user?**

Learn:

- Authentication
    
- Login
    
- Logout
    
- Registration
    
- Credentials
    
- Password hashing
    
- Password verification
    
- Session

    
- Token
    
- Access token
    
- Refresh token
    
- [[Back-End/JWT|JWT]]

    
- JWT claims
    
- Token expiration
    
- Token rotation
    

### Password security

- Hashing
    
- Salt
    
- Argon2
    
- bcrypt
    
- Password storage
    
- Password verification
    

---

# 13. Authorization

This answers:

> **What is this user allowed to do?**

Learn:

- Authorization
    
- Permission
    
- Role

    
- RBAC
    
- ABAC
    
- Access control
    
- Resource ownership
    
- Policy
    
- Privilege
    
- Least privilege
    

Example:

```text
USER
 └── view assigned tasks

ADMIN
 ├── create tasks
 └── delete tasks

SUPERADMIN
 ├── manage users
 └── manage admins
```

---

# 14. Validation

Learn both **input validation** and **business validation**.

### Input validation

- Required field
    
- Data type
    
- String length
    
- Format
    
- Range
    
- Schema validation
    
- Sanitization
    

Tools/concepts:

- express-validator
    
- [[Back-End/Zod|Zod]]

    
- Joi
    
- JSON Schema
    

Example:

```json
{
  "title": "Learn APIs"
}
```

Backend asks:

```text
Is title present?
Is it a string?
Is it too long?
Is it allowed?
```

---

# 15. Error handling

Learn:

- Error
    
- Exception
    
- Error propagation
    
- Error middleware
    
- Error response
    
- Error code
    
- Error type
    
- Custom error
    
- Global error handler
    

Typical architecture:

```text
Service
   ↓
throws error
   ↓
Controller
   ↓
Express error middleware
   ↓
HTTP error response
```

For example:

```text
NotFoundError
      ↓
404
```

```text
ForbiddenError
      ↓
403
```

---

# 16. Transactions & Data Integrity

This is where backend development starts becoming more interesting.

Learn:

- [[Database/Atomic-Transaction|Transaction]]

    
- [[Database/ACID|ACID]]

    
- Atomicity
    
- [[Database/Consistency|Consistency]]

    
- [[Database/Isolation|Isolation]]

    
- [[Database/Durability|Durability]]

    
- COMMIT
    
- ROLLBACK
    
- [[Database/Isolation-Level|Isolation level]]

    
- Lock
    
- [[Database/Race-Condition|Race condition]]

    
- Deadlock
    
- Concurrency
    
- Optimistic locking
    
- Pessimistic locking
    

Example:

```text
Create order
     +
Decrease inventory
     ↓
Transaction
     ↓
Both succeed
OR
both rollback
```

---

# 17. Security

Learn these gradually:

### Web security

- [[Back-End/HTTP-HTTPS-SSL|HTTPS]]

    
- [[Back-End/HTTP-HTTPS-SSL|TLS]]

    
- CORS
    
- CSRF
    
- XSS
    
- SQL injection
    
- Clickjacking
    
- Session security
    
- Cookie security
    

### API security

- Authentication
    
- Authorization
    
- [[Back-End/Rate-Limiting|Rate limiting]]

    
- Input validation
    
- Password hashing
    
- Token security
    
- Secrets
    
- API keys
    
- Environment variables
    

### Important HTTP cookie concepts

- HttpOnly
    
- Secure
    
- SameSite
    
- Domain
    
- Path
    
- Cookie expiration
    

---

# 18. Caching

Learn:

- [[Database/Cache|Cache]]

    
- Cache hit
    
- Cache miss
    
- Cache invalidation
    
- [[Database/TTL|TTL]]

    
- [[Database/Redis|Redis]]

    
- In-memory cache
    
- Distributed cache
    
- Cache-aside
    
- Write-through
    
- Write-back
    

Typical flow:

```text
Request
   ↓
Cache?
 ┌─┴──┐
Yes   No
 ↓     ↓
Return Database
       ↓
      Cache
```

---

# 19. Queues & Background Jobs

Useful for things that don't need to happen during the HTTP request.

Learn:

- Message
    
- Queue
    
- Producer
    
- Consumer
    
- Worker
    
- Job
    
- Background job
    
- Message broker
    
- RabbitMQ
    
- Retry
    
- Backoff
    
- Dead-letter queue
    
- DLQ
    
- Acknowledgement
    
- [[Database/Idempotency|Idempotency]]

    

Example:

```text
API
 ↓
RabbitMQ
 ↓
Worker
 ↓
Send notification
```

---

# 20. Reliability

Learn:

- Retry
    
- Timeout
    
- Backoff
    
- Exponential backoff
    
- Jitter
    
- Circuit breaker
    
- Failover
    
- Health check
    
- Graceful shutdown
    
- [[Database/Idempotency|Idempotency]]

    
- Fault tolerance
    
- [[Back-End/Availability|Availability]]

    

These concepts answer:

> "What happens when something goes wrong?"

---

# 21. Logging & Observability

Learn:

- Logging
    
- [[Back-End/Log-Levels|Log level]]

    
- DEBUG
    
- INFO
    
- WARN
    
- ERROR
    
- Structured logging
    
- Request ID
    
- Correlation ID
    
- [[Back-End/Metrics|Metrics]]

    
- [[Back-End/Trace|Tracing]]

    
- Monitoring
    
- [[Back-End/Observability|Observability]]

    
- Health check
    
- Alerting
    

The three major pillars:

```text
Observability
 ├── Logs
 ├── Metrics
 └── Traces
```

---

# 22. Testing

Learn:

### Unit testing

Tests one piece of logic.

```text
taskService.createTask()
```

### Integration testing

Tests multiple components together.

```text
API → Service → Database
```

### API testing

Tools:

- Postman
    
- Bruno
    
- Supertest
    

### Other terms

- Test case
    
- Test suite
    
- Assertion
    
- Mock
    
- Stub
    
- Fixture
    
- Test database
    
- Integration test
    
- End-to-end test
    
- Regression test
    

---

# 23. API performance

Later, learn:

- Latency
    
- Throughput
    
- Requests per second
    
- Response time
    
- Bottleneck
    
- Load
    
- Load testing
    
- Connection pooling
    
- Database indexing
    
- N+1 query problem
    
- Pagination
    
- Caching
    
- Compression
    

---

# 24. Architecture

Once you understand the individual pieces, learn how they fit together.

### Basic architecture

```text
Route
  ↓
Controller
  ↓
Service
  ↓
Repository
  ↓
Database
```

### Layered architecture

- Presentation layer
    
- API layer
    
- Application layer
    
- Domain layer
    
- Data access layer
    
- Infrastructure layer
    

### Other architectures

- [[Back-End/Monolithic-Architecture|Monolith]]

    
- Modular monolith
    
- [[Back-End/Microservice-Architecture|Microservices]]

    
- Event-driven architecture
    
- Hexagonal architecture
    
- Clean architecture
    
- [[Back-End/MVC|MVC]]

    

For your current projects, **layered architecture + modular monolith** is a very good place to focus before worrying about microservices.

---

# 25. The concepts I'd learn FIRST

Don't try to learn all of this at once.

I'd use this order:

### Phase 1 — Web fundamentals

```text
HTTP
URL
Request
Response
Headers
Body
HTTP methods
Status codes
JSON
HTTPS
```

### Phase 2 — APIs

```text
API
Endpoint
REST
CRUD
Route
Path parameters
Query parameters
Request body
API contract
OpenAPI
Swagger
```

### Phase 3 — Express

```text
Express
Router
Route handler
Middleware
req
res
next
Controller
Error middleware
```

### Phase 4 — Backend logic

```text
Business logic
Business rules
Service
Use case
Validation
Error handling
Invariants
State
```

### Phase 5 — Database

```text
SQL
PostgreSQL
Table
Row
Column
Primary key
Foreign key
Relationship
Index
Constraint
Migration
ORM
Prisma
```

### Phase 6 — Security

```text
Authentication
Authorization
Password hashing
JWT
Access token
Refresh token
RBAC
Permissions
CORS
CSRF
XSS
SQL injection
```

### Phase 7 — Reliability

```text
Transaction
ACID
Concurrency
Race condition
Idempotency
Retry
Timeout
Queue
Worker
Caching
```

### Phase 8 — Production

```text
Logging
Monitoring
Metrics
Tracing
Observability
Health checks
Rate limiting
Performance
Load testing
Deployment
CI/CD
```

---

## And the entire picture

Eventually, you should be able to look at this:

```text
                         FRONTEND
                            │
                            │
                       HTTP Request
                            │
                            ▼
                    ┌───────────────┐
                    │      API      │
                    │   Endpoints   │
                    └───────┬───────┘
                            │
                       Middleware
                     ┌──────┼──────┐
                     │      │      │
                 Auth    AuthZ   Validation
                     │      │      │
                     └──────┼──────┘
                            │
                       Controller
                            │
                         Service
                            │
                    Business Logic
                            │
                 ┌──────────┴──────────┐
                 │                     │
            Repository              Queue
                 │                     │
                 ▼                     ▼
             Database               Worker
                 │
                 ▼
            PostgreSQL
                 │
                 ▼
              Response
                 │
                 ▼
              FRONTEND
```

and understand **what every box means, why it exists, and what problem it solves**.

That's a very solid backend/API foundation.