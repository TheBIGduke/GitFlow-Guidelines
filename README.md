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