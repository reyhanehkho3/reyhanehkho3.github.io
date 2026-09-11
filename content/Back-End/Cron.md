---
title: Cron
publish: true
date created: 2026-09-06
tags:
  - Backend
  - codeless
---
**Definition:** **Cron is a time-based job scheduler** that automatically runs commands or tasks at specified times or recurring intervals, without a person having to trigger them manually. ([man7.org](https://www.man7.org/linux/man-pages/man1/crontab.1p.html?utm_source=chatgpt.com "crontab(1p) - Linux manual page"))  
In a backend, you can use it for **background jobs** such as cleanup, backups, report generation, or periodically checking something. ([Linuxize](https://linuxize.com/post/scheduling-cron-jobs-with-crontab/?utm_source=chatgpt.com "Crontab: Scheduling Cron Jobs in Linux | Linuxize"))

### Simple example

Suppose you want to delete expired sessions every night:

```text
       Cron Scheduler
             │
       Every night
          at 02:00
             ↓
    cleanupExpiredSessions()
```

You don't need a user to click anything. **Cron automatically starts the task at 02:00.**

### 3 examples

**1. Database backup**

```text
Every day at 03:00
        ↓
Backup PostgreSQL database
```

**2. Cleanup**

```text
Every hour
    ↓
Delete expired sessions
    ↓
Delete temporary files
```

**3. Generate reports**

```text
Every Monday at 08:00
          ↓
Generate weekly sales report
          ↓
Send it to the manager
```

### What does a cron expression mean?

A standard Unix cron schedule has five time fields:

```text
* * * * *
│ │ │ │ │
│ │ │ │ └── Day of week
│ │ │ └──── Month
│ │ └────── Day of month
│ └──────── Hour
└────────── Minute
```

For example:

```text
0 2 * * *
```

means:

> **Run at 02:00 every day.** ([man7.org](https://www.man7.org/linux/man-pages/man5/crontab.5.html?utm_source=chatgpt.com "crontab(5) - Linux manual page"))

### Cron vs. normal code

The important distinction is:

```text
Normal function:
User/API request
      ↓
   Function()
```

```text
Cron job:
      Clock
        ↓
   Scheduled time
        ↓
   Function()
```

So when someone says:

> **"Use a background job scheduler / cron."**

they basically mean:

> **"Run this task automatically in the background at a particular time or interval, rather than waiting for a user request."**

One small distinction: classic Unix **cron is primarily for recurring schedules**. If you need something like **“run this once 20 minutes from now,”** a job queue/scheduler or a one-time scheduler may be more appropriate. ([Debian](https://www.debian.org/doc/manuals/debian-handbook/sect.task-scheduling-cron-atd.el.html?utm_source=chatgpt.com "9.7. Scheduling Tasks with cron and atd"))

---
[[Back-End]]
[[My-Journey-In-Codeless]]