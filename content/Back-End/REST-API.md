---
title: REST API
publish: true
date created: 2026-17-05
tags:
  - codeless
  - Backend
  - websocket
---
- REpresentational State Transfer
-  An **architectural style** for designing networked applications. A **REST API** (or RESTful API) is an [[API]] that conforms to the constraints of the REST architecture.
-  **HTTP** as its protocol.    
- **URLs/URIs** to identify resources (like `/users`).
- **HTTP Methods** (GET, POST, PUT, DELETE) to define actions.
- **Data formats** like **JSON** to send and receive data.

## REST
For an API to be truly "RESTful," it must follow these six guiding principles:
#### client-server
The client and the server are separate.
#### Stateless
Each request must contain the info the server needs to process the request. 
#### Cacheable
Responses from the server must explicitly state whether they can be cached or not.
It means that when a server sends a response back to a client, it must **clearly indicate** whether that response can be stored ("cached") and reused later, or if it must be fetched fresh every time.
#### Uniform Interface
The most fundamental principle.
- **Resource-Based**: Everything is a **resource** (e.g., a user, a product, an order), identified by a URI (like `/users/123`).
- **Manipulation of Resources through Representations**: Clients interact with resources using a **representation** of that resource (like JSON or XML), not the actual resource on the server.
- **Self-descriptive Messages**: Each request and response contains enough information to describe how to process it.
- **HATEOAS (Hypermedia as the Engine of Application State)**: The response from the server should include hyperlinks to other related actions the client can take. (This is an advanced constraint that is often relaxed in simpler APIs).
#### Layered System
 The client doesn't know if it's connected directly to the end server or to an intermediary.
#### Code On Demand
 The server can send executable code to the client (like JavaScript). 
## why is REST so popular?
- **Simplicity & Standardization**: It uses well-known HTTP standards that every developer understands.
- **Scalability**: The stateless and layered nature makes it easy to scale applications.
- **Flexibility & Independence**: The client and server can be written in different programming languages (JavaScript, Python, Java, etc.) and can be developed and deployed independently.
- **Platform Agnostic**: Any device that can use HTTP (phones, browsers, IoT devices) can use a REST API.

**REST API can influence how you organize your folders**, but REST itself does **not prescribe a folder structure**.

REST defines **how your API should behave**—resources, HTTP methods, URLs, status codes, etc. Your architecture determines how you organize the code.

For example, a REST API might have:

```text
GET    /users
POST   /users
GET    /users/:id
DELETE /users/:id

GET    /tasks
POST   /tasks
```

You could organize the backend like this:

```text
src/
├── users/
│   ├── user.routes.js
│   ├── user.controller.js
│   └── user.service.js
│
├── tasks/
│   ├── task.routes.js
│   ├── task.controller.js
│   └── task.service.js
│
└── app.js
```

This is **feature/module-based organization**.

But you could also use a layer-based structure:

```text
src/
├── routes/
│   ├── user.routes.js
│   └── task.routes.js
│
├── controllers/
│   ├── user.controller.js
│   └── task.controller.js
│
├── services/
│   ├── user.service.js
│   └── task.service.js
│
└── models/
    ├── user.model.js
    └── task.model.js
```

Both can implement the **same REST API**.

### The important distinction

```text
REST API
   ↓
Defines API behavior
   ├── URLs
   ├── HTTP methods
   ├── resources
   └── responses

Architecture
   ↓
Defines code organization
   ├── folders
   ├── modules
   ├── controllers
   ├── services
   └── repositories
```

So:

> **REST affects what your API looks like, but your chosen architecture affects how your folders and files are organized.**

A **modular REST API** often organizes folders around resources/features (`users`, `tasks`, `auth`), but that's an architectural choice—not a REST requirement.


## why WebSockets/Socket.IO rather than traditional REST APIs?


The main reason is **how the data needs to move**.

### REST API

With traditional REST, the **client asks the server** for data.

```text
Client ── request ──> Server
Client <─ response ── Server
```

For example, a chat app could do:

```http
GET /messages
```

The server responds with the current messages.

But if another user sends a new message, the client doesn't automatically know about it. It has to ask again:

```text
Client: "Any new messages?"
Server: "No"

Client: "Any new messages?"
Server: "No"

Client: "Any new messages?"
Server: "Yes!"
```

This is called **polling** if you repeatedly make requests.

---

## WebSocket

A WebSocket creates a **persistent connection** between the client and server.

```text
Client ═══════════════ Server
       persistent connection
```

Now **either side can send data at any time**.

```text
User A
  ↓
Server
  ↓
User B immediately receives message
```

No need for User B to repeatedly ask.

### Example: chat

```text
User A: "Hello!"
       ↓
     Server
       ↓
User B: receives "Hello!" immediately
```

This is why WebSockets are useful for:

- 💬 Chat applications
    
- 🔔 Real-time notifications
    
- 🎮 Multiplayer games
    
- 📈 Live dashboards
    
- 🟢 Online/offline presence
    
- 🚕 Live location tracking
    
- 📊 Real-time monitoring
    

---

# Where does Socket.IO fit?

**Socket.IO is a library built around real-time communication.**

It commonly uses WebSockets when available, while providing additional features such as:

- automatic reconnection
    
- events
    
- rooms
    
- namespaces
    
- acknowledgements
    

For example:

```js
socket.emit("new-message", {
  text: "Hello!"
});
```

The server can listen:

```js
socket.on("new-message", (message) => {
  // handle message
});
```

So:

```text
WebSocket
   ↓
low-level communication protocol

Socket.IO
   ↓
library providing a higher-level real-time system
```

---

## REST vs WebSocket

|                            | REST                        | WebSocket             |
| -------------------------- | --------------------------- | --------------------- |
| Communication              | Request → Response          | Two-way               |
| Connection                 | Usually individual requests | Persistent connection |
| Server can push data?      | Not directly                | ✅ Yes                 |
| Good for CRUD              | ✅                           | Usually unnecessary   |
| Good for chat              | Possible, but inefficient   | ✅                     |
| Good for real-time updates | Less ideal                  | ✅                     |
| Complexity                 | Lower                       | Higher                |

### Important: WebSockets don't replace REST

You often use **both**.

For example, a social media app:

```text
REST API
├── GET /posts
├── POST /posts
├── DELETE /posts/:id
└── GET /profile

WebSocket
├── new notification
├── new message
├── user online
└── post liked
```

A good mental model is:

> **REST = "Give me something."**  
> **WebSocket = "Keep me connected and tell me when something happens."**

So you shouldn't choose WebSockets simply because they're "faster." **Use them when the application actually needs real-time, server-initiated updates.**





---

[[Back-End]]
[[My-Journey-In-Codeless]]