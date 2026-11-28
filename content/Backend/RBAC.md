---
title: RBAC
publish: true
date created: 2026-11-25
tags:
  - backend
  - codeless
---
## **What is RBAC?**

**RBAC (Role-Based Access Control)** is an authorization model that manages access to resources based on a user's assigned role.

Instead of giving permissions to each user individually, permissions are assigned to roles, and users are assigned those roles.

### **How does it work?**

Imagine an application with three types of users:

1. **Admin:** Can manage users, change settings, and access all features.
    
2. **Editor:** Can create, edit, and delete content.
    
3. **Viewer:** Can only view content.
    

Each user receives a role, and that role determines what they are allowed to do.

### **Example**

|Role|Permissions|
|---|---|
|Admin|Read, Create, Update, Delete|
|Editor|Read, Create, Update|
|Viewer|Read|

For example:

```
User: Reyhaneh
Role: Editor

Permissions:
- Read content
- Create content
- Update content
- Cannot delete content
```

### **Important RBAC concepts**

- **User:** The person or account accessing the application.
    
- **Role:** A predefined job or access category.
    
- **Permission:** An allowed action on a resource.
    
- **Resource:** Something the user wants to access, such as a database, API, or file.
    

### **Why use RBAC?**

- **Security:** Prevents unauthorized access.
    
- **Simplicity:** Manage permissions through roles instead of individual users.
    
- **Scalability:** Easier to manage access when an application has many users.
    
- **Maintainability:** Changing a role's permissions updates access for all users assigned to that role.
    

### **RBAC vs. Authentication vs. Authorization**

|Concept|Meaning|
|---|---|
|Authentication|Who are you?|
|Authorization|What are you allowed to do?|
|RBAC|An approach to authorization based on roles.|

**In simple terms:** RBAC determines what users can access or do based on their assigned roles, rather than managing permissions individually for every user.

---
[[Backend]]
[[My-Journey-In-Codeless]]