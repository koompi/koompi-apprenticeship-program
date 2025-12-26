# Module 02: Basic Git Commands

## Level 2.5: Git & GitHub

---

## Module Objectives

By the end of this module, you will be able to:

- View commit history
- Undo changes in various ways
- Work with branches
- Use essential daily Git commands

---

## Lesson 1: Viewing History

### git log

See all commits:

```bash
git log
```

Output:

```
commit a1b2c3d4e5f6... (HEAD -> main)
Author: Sokha <sokha@email.com>
Date: Thu Dec 26 10:00:00 2024 +0700

 Add navigation styling

commit f6e5d4c3b2a1...
Author: Sokha <sokha@email.com>
Date: Thu Dec 26 09:30:00 2024 +0700

 Add header section
```

### Compact Log View

```bash
# One line per commit
git log --oneline

# Output:
# a1b2c3d Add navigation styling
# f6e5d4c Add header section
# 1234567 Initial commit
```

### Other Useful Log Options

```bash
# Last 5 commits
git log -5

# Show what changed in each commit
git log -p

# Graph view (for branches)
git log --oneline --graph --all
```

---

## Lesson 2: Checking Differences

### git diff

See what changed in your files:

```bash
# Changes not yet staged
git diff

# Changes that are staged
git diff --staged

# Specific file
git diff index.html
```

### Understanding Diff Output

```diff
diff --git a/index.html b/index.html
--- a/index.html
+++ b/index.html
@@ -1,5 +1,6 @@
 <html>
 <head>
- <title>Old Title</title>
+ <title>New Title</title>
+ <link rel="stylesheet" href="style.css">
 </head>
 </html>
```

- Lines starting with `-` were removed
- Lines starting with `+` were added

---

## Lesson 3: Undoing Changes

### Discard Unstaged Changes

```bash
# Discard changes to specific file
git checkout -- filename.html

# Or using restore (newer)
git restore filename.html
```

**Warning**: This permanently loses your changes!

### Unstage Files

```bash
# Unstage specific file
git reset HEAD filename.html

# Or using restore (newer)
git restore --staged filename.html
```

### Amend Last Commit

Forgot something? Fix the last commit:

```bash
# Make your fix
git add forgotten-file.html

# Amend the commit
git commit --amend -m "Better commit message"
```

### Revert a Commit

Create a new commit that undoes a previous one:

```bash
git revert abc123
```

This is safe — doesn't rewrite history.

### Reset to Previous Commit

**Caution**: This can lose work!

```bash
# Soft reset (keep changes staged)
git reset --soft abc123

# Mixed reset (keep changes unstaged) - default
git reset abc123

# Hard reset (discard all changes)
git reset --hard abc123
```

---

## Lesson 4: Branches

### What Are Branches?

Branches let you work on features without affecting main code:

```
 ┌─ [feature-login]
 │ → Add login page
main: ──●──●──●──●──┤
 │ → Continue main work
 └── [main]
```

### Creating Branches

```bash
# Create a new branch
git branch feature-login

# Switch to it
git checkout feature-login

# Or do both at once
git checkout -b feature-login

# Newer syntax
git switch -c feature-login
```

### Listing Branches

```bash
# List local branches
git branch

# Current branch has asterisk
# feature-login
# * main
```

### Switching Branches

```bash
git checkout main
# or
git switch main
```

### Merging Branches

Bring changes from one branch into another:

```bash
# Switch to branch you want to merge INTO
git checkout main

# Merge the feature branch
git merge feature-login
```

### Deleting Branches

```bash
# Delete merged branch
git branch -d feature-login

# Force delete (even if not merged)
git branch -D abandoned-feature
```

---

## Lesson 5: Common Workflows

### Daily Workflow

```bash
# Morning: Start work
git status # Check current state
git pull # Get latest changes (if using remote)

# Make changes to files...

# Save progress
git add .
git commit -m "Add contact form"

# Continue working...
git add .
git commit -m "Style contact form"

# End of day: Push to remote
git push
```

### Feature Branch Workflow

```bash
# Start new feature
git checkout -b feature-dark-mode

# Work on feature...
git add .
git commit -m "Add dark mode toggle"

git add .
git commit -m "Implement dark mode styles"

# Feature complete - merge back
git checkout main
git merge feature-dark-mode
git branch -d feature-dark-mode
```

---

## Lesson 6: Useful Commands Reference

### Status & Information

| Command | Purpose |
|---------|---------|
| `git status` | Current state |
| `git log` | Commit history |
| `git log --oneline` | Compact history |
| `git diff` | Show changes |
| `git branch` | List branches |

### Making Changes

| Command | Purpose |
|---------|---------|
| `git add .` | Stage all |
| `git add file` | Stage specific file |
| `git commit -m "msg"` | Commit with message |
| `git commit --amend` | Fix last commit |

### Undoing

| Command | Purpose |
|---------|---------|
| `git restore file` | Discard changes |
| `git restore --staged file` | Unstage |
| `git revert commit` | Undo a commit safely |
| `git reset --hard commit` | Reset to commit (destructive) |

### Branches

| Command | Purpose |
|---------|---------|
| `git branch name` | Create branch |
| `git checkout name` | Switch to branch |
| `git checkout -b name` | Create and switch |
| `git merge name` | Merge branch |
| `git branch -d name` | Delete branch |

---

## Lesson 7: Common Problems & Solutions

### Problem: Committed to Wrong Branch

```bash
# Move commit to correct branch
git checkout correct-branch
git cherry-pick abc123

# Remove from wrong branch
git checkout wrong-branch
git reset --hard HEAD~1
```

### Problem: Need to Temporarily Save Work

```bash
# Stash current changes
git stash

# Do other work...

# Get changes back
git stash pop
```

### Problem: Merge Conflict

When Git can't auto-merge:

```
<<<<<<< HEAD
Your version
=======
Their version
>>>>>>> branch-name
```

1. Edit file to resolve
2. Remove conflict markers
3. `git add filename`
4. `git commit`

---

## Self-Check Exercises

### Exercise 1: Log Exploration

1. Create 5 commits in a project
2. View with `git log`
3. View with `git log --oneline`
4. Find a specific commit

### Exercise 2: Undo Practice

1. Make changes to a file
2. Use `git restore` to undo before staging
3. Make changes again
4. Stage, then unstage with `git restore --staged`

### Exercise 3: Branch Workflow

1. Create a new branch called `feature-test`
2. Make changes and commit
3. Switch back to main
4. Merge the feature branch
5. Delete the feature branch

### Exercise 4: Amend Commit

1. Make a commit with a typo in the message
2. Use `git commit --amend` to fix it
3. Verify with `git log`

---

## Module Summary

**Essential Commands**

```bash
# Status
git status
git log --oneline

# Changes
git add .
git commit -m "message"

# Undo
git restore filename
git restore --staged filename

# Branches
git branch name
git checkout name
git merge name
```

---

## Next Steps

**Before moving to Module 03:**

- [ ] View and understand history
- [ ] Undo changes safely
- [ ] Create and merge branches
- [ ] Get mentor verification

**Coming Next**: Module 03 - GitHub & Remote Repositories

*You will put your code online!*

---

<div align="center">

**Git mastery growing!** 

*These commands will become second nature.*

</div>
