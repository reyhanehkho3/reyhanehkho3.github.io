---
title: Domain
publish: true
date created: 2026-11-28
tags:
  - backend
---
## **1. What is a Domain?**

A **domain name** is the human-readable address of a website.

Examples:

- `google.com`
    
- `github.com`
    
- `example.com`
    

Computers communicate using IP addresses, but remembering IP addresses is difficult.

That's why we use domain names.

For example:

```
google.com → 142.250.x.x
```

**DNS (Domain Name System)** translates domain names into IP addresses.

## **2. What is a Subdomain?**

A **subdomain** is an additional part of a domain used to organize different sections or services of a website.

For example:

```
example.com
```

You can create different subdomains:

- `blog.example.com` → Blog
    
- `api.example.com` → Backend API
    
- `admin.example.com` → Admin dashboard
    
- `docs.example.com` → Documentation
    
- `shop.example.com` → Online store
    

Here:

- `example.com` is the main domain.
    
- `blog`, `api`, `admin`, `docs`, and `shop` are subdomains.
    

## **3. Anatomy of a URL**

Consider this URL:

```
https://api.example.com:8080/users?id=10
```

Each part has a different meaning:

|Part|Name|Description|
|---|---|---|
|`https://`|Protocol|Defines how the browser communicates with the server.|
|`api`|Subdomain|Identifies a specific service.|
|`example.com`|Domain|Main domain name.|
|`:8080`|Port|Identifies the server application or service.|
|`/users`|Path|Identifies a resource or endpoint.|
|`?id=10`|Query string|Provides additional parameters.|

## **4. Can a Domain Have Multiple Subdomains?**

Yes!

For example:

```
example.com
│
├── www.example.com
├── api.example.com
├── admin.example.com
├── blog.example.com
└── dev.example.com
```

You can even have nested subdomains:

```
api.dev.example.com
```

Here:

- `example.com` is the main domain.
    
- `dev.example.com` is a subdomain.
    
- `api.dev.example.com` is a subdomain of `dev.example.com`.
    

## **5. Are Subdomains Separate Websites?**

Not necessarily, but they can be.

For example:

- `example.com` → Main website
    
- `api.example.com` → Backend API
    
- `admin.example.com` → Admin dashboard
    

Each subdomain can point to a different server or application.

They can also point to the same server.

This is configured through DNS.

## **6. Domain vs. Subdomain vs. URL vs. IP**

|Term|Meaning|Example|
|---|---|---|
|Domain|Main website address|`example.com`|
|Subdomain|Additional address under a domain|`api.example.com`|
|URL|Complete address of a resource|`https://api.example.com/users`|
|IP address|Network address of a machine|`192.168.1.10`|
|DNS|Translates domain names into IP addresses|Domain → IP|

**Important:** A domain is not necessarily a website. It is an address that can point to a website, backend API, mail server, or another service.

## **7. What Should You Learn Next?**

A useful next topic is **DNS Records**.

The most important types are:

- `A` → Maps a domain to an IPv4 address.
    
- `AAAA` → Maps a domain to an IPv6 address.
    
- `CNAME` → Points one domain name to another domain name.
    
- `MX` → Specifies mail servers for a domain.
  
  ---
[[Backend]]