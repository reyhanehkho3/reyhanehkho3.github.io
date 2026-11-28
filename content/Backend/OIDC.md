---
title: OICD
publish: true
date created: 2026-11-28
tags:
  - Sah
  - backend
---
# **What is OIDC?**

**OIDC (OpenID Connect)** is an authentication protocol built on top of **OAuth 2.0**.

It allows an application to verify a user's identity without implementing its own authentication system.

For example:

- Sign in with Google
    
- Sign in with Microsoft
    
- Sign in with GitHub
    

These services can use OIDC.

## **1. Why do we need OIDC?**

Imagine you are developing a web application.

You need to:

- Authenticate users.
    
- Verify their identities.
    
- Manage login sessions.
    
- Handle user information.
    

Instead of implementing authentication yourself, you can use an **Identity Provider (IdP)** such as Google or Keycloak.

OIDC defines how your application communicates with that provider.

## **2. How does OIDC work?**

Imagine a user wants to log in to your application using Google.

1. The user clicks **Sign in with Google**.
    
2. Your application redirects the user to Google.
    
3. Google authenticates the user.
    
4. Google sends the user back to your application with an authorization code.
    
5. Your application exchanges that code for tokens.
    
6. Your application validates the ID Token and identifies the user.
    
7. The user is logged in.
    

## **3. What are OIDC tokens?**

OIDC uses different types of tokens:

|Token|Purpose|
|---|---|
|ID Token|Contains information about the authenticated user.|
|Access Token|Allows access to protected resources or APIs.|
|Refresh Token|Allows the application to obtain new tokens without asking the user to log in again.|

The most important token specific to OIDC is the **ID Token**.

It usually contains information such as:

```
{
  "iss": "https://accounts.google.com",
  "sub": "123456789",
  "email": "user@example.com",
  "name": "John Doe",
  "aud": "my-application",
  "exp": 1795860000
}
```

Some important fields:

- `iss`: Who issued the token.
    
- `sub`: Unique identifier of the user.
    
- `email`: User's email address.
    
- `aud`: Intended recipient of the token.
    
- `exp`: Token expiration time.
    

## **4. OIDC vs OAuth 2.0**

Both are related, but they have different purposes.

|OAuth 2.0|OIDC|
|---|---|
|Authorization|Authentication|
|Determines what an application can access.|Determines who the user is.|
|Provides Access Tokens.|Provides ID Tokens and Access Tokens.|

**Example:**

- OAuth 2.0: Allow an application to access your Google Calendar.
    
- OIDC: Verify that you are the person who owns a Google account.
    

OIDC extends OAuth 2.0 by adding an authentication layer.

## **5. Where does Keycloak fit in?**

**Keycloak** is an Identity Provider (IdP) that supports OIDC.

You can use it to:

- Manage users.
    
- Authenticate users.
    
- Issue ID Tokens and Access Tokens.
    
- Manage roles and permissions.
    
- Provide Single Sign-On (SSO).
    

Your application delegates authentication to Keycloak instead of handling passwords itself.

## **6. Important terminology**

|Term|Meaning|
|---|---|
|OIDC|Authentication protocol|
|OAuth 2.0|Authorization framework|
|IdP|Identity Provider|
|Client|Application requesting authentication|
|ID Token|Contains information about the authenticated user|
|SSO|Single Sign-On|
|Claims|Information contained in a token|
|Scope|Specifies what information or access is requested|

**In simple terms:** OIDC allows your application to use an external service (such as Google or Keycloak) to authenticate users and verify their identities.



---
[[Backend]]