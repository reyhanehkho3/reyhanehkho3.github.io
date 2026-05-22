---
title: Git & Github
publish: true
date created: 2026-05-17
---
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




[[Project-Management]]
