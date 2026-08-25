---
title: Reverse Proxy
publish: true
date created: 2026-08-23
tags:
  - Backend
  - codeless
---
To understand a **reverse proxy**, it helps to first understand a **forward proxy** (the kind you probably use every day).

Here is the simplest breakdown:

**The Analogy**
- **Forward Proxy (You):** You are at a restaurant. You tell the waiter, "Bring me the steak from the kitchen." The waiter goes to the kitchen, gets the steak, and brings it to you. **You** are hiding your identity from the kitchen (the kitchen doesn't know *you* are eating it, just that the waiter took it). 
- **Reverse Proxy (The Restaurant):** You call the restaurant's main phone number. A receptionist answers. You say, "I need to speak to Accounting." The receptionist transfers you to Accounting. You never actually call Accounting directly; you call the main number, and the receptionist routes you. **The restaurant** is hiding its internal structure from you (you don't know Accounting's direct line).

---

### The Technical Definition

A **reverse proxy** is a server that sits **in front** of one or more web servers (backend servers) and intercepts all client requests. 

Instead of a client (like your web browser) connecting directly to a website's server, the client connects to the reverse proxy. The reverse proxy then decides which backend server should handle the request, fetches the response, and delivers it back to the client as if it came directly from the proxy itself.

---

### How it works step-by-step:

1. You type `www.example.com` into your browser.
2. Your DNS resolves to the **Reverse Proxy's** IP address (not the actual web server).
3. Your browser sends a request to the reverse proxy.
4. The reverse proxy looks at the request (e.g., "I want `/images/`" or "I want `/api/`").
5. The proxy forwards that request to the correct internal server (Server A for images, Server B for the API).
6. The internal server processes the request and sends the response back to the proxy.
7. The proxy sends the response back to your browser. **You never know Server A or B even exist.**

---

### Why do companies use Reverse Proxies? (The Benefits)

Reverse proxies are absolutely critical to the modern internet. Here is why:

**1. Load Balancing (Traffic Cop)**
If a website gets millions of visitors, one server cannot handle the load. The reverse proxy distributes incoming traffic across a pool of hundreds of backend servers, ensuring no single server gets overwhelmed.

**2. Security and Anonymity (The Bouncer)**
The reverse proxy acts as a shield. The actual backend servers are hidden inside a private network with no direct internet access. Hackers can only attack the proxy, which is hardened against attacks. It also acts as a central point to enforce SSL/TLS encryption (HTTPS).

**3. Caching (The Speed Booster)**
Reverse proxies can store (cache) static content like images, CSS files, and JavaScript. If 1,000 users request the same company logo, the proxy serves it from its own memory 1,000 times without ever bothering the backend servers. This drastically speeds up load times.

**4. Compression and Optimization**
The proxy can compress large files (like images or HTML) into smaller sizes before sending them to the user's browser, saving bandwidth and speeding up downloads for mobile users.

**5. A/B Testing and Canary Releases**
The proxy can be programmed to send 5% of users to a new beta version of your website (Server B) and 95% of users to the stable version (Server A). If the beta crashes, only 5% of users are affected.

---

### Real-World Examples

- **NGINX** and **HAProxy** are the most popular open-source reverse proxy software.
- **Cloudflare** is a massive reverse proxy network. When you use Cloudflare, your website's DNS points to Cloudflare, which proxies your traffic, caches it, and protects you from DDoS attacks before sending the "clean" traffic to your actual web host.
- **Amazon's ELB (Elastic Load Balancer)** is a cloud-based reverse proxy.

---

### Reverse Proxy vs. Forward Proxy (Quick Recap)

| Feature | Forward Proxy | Reverse Proxy |
| :--- | :--- | :--- |
| **Who is it for?** | The **Client** (the user). | The **Server** (the website owner). |
| **What does it hide?** | Hides the **client's** identity (IP address) from the server. | Hides the **server's** internal structure from the client. |
| **Common use** | Bypassing geo-blocks, corporate internet filtering, privacy. | Load balancing, security, caching, hosting multiple websites on one IP. |

---

### One very common misconception

People often confuse a **Reverse Proxy** with a **VPN** or a **Forward Proxy**. 
Remember: If you *pay for it* to hide your own browsing (like NordVPN), you are using a **Forward Proxy**. If a *website* pays for it to handle millions of visitors (like using Cloudflare), they are using a **Reverse Proxy**.

---
[[Back-End]]
[[codeless]]