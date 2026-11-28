---
title: OAuth
publish:
date created: 2026-11-28
tags:
  - Sah
  - backend
---
# **What is OAuth?**

**OAuth (Open Authorization)** is an authorization framework that allows an application to access another service's resources without needing the user's password.

In simple terms, it lets you give an application permission to access certain information or perform certain actions on your behalf.

## **1. Why do we need OAuth?**

Imagine you have a Google account and use a third-party application that wants to access your Google Calendar.

Without OAuth, the application might ask for your Google password.

This is dangerous because:

- The application would have access to your password.
    
- It might access more information than necessary.
    
- You would have to change your password to revoke its access.
    

OAuth solves this problem.

Instead, Google can give the application a limited permission to access your calendar.

## **2. How does OAuth work?**

Imagine you want to use an application that needs access to your Google Calendar.

1. You click **Connect Google Calendar**.
    
2. The application redirects you to Google.
    
3. Google asks you to log in (if necessary).
    
4. Google asks whether you allow the application to access your calendar.
    
5. You approve the request.
    
6. Google gives the application an Access Token.
    
7. The application uses that token to access your calendar.
    

The important point is that **the application never needs your Google password**.

## **3. What is an Access Token?**

An Access Token is a credential that allows an application to access a protected resource.

For example:

```
Access Token: abc123xyz
```

The application sends this token when making an API request:

```
GET /calendar/events
Authorization: Bearer abc123xyz
```

The server checks the token and determines whether the application has permission to access the requested resource.

## **4. Important OAuth terminology**

|Term|Meaning|
|---|---|
|Resource Owner|The user who owns the data.|
|Client|The application requesting access.|
|Authorization Server|The server that authenticates the user and issues tokens.|
|Resource Server|The server hosting the protected resources (e.g. Google Calendar API).|
|Access Token|Credential used to access protected resources.|
|Scope|Defines what permissions the application requests.|
|Consent|User's approval of the requested permissions.|

## **5. What is the difference between OAuth and OIDC?**

This is probably the most important distinction.

| OAuth 2.0                           | OIDC                             |
| ----------------------------------- | -------------------------------- |
| Authorization                       | Authentication                   |
| What can this application access?   | Who is this user?                |
| Uses Access Tokens                  | Uses ID Tokens and Access Tokens |
| Does not define user authentication | Adds an authentication layer     |

For example:

- **OAuth:** Allow this application to read your Google Calendar.
    
- **OIDC:** Verify that you are the owner of this Google account.
    

## **6. How are they related?**

Think of it this way:

- OAuth 2.0 provides a way to grant applications access to resources.
    
- OIDC builds on OAuth 2.0 to provide user authentication.
    

**In simple terms:**

OAuth answers: _What is this application allowed to do?_

OIDC answers: _Who is the user?_



---
[[Backend]]