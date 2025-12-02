# Gitflow for Octopy

**This manual outlines the standard procedure for using Git across all Octopy's projects. This workflow is designed to ensure a stable production environment while allowing multiple developers to work concurrently**

---

# 1. Core Branches

Our repository always maintains two permanent branches that serve specific, critical roles.

| Branch | Role | Purpose |
|--------|------|---------|
| `main` | Production | Always reflects the code currently running in production. It must be stable, tested, and ready to deploy. Only merges (no direct commits) are allowed
| `develop` | Integration | Reflects the state of the next major release. All completed features are merged here before being packaged for release |

---

# 2. Synchronization and Setup

> [!WARNING]
> Before starting any work, you must ensure your local environment is up-to-date and clean

## 2.1 Updating Your Local Repository

Use these commands frequently to keep your work aligned with the remote repository:

| Command | Action | Explanation |
|---------|--------|-------------|
| `git fetch` | Download changes | Downloads changes and branches from the remote (`origin`) but **does not** merge or modify your local working files. Use this to check what others have done
| `git pull` | Fetch and Merge | A shortcut for `git fetch` followed by `git merge`. This downloads remote changes and immediately attempts to integrate them into your current local branch
| `git push` | Upload changes | Uploads your local committed changes to the remote repository

> [!TIP]
> Best Practice: Use git fetch often to inspect changes, and git pull only when you are sure you want to integrate the remote changes into your current branch

## 2.2 Initial Setup

1. Clone the repository
```
git clone [repository URL]
```

2. Switch to the primary development branch:
```
git checkout develop
```

---

# 3. Feature Development Cycle
Every task starts and ends on a temporary branch.

## 3.1 Branch Naming Convention Dictionary

> [!IMPORTANT]
> All temporary branches must use a descriptive prefix and are always branched off of develop (except for hotfix/)

| Prefix | Type of Work | Example | 
|--------|--------------|---------|
| `feature/` | New functionality or major enhancement | `feature/dashboard-v2` |
| `bugfix/` | Fixing bugs found in the `develop` branch | `bugfix/api-validation-issue` |
| `hotfix/` | Critical fix for a bug found in production (`main`) | `hotfix/login-crash-v1.0.1` |
| `feature/` | New functionality or major enhancement | feature/dashboard-v2 |
| `refactor/` | Restructuring code without changing behavior | feature/dashboard-v2 |

## 3.2 Start the Feature

1. `Sync develop`
```
git checkout develop
git pull
```

2. Create and switch to your new branch using the naming convention
```
git checkout -b feature/new-task-name
```

## 3.3 Work, Commit, and Push

1. Write code and commit locally
```
git add .
git commit -m "FEAT: Added initial structure for form"
```

2. Push to Remote (for backup and sharing)
```
git push -u origin feature/new-task-name
```

# 3.4 Finish the Feature (Pull Request)

1. Open a Pull Request requesting to merge your branch INTO `develop`
2. Get the necessary approval from a reviewer
3. Merge the PR into develop and delete the temporary branch.