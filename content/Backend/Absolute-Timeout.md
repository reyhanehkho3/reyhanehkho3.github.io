---
title: Absolute Timeout
publish: true
date created: 2026-11-25
tags:
  - backend
  - Sah
---
## **What is Absolute Timeout (Max Session Lifetime)?**

**Absolute Timeout**, also called **Maximum Session Lifetime**, is the maximum amount of time a session can remain valid, regardless of whether the user is active or inactive.

Once this time expires, the user must authenticate again.

### **How does it work?**

Imagine an application has an Absolute Timeout of 8 hours.

1. You log in at 09:00.
    
2. You actively use the application throughout the day.
    
3. Your activity does not reset the absolute timeout.
    
4. At 17:00, your session expires.
    
5. You must log in again.
    

### **Example**

|Time|Activity|Result|
|---|---|---|
|09:00|User logs in|Session starts|
|11:00|User is active|Session remains valid|
|14:00|User is active|Session remains valid|
|16:30|User is active|Session remains valid|
|17:00|8 hours have passed|Session expires|

### **Absolute Timeout vs. Idle Timeout**

|Idle Timeout|Absolute Timeout|
|---|---|
|Based on inactivity|Based on total session lifetime|
|Resets after qualifying activity|Does not reset with activity|
|Example: 15 minutes|Example: 8 hours|
|Prevents misuse of unattended sessions|Limits how long a session can remain valid|

### **Why is it important?**

- **Security:** Limits the lifetime of potentially compromised sessions.
    
- **Access control:** Requires users to periodically re-authenticate.
    
- **Risk reduction:** Prevents sessions from remaining valid indefinitely.
    

**In simple terms:** Idle Timeout expires your session when you stop using the application. Absolute Timeout expires your session after a fixed amount of time, even if you're actively using it.


---
[[Backend]]