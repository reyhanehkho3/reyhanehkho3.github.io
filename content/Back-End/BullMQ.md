---
title: BullMQ
publish: true
date created: 2026-09-18
tags:
  - codeless
  - Backend
  - Nitros
---
**BullMQ** is a **job queue system for Node.js**. It is commonly used when you want to run tasks **asynchronously and in the background** instead of making the user wait.

It is built on top of **Redis**.

### Simple example

Imagine your chatbot needs to process an uploaded PDF.

Without BullMQ:

```text
User uploads PDF
      ↓
Backend receives PDF
      ↓
Backend processes PDF  ← takes 30 seconds
      ↓
Response to user
```

The user has to wait.

With BullMQ:

```text
User uploads PDF
      ↓
Backend
      ↓
Add job to BullMQ
      ↓
Return "Processing..."
      ↓
                 Redis
                   ↓
              BullMQ Queue
                   ↓
                Worker
                   ↓
            Process PDF
```

The worker processes the task in the background.

### The main pieces

```text
Producer → Queue → Worker
              ↑
            Redis
```

**1. Producer**

Creates a job:

```typescript
await pdfQueue.add('process-pdf', {
  fileId: '123',
});
```

**2. Queue**

BullMQ stores/manages the job. Redis is used underneath to keep track of jobs.

**3. Worker**

Actually performs the work:

```typescript
const worker = new Worker('pdf', async (job) => {
  console.log('Processing:', job.data.fileId);

  await processPdf(job.data.fileId);
});
```

### What is BullMQ useful for?

Common examples:

- 📧 Sending emails
    
- 📄 Processing uploaded files
    
- 🤖 Running AI/LLM requests
    
- 🖼️ Image processing
    
- 🔄 Background data synchronization
    
- 📊 Generating reports
    
- 🔔 Sending notifications
    
- ⏰ Scheduled/ delayed jobs
    
- 🔁 Retrying failed operations
    

For example, if an email service temporarily fails, BullMQ can retry the job rather than losing the request.

### BullMQ vs Redis

They're related, but **not the same thing**:

```text
Redis
  ↓
Data store / in-memory database

BullMQ
  ↓
Job queue framework
  ↓
uses Redis underneath
```

So if your NestJS application has something like:

```text
NestJS
 ├── Chat
 ├── Users
 ├── Files
 └── AI processing
          ↓
       BullMQ
          ↓
        Redis
          ↓
       Worker
```

BullMQ is basically the **traffic manager for background jobs**: it decides what needs to be processed, when, retries, failures, delays, and so on.


---
[[Back-End]]
[[My-Journey-In-Codeless]]
