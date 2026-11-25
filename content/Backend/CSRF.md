---
title: CSRF
publish: true
date created: 2026-11-25
tags:
  - backend
  - Sah
---

## **What is CSRF?**

**CSRF (Cross-Site Request Forgery)** is a web security attack where an attacker tricks a logged-in user into performing an unwanted action on a website without their knowledge.

It takes advantage of the fact that browsers automatically send cookies (including session cookies) with matching requests.

### **How does it work?**

Imagine you're logged in to your bank's website:

1. You log in to `bank.com`. Your browser stores your session cookie.
    
2. You visit another website controlled by an attacker.
    
3. That website secretly sends a request to `bank.com` to transfer money.
    
4. Your browser automatically attaches your bank's session cookie to the request.
    
5. The bank might recognize the session as valid and process the transfer.
    

### **How can CSRF be prevented?**

Common protection mechanisms include:

- **SameSite Cookie:** Restricts when cookies are sent with requests from other websites.
    
- **CSRF Token:** Requires a unique, unpredictable token with sensitive requests.
    
- **Origin/Referer Validation:** Checks where a request originated.
    
- **Custom Headers:** Requires specific HTTP headers for sensitive requests.
    

### **CSRF vs. XSS**

- **CSRF:** Tricks your browser into performing an unwanted action using your authenticated session.
    
- **XSS (Cross-Site Scripting):** Injects malicious JavaScript into a trusted website so it executes in visitors' browsers.
    

**In simple terms:** CSRF exploits your existing login session to perform actions you didn't authorize.

---
[[Backend]]