---
title: SSRr
publish: true
date created: 2026-11-25
tags:
  - Sah
  - frontend
---
## **What is SSR?**

**SSR (Server-Side Rendering)** is a web development technique where the server generates the HTML of a web page and sends it to the browser.

Instead of the browser generating the entire page using JavaScript, the server prepares the HTML before sending it.

### **How does it work?**

1. You visit a website.
    
2. Your browser sends an HTTP request to the server.
    
3. The server generates the page's HTML.
    
4. The server sends the generated HTML to your browser.
    
5. The browser displays the page.
    

### **Example**

Imagine visiting an online store.

With SSR:

- The server retrieves the product information.
    
- It generates the HTML containing the product name, price, and description.
    
- Your browser receives the HTML and displays the page.
    

### **SSR vs. CSR**

**CSR (Client-Side Rendering)** means the browser generates most of the page using JavaScript.

|SSR|CSR|
|---|---|
|HTML is generated on the server|HTML is generated in the browser|
|Browser receives pre-rendered HTML|Browser receives JavaScript and initial HTML|
|Often improves initial content visibility|May require JavaScript execution before content appears|
|Can help search engine indexing|Search engine indexing may require additional processing|

### **What are the advantages of SSR?**

- **SEO:** Search engines can more easily access the initial page content.
    
- **Initial loading:** Users can see meaningful content before the full JavaScript application loads.
    
- **Performance:** Reduces some of the initial rendering work required from the browser.
    

### **Which frameworks support SSR?**

- Next.js (React)
    
- Nuxt (Vue)
    
- SvelteKit (Svelte)
    
- Angular (Angular SSR)
    

**In simple terms:** SSR means the server builds the webpage's HTML and sends it to the browser, rather than making the browser build the entire page itself.


---
[[Frontend]]