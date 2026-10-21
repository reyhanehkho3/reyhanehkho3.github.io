---
title: LDAP
publish: true
date created: 2026-10-21
tags:
  - backend
---
LDAP (Lightweight Directory Access Protocol) is a protocol used to access and manage directory information over a network. In companies, it's commonly used to store employee accounts and verify users when they log in.

Think of it as a company-wide phonebook that stores not only names and phone numbers, but also usernames, groups, departments, and other account information.

## 1. Why do companies use LDAP?

Imagine your company has 1,000 employees and several internal systems:

- GitLab
    
- Internal dashboards
    
- Linux servers
    
- Monitoring tools
    
- Company applications
    

Instead of creating a separate username and password for every employee in every system, the company can use a centralized directory.

Company Directory (LDAP)

Employee accounts, groups, and directory information

GitLab

Linux servers

Internal apps

Multiple systems can use the same centralized directory.

## 2. How does LDAP login work?

Suppose you want to log in to an internal company application.

1. You enter your company username and password.
    
2. The application sends an authentication request to an LDAP server.
    
3. The LDAP server checks whether the credentials are valid.
    
4. The application grants or denies access based on the result and its authorization rules.
    

For example, the directory might contain an entry like this:

```
uid=reyhaneh
cn=Reyhaneh Khosravi
department=Engineering
memberOf=Backend-Developers
```

This is a simplified illustration of directory information, not necessarily the exact format your company uses.

The application can use group membership to help decide whether a user is allowed to access a resource.

## 3. LDAP vs. other authentication technologies

|Technology|Main purpose|
|---|---|
|LDAP|Access and manage directory information; can support authentication|
|Active Directory (AD)|Microsoft's directory service, which supports LDAP and other protocols|
|OAuth 2.0|Delegated authorization, such as allowing an app to access another service|
|OpenID Connect (OIDC)|User authentication and identity built on OAuth 2.0|
|JWT|A token format that can carry claims about a user|

Important distinction: LDAP is not the same as JWT. LDAP can verify credentials against a directory, while a backend may issue a JWT after successful login to authenticate subsequent API requests.

## 4. What are LDAP and LDAPS?

- LDAP: Commonly uses port `389`.
    
- LDAPS: LDAP over TLS, commonly uses port `636` to protect the connection with encryption.
    

These are standard ports, although a particular environment may use different configurations.

Never send passwords over an unencrypted LDAP connection across an untrusted network.

## 5. Where might you encounter LDAP?

In a company development environment, LDAP may be involved when:

- You log in to GitLab using your company account.
    
- You access a Linux server with centralized company credentials.
    
- An internal application authenticates employees against a company directory.
    
- IT manages users and groups centrally.
    

One final distinction: LDAP itself doesn't automatically give you single sign-on (SSO). It can be part of an authentication system, while SSO is typically provided through an identity provider such as Active Directory Federation Services or Keycloak.


---
[[Backend]]