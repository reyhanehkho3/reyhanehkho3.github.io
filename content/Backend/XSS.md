---
title: XSS
publish: true
date created: 2026-11-25
tags:
  - backend
  - Sah
---
## **What is XSS?**

**XSS (Cross-Site Scripting)** is a web security vulnerability that allows an attacker to inject malicious JavaScript into a website.

When another user visits the affected page, the malicious JavaScript can execute in their browser as if it were part of the trusted website.

### **How does it work?**

Imagine a website that allows users to post comments.

1. An attacker submits a comment containing malicious JavaScript.
    
2. The website stores the comment without properly handling the input.
    
3. Another user visits the page.
    
4. The browser executes the injected JavaScript.
    
5. The script might steal accessible information, modify page content, or perform actions on behalf of the user.
    

### **Simple example**

A normal comment:

```
Hello! Nice website.
```

A malicious comment:

```
<script>
  alert('Your account is compromised!');
</script>
```

If the website incorrectly handles and renders this input as executable HTML, the JavaScript runs in visitors' browsers.

### **Types of XSS**

|Type|Description|
|---|---|
|Stored XSS|Malicious script is saved on the server and executed when users view it.|
|Reflected XSS|Malicious script is included in a request and reflected in the response.|
|DOM-based XSS|Client-side JavaScript processes untrusted data in an unsafe way, causing script execution.|

### **How can XSS be prevented?**

- **Input validation:** Validate user input.
    
- **Output encoding:** Display user-provided content as text instead of executable HTML or JavaScript.
    
- **Content Security Policy (CSP):** Restrict which scripts the browser can execute.
    
- **HttpOnly Cookies:** Prevent JavaScript from directly accessing sensitive cookies.
    

### **XSS vs. CSRF**

- **XSS:** An attacker injects malicious JavaScript into a trusted website.
    
- **CSRF:** An attacker tricks your browser into sending an unauthorized request using your existing session.
    

**In simple terms:** XSS exploits a website's handling of untrusted content to execute malicious code in visitors' browsers.


---
[[Backend]]