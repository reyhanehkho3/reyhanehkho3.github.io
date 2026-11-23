---
title: Squash Merge
publish: true
date created: 2026-11-23
tags:
  - git
---
**Squash Merge** is a Git merging strategy that combines all commits from a feature branch into **one single commit** on the target branch.

In simple terms, instead of bringing all the individual commits into `develop`, Git combines their changes and creates one clean commit.

## **1. Example**

Imagine you're working on a feature branch called `feature/user-auth`.

During development, you make these commits:

```
feature/user-auth

Commit 1: Add login endpoint
Commit 2: Fix login validation
Commit 3: Add password hashing
Commit 4: Fix authentication bug
Commit 5: Update login tests
```

Now you want to merge this branch into `develop`.

### **Normal Merge**

All five commits are preserved in the `develop` branch history.

**Normal Merge**

`develop`

- Commit 1: Add login endpoint
    
- Commit 2: Fix login validation
    
- Commit 3: Add password hashing
    
- Commit 4: Fix authentication bug
    
- Commit 5: Update login tests
    

Five individual commits remain visible in history.

### **Squash Merge**

All five commits are combined into one commit.

**Squash Merge**

`develop`

**Add user authentication**

Contains all five commits' changes

One clean commit appears in history.

## **2. How to do a Squash Merge?**

Using Git command line:

```
# Switch to the target branch
git checkout develop

# Get the latest changes
git pull

# Squash merge your feature branch
git merge --squash feature/user-auth

# Create one commit
git commit -m "Add user authentication"
```

Now your changes are in `develop` as one commit.

Note: `git merge --squash` does not automatically create a commit. That's why you need the separate `git commit` command.

## **3. Normal Merge vs Squash Merge**

|Feature|Normal Merge|Squash Merge|
|---|---|---|
|Number of commits|Preserves individual commits|One commit|
|Git history|More detailed|Cleaner|
|Original commit history|Preserved|Not preserved as individual commits|
|Best for|Detailed development history|Clean feature-level history|

## **4. When should you use Squash Merge?**

For example, suppose your team follows this workflow:

```
main
  |
  └── develop
        |
        └── feature/payment
              |
              ├── Add payment API
              ├── Fix validation
              ├── Fix bugs
              └── Add tests
```

When `feature/payment` is ready, you squash merge it into `develop`.

Your `develop` history will contain something like:

```
develop
  |
  ├── Add user authentication
  ├── Add payment feature
  └── Add order management
```

This makes it easier to understand what each merged feature introduced.

**My recommendation:** Squash Merge is a good choice when your feature branch contains many small commits (such as `fix`, `update`, `try again`, etc.) and you want a clean history in your main development branches.

One important detail: Squash Merge does not delete your feature branch automatically. You can delete it after successfully merging.


---
[[Git&Github]]