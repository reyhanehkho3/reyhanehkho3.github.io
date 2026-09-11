---
title: Test
publish: true
date created: 2026-09-11
tags:
  - Backend
  - test
  - codeless
---
There are many types of tests in software development. The easiest way to understand them is by looking at **what part of the system they test**.

A common hierarchy is:

```text
                 Tests
                   |
    ┌──────────────┼──────────────┐
    ↓              ↓              ↓
 Unit Tests   Integration    End-to-End
                  Tests          Tests
```

---

# 1. Unit Test

A **unit test** tests the smallest piece of code independently.

A unit test might be weak because it only checks a part and maybe there is something else that is causing the bug on that part and the unit test wouldn't know.

Usually:

- a function
    
- a class
    
- a method
    
- a component
    

The goal:

> "Does this small piece of logic work correctly?"

### Example

You have:

```js
function calculateTotal(price, tax) {
    return price + tax;
}
```

Unit test:

```js
expect(calculateTotal(100, 10))
    .toBe(110);
```

You are not testing:

- database
    
- API
    
- frontend
    
- network
    

Only the function.

### Backend example

Service:

```js
function isAdmin(user) {
    return user.role === "ADMIN";
}
```

Test:

```text
Input:
{
 role: "ADMIN"
}

Expected:
true
```

### Advantages

✅ Fast  
✅ Easy to debug  
✅ Finds logic bugs early

### Disadvantages

❌ Does not prove the whole system works

---

# 2. Integration Test

An **integration test** checks whether multiple parts work together.

Example:

```text
Controller
    ↓
Service
    ↓
Database
```

You test the connection between them.

---

Example:

Your API:

```http
POST /users
```

Integration test:

```text
Send request
      ↓
Controller receives it
      ↓
Service creates user
      ↓
Database stores user
      ↓
Response returns
```

Expected:

```json
{
 "id": 1,
 "username": "reyhan"
}
```

You are testing:

- routes
    
- middleware
    
- services
    
- database interaction
    

---

### Example tools

Backend:

- Supertest
    
- Jest
    
- pytest
    

Frontend:

- React Testing Library
    
- Vue Test Utils
    

---

# 3. End-to-End (E2E) Test

An E2E test tests the entire system like a real user.

It starts from the UI.

Example:

User registration:

```text
Browser
   ↓
Open website
   ↓
Fill registration form
   ↓
Click Register
   ↓
Frontend sends API request
   ↓
Backend creates user
   ↓
Database saves user
   ↓
User sees dashboard
```

The test checks the whole journey.

Example:

```text
Open /register

Type:
email=test@test.com
password=123456

Click submit

Expect:
Dashboard appears
```

Tools:

- Playwright
    
- Cypress
    
- Selenium
    

### Advantages

✅ Tests real user behavior

### Disadvantages

❌ Slow  
❌ More fragile

---

# 4. API Test

Tests your API endpoints directly.

Example:

```http
POST /api/login
```

Test:

Request:

```json
{
 "email": "test@test.com",
 "password": "123"
}
```

Response:

```json
{
 "token": "abc123"
}
```

Checks:

- status codes
    
- response format
    
- authentication
    
- validation
    

Tools:

- Postman
    
- Bruno
    
- Supertest
    

---

# 5. Component Test (Frontend)

Tests a UI component independently.

Example:

Component:

```jsx
<Button text="Save" />
```

Test:

```text
Render button

Click button

Expect:
onClick called
```

You don't test the whole application.

Tools:

- React Testing Library
    
- Vue Test Utils
    

---

# 6. Regression Test

A **regression test** checks that old functionality still works after changes.

Example:

You add:

```text
Feature:
Allow users to upload images
```

A bug appears:

```text
Login no longer works
```

You fix it and add a regression test:

```text
Login should always work
```

Later changes cannot break it silently.

Think:

> "We had this bug before. Make sure it never comes back."

---

# 7. Smoke Test

A smoke test checks if the basic system works.

Usually after deployment.

Example:

After deploying:

```text
✓ Website opens
✓ API responds
✓ Database connects
✓ Login works
```

It answers:

> "Is the system alive?"

Not:

> "Is every feature perfect?"

---

# 8. Sanity Test

Similar to smoke testing, but more focused.

Example:

You fix:

```text
Task creation bug
```

Sanity test:

```text
✓ Create task works
✓ Task appears in list
```

You don't test everything.

---

# 9. Performance Test

Checks how the system behaves under load.

Examples:

```text
100 users
1000 users
10000 users
```

Measures:

- response time
    
- throughput
    
- resource usage
    

Example:

```text
GET /tasks

1000 requests/sec

Average response:
120ms
```

Tools:

- k6
    
- JMeter
    
- Gatling
    

---

# 10. Load Test

A type of performance test.

Question:

> "Can the system handle expected traffic?"

Example:

Your app normally has:

