---
title: Cookie
publish: true
date created: 2026-11-25
tags:
  - backend
  - Sah
---
## **What is a Cookie?**

A **cookie** is a small piece of data that a website stores in your browser (Chrome, Firefox, etc.) to remember information about you or your interaction with the website.

Since HTTP is a **stateless protocol**, the server doesn't automatically remember previous requests. Cookies help websites maintain information between requests.

### **What are cookies used for?**

- **Authentication:** Remember that you're logged in.
    
- **Session management:** Identify your current session.
    
- **Preferences:** Remember your language, theme, or settings.
    
- **Shopping carts:** Remember items you've added.
    

### **What is a Session Cookie?**

A **session** represents a period of interaction between a user and an application.

A **Session Cookie** typically stores a unique `Session ID` that allows the server to recognize a user across multiple HTTP requests.

**How it works:**

1. You log in to a website.
    
2. The server validates your credentials and creates a session.
    
3. The server generates a unique `Session ID`.
    
4. The browser stores that ID in a cookie.
    
5. With subsequent requests, the browser sends the cookie to the server.
    
6. The server uses the ID to retrieve the user's session information.
    

Example:

```
Set-Cookie: session_id=abc123xyz
```

The browser sends it with subsequent requests:

```
Cookie: session_id=abc123xyz
```

### **Where is the session information stored?**

Usually, the browser stores the Session ID, while the actual session information is stored on the server.

For example:

- **Browser:** `session_id = abc123xyz`
    
- **Server (Redis, PostgreSQL, etc.):** Session ID, user ID, login status, and other session data.
    

### **Cookie vs. Session**

|Cookie|Session|
|---|---|
|Stored in the browser|Usually managed on the server|
|Can contain data or an identifier|Represents a user's interaction state|
|Can be temporary or persistent|Has its own expiration rules|
|Sent with HTTP requests|Retrieved using a session identifier|

**Important:** Cookies and sessions are not the same thing. A cookie is one mechanism for identifying and maintaining a session.

### **Cookie vs. Session Cookie**

- **Cookie:** General term for data stored in the browser.
    
- **Session Cookie:** A cookie without an explicit expiration date, typically removed when the browser session ends.
    

_Note: Closing the browser doesn't necessarily destroy the server-side session. These are two separate things._


### Cookie(HttpOnly; Secure; SameSite=Lax).

This describes a cookie with three **security attributes**: `HttpOnly`, `Secure`, and `SameSite=Lax`.

These attributes control how the browser handles and protects the cookie.

### **1.** `HttpOnly`

Prevents JavaScript running in the browser from accessing the cookie through `document.cookie`.

**Why?** It helps protect sensitive cookies, such as session cookies, from being stolen through certain Cross-Site Scripting (XSS) attacks.

### **2.** `Secure`

The browser sends the cookie only over **HTTPS** connections, not ordinary HTTP connections.

**Why?** It helps prevent the cookie from being exposed through unencrypted network traffic.

### **3.** `SameSite=Lax`

Controls when the browser sends the cookie with requests originating from other websites.

With `Lax`:

- The cookie is generally sent with requests within the same site.
    
- It is generally sent when a user navigates to your website through a normal cross-site link (top-level GET navigation).
    
- It is generally NOT sent with cross-site POST requests or embedded cross-site resources.
    

**Why?** It helps protect against Cross-Site Request Forgery (CSRF) attacks.

### **Example**

A server might send this HTTP header:

```
Set-Cookie: session_id=abc123;
            HttpOnly;
            Secure;
            SameSite=Lax
```

This means:

|Attribute|Purpose|
|---|---|
|`HttpOnly`|JavaScript cannot read the cookie|
|`Secure`|Cookie is sent only over HTTPS|
|`SameSite=Lax`|Restricts sending cookies in cross-site requests|

**In simple terms:** These three attributes make a session cookie safer by limiting who can access it, how it is transmitted, and when the browser sends it.

One important distinction: These attributes improve cookie security, but they don't guarantee complete protection against XSS, CSRF, or session hijacking.

---
[[Backend]]