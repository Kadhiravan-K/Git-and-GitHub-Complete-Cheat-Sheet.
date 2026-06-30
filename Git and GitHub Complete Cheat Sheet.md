# Git and GitHub Complete Cheat Sheet with Examples and Senior-Level Scenario Workflows

````md
# Git and GitHub Complete Cheat Sheet
Author: Kadhiravan K
Level: Beginner
Purpose: Daily development, team collaboration, and production workflows.

---

# Table of Contents

1. Git Basics
2. Repository Creation
3. Tracking Changes
4. Commit Management
5. Branch Management
6. Remote Repository Operations
7. Pull and Push Operations
8. Merge and Rebase
9. Undo Operations
10. Stashing
11. Tags and Releases
12. Advanced Commands
13. Git Configuration
14. Troubleshooting Commands
15. Senior Developer Workflows
16. Team Collaboration Workflows
17. Open Source Contribution Workflow
18. Emergency Recovery Commands

---

# 1. Git Basics

## Check Git Version

```bash
git --version
````

Example:

```bash
git version 2.49.0
```

Purpose:

* Verify Git installation.
* Check current installed version.

---

## Configure Username

```bash
git config --global user.name "Kadhiravan K"
```

Purpose:

* Sets author name for commits.

---

## Configure Email

```bash
git config --global user.email "example@gmail.com"
```

Purpose:

* Associates commits with GitHub account.

---

## View Configuration

```bash
git config --list
```

Purpose:

* Shows all Git settings.

---

# 2. Repository Creation

## Initialize Repository

```bash
git init
```

Purpose:

* Creates a new Git repository.

Result:

```text
Initialized empty Git repository
```

---

## Clone Existing Repository

```bash
git clone https://github.com/user/project.git
```

Example:

```bash
git clone https://github.com/Kadhiravan-K/File-Folder-organization-cheatsheet.git
```

Purpose:

* Downloads repository with complete history.

---

# 3. Tracking Changes

## Check Status

```bash
git status
```

Purpose:

* Shows modified files.
* Shows staged files.
* Shows untracked files.

---

## Add Single File

```bash
git add README.md
```

Purpose:

* Moves file into staging area.

---

## Add Multiple Files

```bash
git add file1.py file2.py
```

---

## Add Entire Project

```bash
git add .
```

Purpose:

* Stages every changed file.

---

# 4. Commit Management

## Create Commit

```bash
git commit -m "Add login module"
```

Purpose:

* Saves snapshot permanently.

---

## Add and Commit Together

```bash
git commit -am "Fix bug"
```

Condition:

* Works only for tracked files.

---

## View Commit History

```bash
git log
```

---

## Short Commit History

```bash
git log --oneline
```

Example:

```text
4d8e92f Added authentication
92d8831 Fixed API bug
```

---

## Graph View

```bash
git log --oneline --graph --all
```

Purpose:

* Visualizes branch history.

---

# 5. Branch Management

## List Branches

```bash
git branch
```

---

## Create Branch

```bash
git branch feature-login
```

---

## Switch Branch

```bash
git checkout feature-login
```

---

## Create and Switch

```bash
git checkout -b feature-login
```

Modern Command:

```bash
git switch -c feature-login
```

---

## Delete Branch

```bash
git branch -d feature-login
```

Force Delete:

```bash
git branch -D feature-login
```

---

## Rename Branch

```bash
git branch -m old-name new-name
```

---

# 6. Remote Repository Commands

## View Remotes

```bash
git remote -v
```

---

## Add Remote

```bash
git remote add origin https://github.com/user/project.git
```

---

## Remove Remote

```bash
git remote remove origin
```

---

## Change Remote URL

```bash
git remote set-url origin https://github.com/user/newrepo.git
```

---

# 7. Push and Pull

## First Push

```bash
git push -u origin main
```

Purpose:

* Creates upstream tracking.

---

## Normal Push

```bash
git push
```

---

## Pull Latest Changes

```bash
git pull
```

---

## Fetch Only

```bash
git fetch
```

Purpose:

* Downloads changes without merging.

---

# 8. Merge and Rebase

## Merge Branch

```bash
git checkout main
git merge feature-login
```

---

## Rebase Branch

```bash
git checkout feature-login
git rebase main
```

Purpose:

* Creates cleaner history.

---

## Abort Merge

```bash
git merge --abort
```

---

## Abort Rebase

```bash
git rebase --abort
```

---

# 9. Undo Operations

## Undo Unstaged Changes

```bash
git restore file.txt
```

---

## Unstage File

```bash
git restore --staged file.txt
```

---

## Undo Last Commit

```bash
git reset --soft HEAD~1
```

---

## Remove Commit Completely

```bash
git reset --hard HEAD~1
```

WARNING:

* Deletes history permanently.

---

## Revert Commit Safely

```bash
git revert commit_hash
```

Preferred in production environments.

---

# 10. Stashing

## Save Temporary Work

```bash
git stash
```

---

## View Stashes

```bash
git stash list
```

---

## Restore Stash

```bash
git stash pop
```

---

## Apply Without Delete

```bash
git stash apply
```

---

# 11. Tags and Releases

## Create Tag

```bash
git tag v1.0.0
```

---

## Push Tags

```bash
git push origin --tags
```

---

## List Tags

```bash
git tag
```

---

# 12. Advanced Commands

## Show File Differences

```bash
git diff
```

---

## Show Staged Differences

```bash
git diff --staged
```

---

## Find Author of Each Line

```bash
git blame app.py
```

---

## Search Commit History

```bash
git log --grep="authentication"
```

---

## Show Specific Commit

```bash
git show commit_hash
```

---

# 13. Scenario-Based Workflows

# Scenario 1

## Create New Repository and Publish to GitHub

```bash
echo "# File-Folder-organization-cheatsheet" >> README.md
git init
git add README.md
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/Kadhiravan-K/XYZ.git
git push -u origin main
```

Explanation:

1. Create README file.
2. Initialize repository.
3. Stage README.
4. Create first commit.
5. Rename branch to main.
6. Connect GitHub repository.
7. Push code to GitHub.

---

# Scenario 2

## Push Existing Project to GitHub

```bash
git remote add origin https://github.com/Kadhiravan-K/XYZ.git
git branch -M main
git push -u origin main
```

---

# Scenario 3

## Create Feature Branch Workflow

```bash
git checkout -b feature-payment
git add .
git commit -m "Add payment module"
git push origin feature-payment
```

---

# Scenario 4

## Update Local Repository

```bash
git pull origin main
```

---

# Scenario 5

## Resolve Merge Conflict

```bash
git pull origin main
# Resolve conflict manually