```text
500 users/minute
```

Load test:

```text
500 users/minute
```

---

# 11. Stress Test

Pushes the system beyond normal limits.

Question:

> "When does it break?"

Example:

```text
Expected:
10,000 users

Test:
100,000 users
```

You learn:

- breaking point
    
- failure behavior
    
- recovery
    

A **pressure test** is usually another name people use for a **stress test** or **load test**, depending on the context.

In software, a pressure test means:

> **Putting the system under heavy pressure (high traffic, high data volume, or limited resources) to see how it behaves.**

The goal is not only "does it work?" but:

- When does it become slow?
    
- When does it fail?
    
- Does it recover?
    
- Does it lose data?
    
- Does it fail gracefully?
    

---

## Example

Imagine your API normally handles:

```text
1000 requests/minute
```

A pressure test might push it:

```text
5000 requests/minute
10000 requests/minute
50000 requests/minute
```

You observe:

```text
Requests increase
        ↓
Response time increases
        ↓
CPU reaches 100%
        ↓
Errors start appearing
        ↓
System crashes
```

You find the breaking point.

---

## Load test vs stress/pressure test

### Load test

Tests **expected usage**.

Question:

> "Can my system handle normal traffic?"

Example:

```text
Expected users:
10,000

Test:
10,000 users
```

---

### Stress / pressure test

Tests **beyond normal limits**.

Question:

> "How much can my system take before it breaks?"

Example:

```text
Expected users:
10,000

Test:
100,000 users
```

---

## Example for an API

Suppose you have:

```http
POST /api/login
```

Normal:

```text
100 login requests/sec
```

Pressure test:

```text
5000 login requests/sec
```

You measure:

```
Response time:
100ms → 2s → 10s

CPU:
40% → 95%

Errors:
0% → 30%
```

Now you know the limit.

---

## Things pressure tests reveal

### 1. Bottlenecks

Example:

```text
API server
   ↓
Database
   ↓
Database becomes slow
```

The problem is not the API server; it's the database.

---

### 2. Resource limits

Example:

```text
Memory:
4GB → 8GB → 16GB
```

Your app may have a memory leak.

---

### 3. Failure behavior

A good system should fail gracefully:

Bad:

```text
Traffic spike
     ↓
Everything crashes
```

Better:

```text
Traffic spike
     ↓
Some requests rejected
     ↓
System stays alive
```

---

## Related terms

|Term|Meaning|
|---|---|
|Load test|Test expected traffic|
|Stress test|Push beyond expected limits|
|Pressure test|Usually stress test; informal term|
|Spike test|Sudden traffic increase|
|Soak test|Long-duration testing|
|Performance test|General category|

---

For backend/API systems, a common testing progression is:

```text
Unit tests
     ↓
Integration tests
     ↓
API tests
     ↓
E2E tests
     ↓
Load tests
     ↓
Pressure/stress tests
```

So when someone says **"pressure test the system"**, they usually mean:

> "Push it hard and find its limits."


---

# 12. Security Test

Checks vulnerabilities.

Examples:

Testing:

- SQL injection
    
- authentication bypass
    
- authorization problems
    
- XSS
    
- CSRF
    

Example:

Try:

```http
DELETE /users/5
```

as a normal user.

Expected:

```text
403 Forbidden
```

---

# 13. Contract Test

Checks that two services agree on communication.

Example:

Frontend expects:

```json
{
 "username": "reyhan"
}
```

Backend accidentally changes:

```json
{
 "name": "reyhan"
}
```

Contract test catches this.

Common in:

- microservices
    
- APIs
    

---

# 14. Acceptance Test

Checks whether the software satisfies business requirements.

Usually from the user's perspective.

Example requirement:

> "Admin users can delete projects."

Acceptance test:

```text
Given:
User is admin

When:
They delete a project

Then:
Project is removed
```

---

# Summary Table

|Test|Tests|Example|
|---|---|---|
|Unit|Small logic|Function calculation|
|Integration|Parts working together|API + DB|
|E2E|Full user flow|Register → Login → Dashboard|
|API|Backend endpoints|POST /login|
|Component|UI pieces|Button behavior|
|Regression|Old bugs stay fixed|Login remains working|
|Smoke|Basic health|App starts|
|Sanity|Specific fix|Task creation|
|Performance|Speed/capacity|Requests/sec|
|Load|Expected traffic|10k users|
|Stress|Beyond limits|100k users|
|Security|Vulnerabilities|Auth bypass|
|Contract|API agreement|Frontend/backend schema|
|Acceptance|Business requirements|User story works|

For a typical **backend REST API project**, the most important ones to learn first are:

1. **Unit tests**
    
2. **Integration tests**
    
3. **API tests**
    
4. **E2E tests**
    
5. **Regression tests**
    
6. **Performance tests** (later)

---
[[Back-End]]
[[My-Journey-In-Codeless]]
