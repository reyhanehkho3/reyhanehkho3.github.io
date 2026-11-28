---
title: SSO
publish: true
date created: 2026-11-28
tags:
  - Sah
  - backend
---
# What is SSO (Single Sign-On)?

**SSO (Single Sign-On)** is an authentication method that allows you to log in to multiple applications using **one account and one login session**.

Instead of entering your username and password separately for every application, you authenticate once and access multiple applications.

## 1. Example

Imagine your company has three applications:

- Email
- Project Management System
- Internal Dashboard

Without SSO:

- You need separate login credentials for each application.
- You have to log in to each application individually.

With SSO:

- You log in once using your company account.
- You can access all three applications without logging in again.

## 2. How does SSO work?

SSO usually involves three main components:

- **User:** The person trying to log in.
- **Identity Provider (IdP):** The system responsible for authenticating the user.
- **Application (Service Provider):** The application the user wants to access.

### Authentication flow

1. You open Application A.
2. Application A redirects you to the Identity Provider (IdP).
3. You enter your username and password.
4. The IdP verifies your identity.
5. The IdP sends an authentication response (usually a token or assertion) to Application A.
6. You open Application B.
7. Application B trusts the same IdP, so you don't need to log in again.

## 3. Important terms

|Term|Meaning|
|---|---|
|SSO|Single Sign-On; one login for multiple applications|
|IdP|Identity Provider; responsible for authenticating users|
|SP|Service Provider; the application you want to access|
|Authentication|Verifying who you are|
|Authorization|Determining what you are allowed to do|
|Token|Digital information used to communicate authentication or authorization information|

## 4. Technologies used for SSO

SSO is a concept, not a specific protocol. Different protocols can implement it.

|Technology|Purpose|
|---|---|
|SAML 2.0|Commonly used for enterprise SSO|
|OIDC|Authentication protocol built on OAuth 2.0|
|OAuth 2.0|Authorization framework, often used alongside OIDC|

For example:

- Google login uses OIDC.
- Enterprise applications commonly use SAML.
- Keycloak can act as an Identity Provider and support both SAML and OIDC.

## 5. Real-world example

Suppose your company uses Microsoft Entra ID.

You log in once using your company account and can access:

- Microsoft Teams
- Outlook
- SharePoint
- Other company applications

You don't need to enter your password every time because these applications trust the same Identity Provider.

## 6. SSO vs. OAuth vs. OIDC

These concepts are related but different:

- **SSO:** The experience — log in once and access multiple applications.
- **OAuth 2.0:** A framework for granting applications access to resources.
- **OIDC:** An authentication protocol that allows applications to verify a user's identity.

**Key takeaway:** SSO centralizes authentication. Instead of every application managing your login independently, a trusted Identity Provider handles authentication for multiple applications.



---
[[Backend]]