git add .
git commit -m "Resolve merge conflict"
git push
```

---

# Scenario 6

## Hotfix Production Bug

```bash
git checkout main
git pull
git checkout -b hotfix-login
git add .
git commit -m "Fix login issue"
git push origin hotfix-login
```

---

# Scenario 7

## Rollback Bad Deployment

```bash
git log
git revert commit_hash
git push
```

---

# Scenario 8

## Move Work to Another Branch

```bash
git stash
git checkout another-branch
git stash pop
```

---

# Scenario 9

## Sync Forked Repository

```bash
git remote add upstream https://github.com/original/repo.git
git fetch upstream
git checkout main
git merge upstream/main
git push origin main
```

---

# Scenario 10

## Release New Version

```bash
git tag v2.0.0
git push origin v2.0.0
git push origin --tags
```

---

# Scenario 11

## Recover Deleted Branch

```bash
git reflog
git checkout -b recovered-branch commit_hash
```

---

# Scenario 12

## Remove Sensitive File from Commit

```bash
git rm secret.txt
git commit -m "Remove secret file"
git push
```

---

# Scenario 13

## Force Push After Rebase

```bash
git push --force-with-lease
```

Senior Recommendation:
Never use:

```bash
git push --force
```

Preferred:

```bash
git push --force-with-lease
```

---

# Scenario 14

## Squash Multiple Commits

```bash
git rebase -i HEAD~5
```

Change:

```text
pick
pick
pick
pick
pick
```

to

```text
pick
squash
squash
squash
squash
```

---

# Scenario 15

## Create Release Branch

```bash
git checkout main
git checkout -b release-v2.1
```

---

# 14. Senior Developer Daily Workflow

```bash
git pull origin main
git checkout -b feature-dashboard

# Development work

git add .
git commit -m "Implement dashboard API"

git push origin feature-dashboard

# Create Pull Request

git checkout main
git pull

git merge feature-dashboard

git push origin main
```

---

# 15. Senior Team Branch Strategy

main
│
├── develop
│
├── feature/login
├── feature/payment
├── feature/dashboard
│
├── release/v2.0
│
└── hotfix/security-fix

Purpose:

main

* Production code.

develop

* Integration branch.

feature/*

* New features.

release/*

* Pre-production stabilization.

hotfix/*

* Emergency production fixes.

---

# 16. Emergency Recovery Commands

Recover deleted commit:

```bash
git reflog
```

Recover deleted branch:

```bash
git checkout -b recovery commit_hash
```

Recover deleted file:

```bash
git checkout commit_hash -- filename
```

---

# 17. Most Frequently Used Commands

```bash
git status
git add .
git commit -m "message"
git pull
git push
git checkout -b branch-name
git merge branch-name
git log --oneline
git stash
git stash pop
git fetch
git diff
git revert commit_hash
git tag v1.0.0
git push origin --tags
```

---

# End of Cheat Sheet

```
```
