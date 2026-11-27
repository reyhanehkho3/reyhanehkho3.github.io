---
title: Docker
publish:
date created: 2026-10-07
tags:
  - devops
---
The basic setup is:

1. Install Docker
    
2. Create a `Dockerfile` for your app
    
3. Create `docker-compose.yml` if you have multiple services (e.g. app + PostgreSQL)
    
4. Build the image
    
5. Start the containers
    
6. Test that the app works inside Docker
    

For example, for a **Node.js backend + PostgreSQL** project:

### 1. Project structure

```text
my-project/
├── src/
├── package.json
├── package-lock.json
├── Dockerfile
├── docker-compose.yml
└── .dockerignore
```

### 2. `Dockerfile`

```dockerfile
FROM node:22-alpine

WORKDIR /app

COPY package*.json ./

RUN npm ci

COPY . .

EXPOSE 3000

CMD ["npm", "run", "start"]
```

This basically says:

> Take a Node image → create `/app` → install dependencies → copy my code → expose port 3000 → start the application.

### 3. `.dockerignore`

```text
node_modules
.git
.env
dist
```

This prevents unnecessary/sensitive files from being copied into the image.

### 4. `docker-compose.yml`

If your backend needs PostgreSQL:

```yaml
services:
  backend:
    build: .
    ports:
      - "3000:3000"
    environment:
      DATABASE_URL: postgresql://postgres:postgres@postgres:5432/mydb
    depends_on:
      postgres:
        condition: service_healthy

  postgres:
    image: postgres:18-alpine
    environment:
      POSTGRES_USER: postgres
      POSTGRES_PASSWORD: postgres
      POSTGRES_DB: mydb
    ports:
      - "5432:5432"
    volumes:
      - postgres_data:/var/lib/postgresql/data
    healthcheck:
      test: ["CMD-SHELL", "pg_isready -U postgres -d mydb"]
      interval: 5s
      timeout: 5s
      retries: 5

volumes:
  postgres_data:
```

One important Docker concept here: **inside Docker, `localhost` means the current container**, not your PostgreSQL container. That's why the backend connects to:

```text
postgres:5432
```

`postgres` is the Compose service name.

### 5. Build and run

From the project directory:

```bash
docker compose up --build
```

Or in the background:

```bash
docker compose up -d --build
```

Check containers:

```bash
docker compose ps
```

Check logs:

```bash
docker compose logs -f backend
```

Stop everything:

```bash
docker compose down
```

If you want to **remove the database volume too**:

```bash
docker compose down -v
```

⚠️ That deletes the PostgreSQL data stored in that Compose volume.

---

### The mental model

Think of it like this:

```text
                 Docker Compose
                       │
          ┌────────────┴────────────┐
          │                         │
     Backend container        PostgreSQL container
          │                         │
     Node/Nest/Express          PostgreSQL
          │                         │
       :3000                     :5432
          │
          └─────── network ────────┘
```

Your computer only needs to expose the ports you actually want to access:

```text
localhost:3000  →  backend container :3000
localhost:5432  →  postgres container :5432
```

---
[[DevOps]]