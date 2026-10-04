---
title: Vite
publish:
date created: 2026-09-17
tags:
  - frontend
  - codeless
  - Nitros
---
**Vite** is a **build tool and development server** commonly used with modern frontend frameworks like Vue, React, and Svelte.

If you're working with **Vue**, you can think of it like this:

```text
Vue application
     │
     ▼
   Vite
 ┌───────────────┐
 │ Development   │
 │ server        │
 │ Build         │
 │ Hot reload    │
 │ Module system │
 └───────────────┘
     │
     ▼
 Browser
```

### 1. Development server

When you run:

```bash
npm run dev
```

Vite starts a local server, often something like:

```text
http://localhost:5173
```

You can then open your Vue application in the browser.

### 2. Hot Module Replacement (HMR)

This is one of Vite's most useful features.

Suppose you change:

```vue
<h1>Hello</h1>
```

to:

```vue
<h1>Hello World</h1>
```

Vite detects the change and updates the browser **without requiring a full page reload**.

So your development loop is very fast:

```text
Edit Vue file
     ↓
Vite detects change
     ↓
Browser updates immediately
```

### 3. Build your application

When you're ready to deploy:

```bash
npm run build
```

Vite takes your source code:

```text
src/
├── main.js
├── App.vue
├── components/
└── views/
```

and produces optimized files, typically in:

```text
dist/
├── index.html
├── assets/
│   ├── index-xxxxx.js
│   └── index-xxxxx.css
```

Those files can then be served by a web server.

### 4. Vite is NOT Vue

This distinction is important:

```text
Vue       → UI framework
Pinia     → state management
Vite      → development/build tool
```

For example, your project might use all three:

```text
                Your Vue App
                     │
       ┌─────────────┼─────────────┐
       ↓             ↓             ↓
      Vue           Pinia        Vite
   UI/components    State      Dev + Build
```

A typical Vue project's `package.json` might contain:

```json
{
  "dependencies": {
    "vue": "...",
    "pinia": "..."
  },
  "devDependencies": {
    "vite": "..."
  }
}
```

**In one sentence:** Vite is the tool that makes developing and building your frontend fast; Vue builds the UI, while Pinia manages shared state.



---
[[Frontend]]
[[My-Journey-In-Codeless]]