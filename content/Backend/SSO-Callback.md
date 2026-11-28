---
title: SSO Callback
publish: true
date created: 2026-11-25
tags:
  - backend
---
## **What is an SSO Callback?**

**SSO (Single Sign-On)** allows users to log in to multiple applications using one authentication provider, such as Google, Microsoft, or an organization's identity provider.

An **SSO Callback** is a URL in your application where the authentication provider redirects the user after the login process.

Your application uses this callback to receive the authentication response and complete the login.

### **How does it work?**

Imagine you're logging in to an application using your Google account.

1. You click **Sign in with Google**.
    
2. Your application redirects you to Google's login page.
    
3. You enter your Google credentials.
    
4. Google authenticates you.
    
5. Google redirects you back to your application's callback URL.
    
6. Your application validates the authentication response and creates a login session.
    

### **Example**

Your application might register this callback URL with Google:

```
https://myapp.com/auth/callback
```

After successful authentication, Google redirects the browser to that URL, typically with an authorization code:

```
https://myapp.com/auth/callback?code=abc123
```

Your backend receives the code and exchanges it for tokens through the authentication provider.

### **Why is it needed?**

The callback allows your application to:

- Receive the authentication response.
    
- Verify the user's identity.
    
- Obtain authentication tokens.
    
- Create a user session.
    
- Redirect the user to the application after login.
    

### **Important concepts**

|Term|Meaning|
|---|---|
|SSO|Single Sign-On|
|Identity Provider (IdP)|Service responsible for authenticating users|
|Callback URL|Where the user is redirected after authentication|
|Authorization Code|Temporary code exchanged for tokens|
|Access Token|Credential used to access protected resources|
|Session|Maintains the user's authenticated state|

**In simple terms:** An SSO callback is the endpoint where your application receives the response from an identity provider after a user attempts to log in. It allows your application to complete the authentication process.