---
title: Git Flow
publish: true
date created: 2026-09-11
tags:
  - git
  - codeless
---
**Git Flow** is a **Git branching strategy**. It defines how you create and use branches while developing features, fixing bugs, and releasing versions.

The basic idea is:

```text
main
  │
  ├── develop
  │     │
  │     ├── feature/login
  │     ├── feature/tasks
  │     └── feature/profile
  │
  └── release / hotfix
```

### Main branches

**`main`**

Contains production/released code.

```text
main
 ↓
what users get
```

**`develop`**

Contains the latest development work before it is released.

```text
develop
 ↓
next version
```

### Feature branch

When implementing a feature:

```bash
git checkout develop
git checkout -b feature/login
```

You work on:

```text
feature/login
```

Then merge it into `develop`:

```text
feature/login
       ↓
    develop
```

### Release branch

When you're preparing a new version:

```text
develop
   ↓
release/1.2.0
```

You use the release branch for final testing, bug fixes, version numbers, etc.

Then:

```text
release/1.2.0
       ↓
     main
```

and usually also merge the fixes back into `develop`.

### Hotfix branch

If production has a critical bug:

```text
main
 │
 └── hotfix/login-bug
          ↓
        main
```

After fixing it, you also merge the fix into `develop`.

---

### The complete flow

```text
                  feature/login
                 ↗
develop ────────────────→
   │
   │
   └────→ release/1.2.0 ───→ main
                              ↑
                         hotfix/bug
```

### Important

**Git Flow is not Git itself.**

Git provides:

```text
branches
commits
merges
tags
```

Git Flow is a **recommended workflow for using those features**.

Also, Git Flow is not the only workflow. Modern teams often use **GitHub Flow** or **trunk-based development**, which are usually simpler.

For a small personal project, you probably **don't need full Git Flow**. A simpler approach like:

```text
main
  ↑
feature/xxx
```

is often enough.

---
[[Git&Github]]
[[My-Journey-In-Codeless]]