# Module 01: Introduction to Git

## Level 2.5: Git & GitHub

---

## Module Objectives

By the end of this module, you will be able to:

- Understand what version control is
- Explain why Git is important
- Install and configure Git
- Create your first repository

---

## Lesson 1: What is Version Control?

### The Problem

Have you ever:

- Needed to undo changes but can't remember what you changed?
- Lost work because you overwrote a file?
- Wanted to try something without breaking your project?
- Needed to work on the same files with teammates?

Version control solves all these problems!

### Version Control Defined

- VERSION CONTROL
- A system that tracks changes to files over time.
- You can:
- • See what changed and when
- • Go back to any previous version
- • Work on multiple versions simultaneously
- • Merge work from multiple people
- Think of it as unlimited UNDO + history + collaboration

---

## Lesson 2: What is Git?

### Git Defined

**Git** is the most popular version control system. Created by Linus Torvalds (creator of Linux) in 2005.

### Git vs GitHub

| Git | GitHub |
|-----|--------|
| Software on your computer | Website/service |
| Tracks changes locally | Hosts code online |
| Works offline | Needs internet |
| Free, open source | Free + paid plans |
| The tool | A place to use the tool |

**Analogy**: Git is like a camera (takes snapshots). GitHub is like a photo album cloud service (stores and shares photos).

---

## Lesson 3: Key Git Concepts

### Repository (Repo)

A folder where Git tracks all changes:

```
my-project/
├── index.html
├── style.css
├── script.js
└── .git/ ← Git's data (hidden folder)
```

### Commit

A "snapshot" of your files at a point in time:

```
Commit History:
────────────────────────────────────────────────────────────
 [Initial] → [Add CSS] → [Fix bug] → [Add feature] → [Now]
────────────────────────────────────────────────────────────
 ↑
 You can go back to any of these!
```

### Staging Area

Before committing, you "stage" files — select which changes to include:

```
┌─────────────────────────────────────────────────────────────────────────────┐
│ THE GIT WORKFLOW │
├─────────────────────────────────────────────────────────────────────────────┤
│ │
│ WORKING DIRECTORY → STAGING AREA → REPOSITORY │
│ (Your files) (To be saved) (Saved history) │
│ │
│ index.html (modified) ┌─────────────┐ Commit 1 │
│ style.css (modified) ──► │ index.html │ ──► Commit 2 │
│ readme.md (no change) │ style.css │ Commit 3 │
│ └─────────────┘ ... │
│ │
│ git add git commit │
│ │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## Lesson 4: Installing Git

### On KOOMPI OS (Linux)

Git is usually pre-installed. Check:

```bash
git --version
```

If not installed:

```bash
sudo pacman -S git
```

### Configure Git

Set your identity (required before first commit):

```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
```

Check your settings:

```bash
git config --list
```

### Configure Editor

```bash
# Set VS Code as default editor
git config --global core.editor "code --wait"

# Or nano (simpler)
git config --global core.editor "nano"
```

---

## Lesson 5: Creating a Repository

### Initialize a New Repository

```bash
# Navigate to your project
cd ~/projects/my-website

# Initialize Git
git init
```

You'll see: `Initialized empty Git repository in /home/user/projects/my-website/.git/`

### Check Status

```bash
git status
```

Shows:

- Which files are new (untracked)
- Which files have changes
- Which files are staged

### Your First Commit

```bash
# Stage all files
git add .

# Create commit with message
git commit -m "Initial commit"
```

---

## Lesson 6: The .gitignore File

### What to Ignore

Some files shouldn't be tracked:

- node_modules/ (can be reinstalled)
- .env files (secrets)
- build files
- system files

### Create .gitignore

```bash
# Create the file
touch .gitignore
```

### Common .gitignore Content

```
# Dependencies
node_modules/

# Build files
dist/
build/

# Environment variables
.env
.env.local

# OS files
.DS_Store
Thumbs.db

# Editor files
.vscode/
*.swp

# Logs
*.log
```

---

## Lesson 7: Understanding Git Workflow

### The Three States

Files can be in three states:

| State | Meaning |
|-------|---------|
| **Modified** | Changed but not staged |
| **Staged** | Marked to go in next commit |
| **Committed** | Safely stored in Git |

### Basic Workflow

```bash
# 1. Make changes to your files
# (edit index.html, add style.css, etc.)

# 2. Check what changed
git status

# 3. Stage changes
git add . # All changes
git add index.html # Specific file

# 4. Commit with message
git commit -m "Add navigation bar"

# 5. Repeat!
```

### Good Commit Messages

```bash
# Bad
git commit -m "changes"
git commit -m "fixed stuff"
git commit -m "asdf"

# Good
git commit -m "Add contact form to homepage"
git commit -m "Fix navigation bug on mobile"
git commit -m "Update hero section styling"
```

**Tips:**

- Start with a verb (Add, Fix, Update, Remove)
- Keep it short (50 characters)
- Explain what, not how

---

## Self-Check Exercises

### Exercise 1: Install & Configure

1. Verify Git is installed (`git --version`)
2. Configure your name and email
3. Verify configuration (`git config --list`)

### Exercise 2: First Repository

1. Create a new project folder
2. Add an index.html file with basic content
3. Initialize Git
4. Make your first commit

### Exercise 3: Multiple Commits

1. Modify your HTML file
2. Commit the changes with a meaningful message
3. Add a CSS file
4. Commit that change
5. Run `git log` to see your history

### Exercise 4: .gitignore

1. Create a .gitignore file
2. Add common ignores
3. Create a node_modules folder (to test)
4. Verify it's ignored with `git status`

### Exercise 5: Existing Project

1. Take one of your existing projects (portfolio, quiz)
2. Initialize Git in it
3. Create a .gitignore
4. Make your first commit

---

## Module Summary

**Key Commands**

| Command | Purpose |
|---------|---------|
| `git init` | Start tracking a folder |
| `git status` | See current state |
| `git add` | Stage files |
| `git commit` | Save a snapshot |
| `git log` | View history |

**Key Concepts**

| Term | Meaning |
|------|---------|
| Repository | Tracked project folder |
| Commit | Snapshot of files |
| Staging | Selecting files to commit |
| .gitignore | Files Git should ignore |

---

## Next Steps

**Before moving to Module 02:**

- [ ] Git installed and configured
- [ ] Created first repository
- [ ] Made multiple commits
- [ ] Understand staging
- [ ] Get mentor verification

**Coming Next**: Module 02 - Basic Git Commands

*You will learn to navigate Git history and undo changes!*

---

<div align="center">

**You've entered the Git world!** 

*Every professional developer uses Git.*

</div>
