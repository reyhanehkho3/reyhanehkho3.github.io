---
title: Idel-Timeout
publish: true
date created: 2026-11-25
tags:
  - backend
  - Sah
---
## **What is Idle Timeout?**

**Idle Timeout** is the amount of time a system allows a user to remain inactive before automatically ending their session or requiring them to authenticate again.

It's commonly used in websites, applications, and banking systems for security purposes.

### **How does it work?**

Imagine you're logged in to an application:

1. You log in successfully.
    
2. You stop interacting with the application.
    
3. The application starts counting your inactivity time.
    
4. If you remain inactive for the configured period (e.g., 15 minutes), your session expires.
    
5. You must log in again to continue.
    

### **Example**

Suppose an application has an Idle Timeout of 15 minutes.

|User activity|Result|
|---|---|
|Logs in at 10:00|Session starts|
|Last activity at 10:05|Inactivity timer resets|
|No activity until 10:20|15 minutes inactive|
|At 10:20|Session expires|

### **Why is Idle Timeout important?**

- **Security:** Prevents someone else from using an unattended, logged-in device.
    
- **Session management:** Automatically expires inactive sessions.
    
- **Data protection:** Reduces the risk of unauthorized access to sensitive information.
    

### **Idle Timeout vs. Session Timeout**

|Idle Timeout|Session Timeout|
|---|---|
|Based on user inactivity|Based on session lifetime|
|Resets when qualifying activity occurs|May expire regardless of user activity|
|Example: 15 minutes without activity|Example: Session expires after 8 hours|

**In simple terms:** Idle Timeout is the maximum amount of time a user can remain inactive before the application automatically expires their session.


---
[[Backend]]