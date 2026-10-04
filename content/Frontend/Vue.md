---
title: Vue
publish:
date created: 2026-09-17
tags:
  - frontend
  - codeless
  - Nitros
---
## 1. What is Vue?

**Vue.js** is a JavaScript framework for building the **frontend/UI** of a web application.

Think of your application as:

```text
                    Your Web Application
                           │
             ┌─────────────┴─────────────┐
             │                           │
         Frontend                     Backend
           Vue.js                     NestJS
             │                           │
       What the user sees          Business logic
       Buttons, pages, forms       Database, APIs
       Chat interface              Authentication
```

Vue primarily handles the **frontend**.

---

# 2. The basic Vue structure

A typical Vue project might look like this:

```text
frontend/
│
├── src/
│   ├── components/
│   │   ├── ChatMessage.vue
│   │   ├── ChatInput.vue
│   │   └── Sidebar.vue
│   │
│   ├── views/
│   │   ├── LoginView.vue
│   │   ├── ChatView.vue
│   │   └── SettingsView.vue
│   │
│   ├── stores/
│   │   └── auth.js
│   │
│   ├── router/
│   │   └── index.js
│   │
│   ├── services/
│   │   └── api.js
│   │
│   ├── assets/
│   │   └── logo.png
│   │
│   ├── App.vue
│   └── main.js
│
├── package.json
├── vite.config.js
└── index.html
```

The important pieces are:

```text
.vue files       → UI components
views/           → Pages
components/      → Reusable UI pieces
stores/          → Application state
router/          → Navigation
services/        → API communication
main.js          → Application entry point
App.vue          → Root component
Vite             → Development/build tool
```

Let's go through them.

---

# 3. `.vue` files — the heart of Vue

A Vue component normally looks like this:

```vue
<template>
  <button @click="count++">
    Count: {{ count }}
  </button>
</template>

<script setup>
import { ref } from 'vue'

const count = ref(0)
</script>

<style scoped>
button {
  padding: 10px;
}
</style>
```

A `.vue` file usually has three sections:

```text
┌─────────────────────────────┐
│ <template>                  │
│                             │
│       HTML / UI             │
│                             │
├─────────────────────────────┤
│ <script setup>              │
│                             │
│       JavaScript            │
│       Logic / State         │
│                             │
├─────────────────────────────┤
│ <style>                     │
│                             │
│       CSS                   │
│                             │
└─────────────────────────────┘
```

This is called a **Single File Component (SFC)**.

---

# 4. `<template>`

The template describes **what the user sees**.

For example:

```vue
<template>
  <h1>Hello</h1>
  <button>Login</button>
</template>
```

It looks like HTML, but Vue adds special features.

For example:

### Display data

```vue
<template>
  <h1>Hello {{ username }}</h1>
</template>
```

If:

```javascript
const username = 'Reyhaneh'
```

the result is:

```text
Hello Reyhaneh
```

`{{ }}` is called **interpolation**.

---

# 5. Vue directives

Vue adds special attributes called **directives**.

For example:

```vue
<button @click="login">
  Login
</button>
```

`@click` means:

> When this button is clicked, execute `login`.

It's shorthand for:

```vue
<button v-on:click="login">
```

You'll see directives everywhere in Vue.

### `v-if`

Conditional rendering:

```vue
<div v-if="isLoggedIn">
  Welcome!
</div>
```

### `v-for`

Looping:

```vue
<div v-for="user in users" :key="user.id">
  {{ user.name }}
</div>
```

### `v-model`

Two-way binding:

```vue
<input v-model="username">
```

Now:

```text
User types
    ↓
username changes
    ↓
Vue updates the application
```

---

# 6. `<script setup>`

This is where your **JavaScript/TypeScript logic** lives.

For example:

```vue
<script setup>
import { ref } from 'vue'

const username = ref('')
const isLoggedIn = ref(false)

function login() {
  isLoggedIn.value = true
}
</script>
```

The template can then use those variables:

```vue
<template>
  <input v-model="username">

  <button @click="login">
    Login
  </button>

  <p v-if="isLoggedIn">
    Welcome {{ username }}
  </p>
</template>
```

So conceptually:

```text
<script>
     │
     │ data + logic
     ↓
<template>
     │
     │ UI
     ↓
Browser
```

---

# 7. Reactive state

One of the most important concepts in Vue is **reactivity**.

For example:

```javascript
import { ref } from 'vue'

const count = ref(0)
```

Then:

```vue
<button @click="count++">
  {{ count }}
</button>
```

Initially:

```text
Count: 0
```

Click:

```text
Count: 1
```

Click:

```text
Count: 2
```

You didn't manually tell Vue:

> Update the HTML.

Vue observes the reactive state and updates the UI automatically.

That's the basic idea of **reactivity**.

---

# 8. Components

This is probably the most important architectural concept.

Instead of creating one giant page:

```text
ChatView.vue
 ├── sidebar
 ├── header
 ├── messages
 ├── input
 ├── buttons
 └── settings
```

you split it into components:

```text
ChatView.vue
│
├── Sidebar.vue
├── ChatHeader.vue
├── MessageList.vue
│   └── ChatMessage.vue
│
└── ChatInput.vue
```

Each component is responsible for a smaller piece of the UI.

For example:

```vue
<!-- ChatMessage.vue -->

<template>
  <div class="message">
    {{ message.text }}
  </div>
</template>

<script setup>
defineProps({
  message: Object
})
</script>
```

Then the parent can use it:

```vue
<ChatMessage :message="message" />
```

---

# 9. Parent → Child communication

Vue components form a hierarchy:

```text
App.vue
   │
   └── ChatView.vue
          │
          ├── Sidebar.vue
          │
          └── ChatMessage.vue
```

Data normally flows **downward**.

For example:

```text
ChatView
   │
   │ message
   ↓
ChatMessage
```

The parent passes data using **props**.

```vue
<ChatMessage
  :message="message"
/>
```

The child receives it:

```javascript
const props = defineProps({
  message: Object
})
```

---

# 10. Child → Parent communication

A child can communicate back to its parent using **events**.

For example:

```vue
<!-- Child -->

<script setup>
const emit = defineEmits(['send'])
</script>

<template>
  <button @click="emit('send')">
    Send
  </button>
</template>
```

Parent:

```vue
<ChatInput @send="sendMessage" />
```

So:

```text
Parent
   │
   │ props
   ↓
Child
   │
   │ events
   ↓
Parent
```

This is a fundamental Vue pattern.

---

# 11. `views/` vs `components/`

You'll commonly see:

```text
src/
├── views/
│   ├── LoginView.vue
│   ├── ChatView.vue
│   └── SettingsView.vue
│
└── components/
    ├── ChatInput.vue
    ├── Sidebar.vue
    └── Message.vue
```

A useful mental model:

### View = page

```text
LoginView
ChatView
SettingsView
```

### Component = reusable piece

```text
Button
Sidebar
ChatMessage
ChatInput
Modal
```

For example:

```text
ChatView
│
├── Sidebar
├── ChatHeader
├── MessageList
│    ├── ChatMessage
│    ├── ChatMessage
│    └── ChatMessage
│
└── ChatInput
```

---

# 12. Vue Router

Now imagine your application has:

```text
/login
/chat
/settings
```

Vue Router handles navigation between these pages.

For example:

```javascript
const routes = [
  {
    path: '/login',
    component: LoginView
  },
  {
    path: '/chat',
    component: ChatView
  },
  {
    path: '/settings',
    component: SettingsView
  }
]
```

Then:

```text
URL
 │
 ├── /login
 │       ↓
 │   LoginView.vue
 │
 ├── /chat
 │       ↓
 │   ChatView.vue
 │
 └── /settings
         ↓
     SettingsView.vue
```

---

# 13. Pinia

This is where your previous question about **Pinia** becomes important.

Imagine you have:

```text
User
 ├── username
 ├── token
 └── loggedIn

Chat
 ├── currentChat
 ├── messages
 └── loading
```

Multiple components may need this information.

Instead of passing it through many components:

```text
App
 ↓
ChatView
 ↓
Sidebar
 ↓
ChatList
 ↓
ChatItem
```

you can put shared state in **Pinia stores**.

For example:

```javascript
// stores/auth.js

import { defineStore } from 'pinia'

export const useAuthStore = defineStore('auth', {
  state: () => ({
    username: null,
    token: null
  })
})
```

Then components can access the same state.

```text
             Pinia Store
             ┌───────────┐
             │ username  │
             │ token     │
             └─────┬─────┘
                   │
        ┌──────────┼──────────┐
        ↓          ↓          ↓
     Sidebar    ChatView    Header
```

That's why Pinia is called a **state management library**.

---

# 14. API calls

Your Vue frontend usually needs to communicate with your NestJS backend.

For example:

```text
Vue
 │
 │ HTTP request
 ↓
NestJS
 │
 │
 ↓
Database
```

You might have something like:

```javascript
const response = await fetch('/api/users')
```

or use Axios:

```javascript
const response = await axios.get('/api/users')
```

Often projects organize this into:

```text
src/
└── services/
    ├── auth.service.js
    ├── chat.service.js
    └── user.service.js
```

For example:

```javascript
export async function getChats() {
  return axios.get('/api/chats')
}
```

Then your component doesn't need to know all the API details.

---

# 15. `main.js`

This is essentially where the Vue application starts.

A typical `main.js` looks something like:

```javascript
import { createApp } from 'vue'
import { createPinia } from 'pinia'
import router from './router'
import App from './App.vue'

const app = createApp(App)

app.use(createPinia())
app.use(router)

app.mount('#app')
```

Think of it as:

```text
main.js
   │
   ├── Create Vue application
   │
   ├── Install Pinia
   │
   ├── Install Router
   │
   ├── Load App.vue
   │
   └── Mount application to browser
```

---

# 16. `App.vue`

`App.vue` is the root component.

For example:

```vue
<template>
  <RouterView />
</template>
```

`RouterView` is where the current page gets rendered.

So:

```text
main.js
   │
   ↓
App.vue
   │
   ↓
RouterView
   │
   ├── /login  → LoginView
   ├── /chat   → ChatView
   └── /settings → SettingsView
```

---

# 17. Where Vite fits

You asked about Vite earlier.

**Vite isn't Vue.**

They're different things:

```text
Vue
 │
 └── Frontend framework
     └── Components, reactivity, UI


Vite
 │
 └── Development/build tool
     ├── Dev server
     ├── Hot reload
     └── Production build
```

So when you run:

```bash
npm run dev
```

Vite starts the development server and serves your Vue application.

When you run:

```bash
npm run build
```

Vite builds the Vue application for production.

---

# 18. Putting everything together

For the kind of **ChatGPT-like application** you're working on, you could mentally visualize the frontend like this:

```text
                         Browser
                            │
                            ↓
                         Vue App
                            │
                       ┌────┴────┐
                       │ App.vue │
                       └────┬────┘
                            │
                       Vue Router
                            │
              ┌─────────────┼─────────────┐
              ↓             ↓             ↓
          LoginView      ChatView     SettingsView
                            │
                ┌───────────┼───────────┐
                ↓           ↓           ↓
             Sidebar    MessageList   ChatInput
                            │
                            ↓
                       ChatMessage


                         Pinia
                           │
             ┌─────────────┼─────────────┐
             ↓             ↓             ↓
          AuthStore     ChatStore     UserStore
                           │
                           ↓
                       API Service
                           │
                           │ HTTP
                           ↓
                         NestJS
                           │
                           ↓
                        Database
```

And **Vite sits underneath the development/build process**:

```text
                 Vite
              /         \
        Development     Build
            │             │
            ↓             ↓
         Vue App       Production
```

## The key concepts to learn in order

If you're learning the Vue codebase you're working on, I'd go in this order:

```text
1. Vue Components (.vue)
        ↓
2. template / script / style
        ↓
3. Reactivity (ref, reactive)
        ↓
4. Directives (v-if, v-for, v-model, :prop, @event)
        ↓
5. Props & Events
        ↓
6. Computed & Watch
        ↓
7. Vue Router
        ↓
8. Pinia
        ↓
9. API calls
        ↓
10. Project architecture
```

Once you understand **components + reactivity + props/events + Pinia + Router**, a Vue project becomes much easier to read.


---
[[Frontend]]
[[My-Journey-In-Codeless]]
