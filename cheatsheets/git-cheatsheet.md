---
title: "Git Quick Reference"
topic: "Git"
category: "Development"
tags: [git, version-control, cli, cheatsheet, reference]
date_created: "2026-01-17"
last_updated: "2026-01-17"
---

# Git Cheatsheet

## Quick Reference

Essential Git commands for version control.

### Setup

```bash
# Configure user
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"

# Initialize repository
git init

# Clone repository
git clone https://github.com/user/repo.git
```

## Basic Commands

| Command | Description | Example |
|---------|-------------|---------|
| `git status` | Show working tree status | `git status` |
| `git add` | Stage changes | `git add file.txt` |
| `git commit` | Commit changes | `git commit -m "message"` |
| `git push` | Push to remote | `git push origin main` |
| `git pull` | Fetch and merge | `git pull origin main` |
| `git log` | View commit history | `git log --oneline` |

## Branching

```bash
# Create branch
git branch feature-name

# Switch branch
git checkout feature-name

# Create and switch
git checkout -b feature-name

# List branches
git branch -a

# Delete branch
git branch -d feature-name

# Merge branch
git merge feature-name
```

## Remote Repositories

```bash
# Add remote
git remote add origin https://github.com/user/repo.git

# List remotes
git remote -v

# Fetch changes
git fetch origin

# Push to remote
git push -u origin main

# Remove remote
git remote remove origin
```

## Undoing Changes

```bash
# Discard changes in working directory
git checkout -- file.txt

# Unstage file
git reset HEAD file.txt

# Amend last commit
git commit --amend

# Reset to previous commit
git reset --hard HEAD~1

# Revert commit (creates new commit)
git revert commit-hash
```

## Viewing Changes

```bash
# Show changes
git diff

# Show staged changes
git diff --staged

# Show commit details
git show commit-hash

# View file history
git log -p file.txt
```

## Stashing

```bash
# Stash changes
git stash

# List stashes
git stash list

# Apply stash
git stash apply

# Apply and remove stash
git stash pop

# Drop stash
git stash drop
```

## Tips & Tricks

- Use `.gitignore` to exclude files from tracking
- Write clear, descriptive commit messages
- Commit frequently with logical changes
- Create branches for new features
- Use `git log --graph --oneline --all` for visual history
- Set up SSH keys for easier authentication
- Use `git rebase` for cleaner history (carefully!)

## Common Patterns

```bash
# Quick commit all changes
git add -A && git commit -m "message" && git push

# Update from remote
git fetch origin && git rebase origin/main

# Create branch from specific commit
git checkout -b new-branch commit-hash

# Cherry-pick commit
git cherry-pick commit-hash

# Interactive rebase (last 3 commits)
git rebase -i HEAD~3

# Clean untracked files
git clean -fd
```

## Resources

- [Official Git Documentation](https://git-scm.com/doc)
- [Pro Git Book](https://git-scm.com/book/en/v2)
- [GitHub Git Cheatsheet](https://education.github.com/git-cheat-sheet-education.pdf)
- [Atlassian Git Tutorials](https://www.atlassian.com/git/tutorials)
