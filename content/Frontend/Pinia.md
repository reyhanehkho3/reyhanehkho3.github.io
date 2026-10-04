---
title: Pinia
publish: true
date created: 2026-09-17
tags:
  - frontend
  - codeless
  - Nitros
---
**Pinia** is the **state management library for Vue.js**. Think of it as a place where you keep data that needs to be shared between different components/pages of your Vue application.

### Without Pinia

Imagine your chatbot has:

```text
App
├── Sidebar
│   └── list of chats
├── ChatView
│   └── current messages
└── UserMenu
    └── current user
```

You might end up passing data between components:

```text
App
 ↓
Sidebar
 ↓
ChatList
```

and using `props` and `emit` everywhere.

That becomes difficult when many unrelated components need the same data.

### With Pinia

You create a **store**:

```js
// stores/chat.js
import { defineStore } from 'pinia'

export const useChatStore = defineStore('chat', {
  state: () => ({
    chats: [],
    currentChat: null,
    messages: []
  }),

  actions: {
    selectChat(chat) {
      this.currentChat = chat
    },

    addMessage(message) {
      this.messages.push(message)
    }
  }
})
```

Then any component can access it:

```vue
<script setup>
import { useChatStore } from '@/stores/chat'

const chatStore = useChatStore()
</script>

<template>
  <div>
    {{ chatStore.currentChat?.title }}
  </div>
</template>
```

Another component can use **the exact same state**:

```js
const chatStore = useChatStore()

console.log(chatStore.messages)
```

So the architecture becomes:

```text
                 ┌───────────────┐
                 │   Pinia Store │
                 │               │
                 │ chats         │
                 │ currentChat   │
                 │ messages      │
                 │ user          │
                 └───────┬───────┘
                         │
          ┌──────────────┼──────────────┐
          ↓              ↓              ↓
       Sidebar        ChatView       UserMenu
```

### What is Pinia actually useful for?

Usually for **global/shared application state**, such as:

- 👤 Current user
    
- 🔐 Authentication state
    
- 💬 Current chat
    
- 📋 List of chats
    
- ⚙️ User settings
    
- 🌐 Current language
    
- 🎨 Theme
    
- 🔔 Notifications
    
- 📡 Loading/error states
    

For your **ChatGPT-like application**, a reasonable structure could be:

```text
stores/
├── auth.js
├── chat.js
├── user.js
└── settings.js
```

For example:

```js
authStore
  ├── user
  ├── accessToken
  ├── isAuthenticated
  └── login()
  └── logout()

chatStore
  ├── chats
  ├── currentChat
  ├── messages
  ├── sendMessage()
  └── createChat()

settingsStore
  ├── theme
  ├── language
  └── updateSettings()
```

### Pinia vs database

An important distinction:

**Pinia is not a database.**

For example:

```text
                 Backend
                    │
                    ↓
              PostgreSQL
             ┌────────────┐
             │ users      │
             │ chats      │
             │ messages   │
             └────────────┘
                    ↑
                    │ API
                    ↓
              Vue + Pinia
             ┌────────────┐
             │ user       │
             │ chats      │
             │ messages   │
             └────────────┘
                    ↑
                    │
             Vue components
```

The database provides **persistent storage**.

Pinia provides **client-side application state**.

If the user refreshes the page, Pinia's state normally disappears unless you explicitly persist it (for example, to `localStorage`) and/or reload it from your backend.

So for your chatbot project, a common pattern is:

**PostgreSQL → persistent source of truth**  
**API → transfers data**  
**Pinia → keeps currently needed data in the Vue app**  
**Components → display and modify that state**

---
[[Frontend]]
[[My-Journey-In-Codeless]]