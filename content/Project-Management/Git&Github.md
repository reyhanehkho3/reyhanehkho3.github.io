---
title: Git & Github
publish: true
date created: 2026-05-17
---
git keeps track of the snapshots of a project through commits. There are 3 important phases:
- Working Tree -> Staging Area -> Commit History.
## Definitions:
- A **Branch** is a separated path for making changes.
- **Commit** is a change that you can't edit. But you can check previous commits and continue with them.
- **Merge/Rebase** means combining histories with different trade-offs.
- A **Conflict** is when git can't merge the changes all together. Solving it requires understanding the changes.
- **Merge Request/ Pull Request** is the place for review, discussion, CI and confirmation before merging.

### Suggested Workflow:
- Understanding the issue/requirements.
- Making a little branch.
- Keep track of the changes through commits.
- Check push and test before diff.
- Make a pull request with short explanation(what and why), reason, ways to test.
- Enable feedback and merge after review/CI. This means only merge your PR after the automated CI pipeline passes successfully and you've received a human code review approval.

### Semantic Versioning: MAJOR.MINOR.PATCH
- **MAJOR** version increments when you make breaking API changes
    
- **MINOR** version increments when you add functionality in a backward-compatible way.
    
- **PATCH** version increments when you make backward-compatible bug fixes
‬
### Changelog:
A **changelog** is a curated, chronologically ordered list of notable changes made to a software project, with each version or release clearly labeled.

It's essentially a **"what's new"** document that tells users and contributors exactly what changed, was added, fixed, or removed in each release of your software.

A changelog must contain meaningful changes for users, not a list of the commits only.

## Setup:
### Initialize:
In order to initialize a repo in your system:

```bash
git init
```

Then you need to set your name and email for the commits:

```bash
git config user.name "Your Name"
git config user.email "your.email@example.com"
```

Or you can set it for all your repositories:

```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

Then comes tracking the files:

```bash
git status
```

```bash
git add file.txt
```

(`git add .` for all files)

```bash
git commit -m "initial commit"
```


### Remote repository:
In order to add a remote repository:

```bash
git remote add origin https://github.com/username/repository.git
git branch -M main
git push -u origin main
```

The second line forcefully renames the current branch to `main`.(It might be master in older versions of git)
- `-m` (move) will fail if a branch named `main` already exists
- `-M` (force move) will overwrite/force the rename even if `main` exists


In the third line:
- **`-u`** = `--set-upstream` (sets a tracking relationship)
- **`origin`** = Name of your remote repository (default name)
	After this, you can use `git push`.

Checking remote branch:

```bash
git remote -v                    # See remotes
git branch -vv                   # See tracking branches
```

### Pull:
```bash
git pull
```

Or specifying remote and branch:

```bash
git pull origin main
```

If you have uncomited local changes:

```bash
# Stash your changes first
git stash
git pull
git stash pop  # Re-apply your changes
```


### Clone:
```bash
git clone <repository-url>
```


When using http, you have to enter your username and password every time. Since github no longer accepts passwords, you have to use personal access token. You can generate one via github settings.

Ssh, requires a one-time key and is more convinient.

Note: In order to use ssh, you need to have a ssh key generated.

cloning into a specific folder:

```bash
git clone https://github.com/username/repository.git my-folder
```

Cloning a specific branch:

```bash
git clone -b develop https://github.com/username/repo.git
│         │  │       │
│         │  │       └── Repository URL
│         │  └── Branch name (develop)
│         └── Flag meaning "branch"
└── Command
```



---
[[Project-Management]]
