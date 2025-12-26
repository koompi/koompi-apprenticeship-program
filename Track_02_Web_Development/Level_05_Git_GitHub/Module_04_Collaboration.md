# Module 04: Collaboration Workflow

## Level 2.5: Git & GitHub

---

## Module Objectives

By the end of this module, you will be able to:

- Work with teammates on the same project
- Use pull requests
- Resolve merge conflicts
- Contribute to open source

---

## Lesson 1: Collaboration Overview

### How Teams Work Together

```
┌─────────────────────────────────────────────────────────────────────────────┐
│ TEAM COLLABORATION │
├─────────────────────────────────────────────────────────────────────────────┤
│ │
│ ┌─────────────┐ │
│ │ GITHUB │ │
│ │ (main) │ │
│ └──────┬──────┘ │
│ │ │
│ ┌───────────────────┼───────────────────┐ │
│ ▼ ▼ ▼ │
│ ┌──────────┐ ┌──────────┐ ┌──────────┐ │
│ │ Sokha's │ │ Dara's │ │ Bopha's │ │
│ │ Computer │ │ Computer │ │ Computer │ │
│ └──────────┘ └──────────┘ └──────────┘ │
│ │ │ │ │
│ feature-nav feature-footer fix-bug │
│ │
│ Everyone pushes to GitHub, pulls updates from GitHub │
│ │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## Lesson 2: Fork & Pull Request Workflow

### For Contributing to Others' Projects

```
1. FORK → Create your copy of their repo
2. CLONE → Download your fork
3. BRANCH → Create feature branch
4. CODE → Make your changes
5. PUSH → Push to YOUR fork
6. PR → Request they merge your changes
```

### Step-by-Step

**1. Fork the Repository**

- Go to the project on GitHub
- Click "Fork" button
- Now you have your own copy

**2. Clone Your Fork**

```bash
git clone https://github.com/YOUR-USERNAME/project.git
cd project
```

**3. Add Upstream Remote**

```bash
git remote add upstream https://github.com/ORIGINAL-OWNER/project.git
```

**4. Create Branch & Work**

```bash
git checkout -b feature-improvement
# Make changes...
git add .
git commit -m "Add improvement"
```

**5. Push to Your Fork**

```bash
git push origin feature-improvement
```

**6. Create Pull Request**

- Go to your fork on GitHub
- Click "Compare & pull request"
- Describe your changes
- Submit!

---

## Lesson 3: Pull Requests

### What is a Pull Request?

A pull request (PR) is a proposal to merge your changes into another branch.

### Creating a Good PR

**Title**: Clear summary of changes

```
Add dark mode toggle to navigation
```

**Description**:

```markdown
## What does this PR do?
Adds a dark mode toggle button to the navigation bar.

## Changes made
- Added toggle button in nav.html
- Added dark mode CSS in styles.css
- Added toggle JavaScript in app.js

## Screenshots
[Include if visual changes]

## How to test
1. Open the page
2. Click the moon icon
3. Verify colors change
```

### Reviewing PRs

When reviewing someone's PR:

- Read the description
- Look at the files changed
- Test locally if possible
- Leave constructive comments
- Approve or request changes

---

## Lesson 4: Merge Conflicts

### When Conflicts Happen

Conflicts occur when two people change the same lines:

```
You: "The color is blue"
Teammate: "The color is red"
Git: "I don't know which one to use!"
```

### Conflict Markers

```html
<<<<<<< HEAD
<h1 class="blue-header">Welcome</h1>
=======
<h1 class="red-header">Hello</h1>
>>>>>>> feature-branch
```

### Resolving Conflicts

1. **Open the conflicted file**
2. **Decide what to keep**
3. **Remove conflict markers**
4. **Save the file**
5. **Stage and commit**

```html
<!-- Resolved: we decided on purple -->
<h1 class="purple-header">Welcome</h1>
```

```bash
git add conflicted-file.html
git commit -m "Resolve merge conflict in header"
```

### Avoiding Conflicts

- Pull before starting work
- Communicate with teammates
- Work on different files when possible
- Use feature branches
- Merge main into your branch regularly

---

## Lesson 5: Team Workflow Best Practices

### Branch Naming

```
feature/add-login-page
feature/dark-mode
fix/navigation-bug
hotfix/critical-security
docs/update-readme
```

### Commit Message Format

```
type: short description

Longer explanation if needed.

- Bullet points for details
- Reference issues: Fixes #123
```

Types: `feat`, `fix`, `docs`, `style`, `refactor`, `test`

### Protected Branches

Main branch should require:

- Pull request reviews
- Passing tests
- No direct pushes

---

## Lesson 6: Contributing to Open Source

### Finding Projects

- GitHub Explore
- Topics you're interested in
- Projects you use
- "Good first issue" labels

### First Contributions

Start small:

- Fix typos in documentation
- Improve README
- Add tests
- Fix simple bugs

### Contribution Checklist

- [ ] Read CONTRIBUTING.md
- [ ] Check existing issues/PRs
- [ ] Fork and clone
- [ ] Follow code style
- [ ] Write clear commit messages
- [ ] Test your changes
- [ ] Respond to review feedback

### Your First Open Source PR

Try [First Contributions](https://github.com/firstcontributions/first-contributions) — a project made for learning!

---

## Lesson 7: GitHub Features

### Issues

Track bugs and features:

- Report bugs
- Request features
- Discuss improvements

### Projects

Organize work:

- Kanban boards
- Track progress
- Assign tasks

### Actions

Automate workflows:

- Run tests
- Deploy code
- Check code quality

### GitHub Pages

Host websites for free!

```bash
# In repo settings → Pages
# Select branch (usually main or gh-pages)
# Your site: username.github.io/repo-name
```

---

## Self-Check Exercises

### Exercise 1: Fork & PR

1. Fork a practice repository
2. Make a simple change
3. Create a pull request

### Exercise 2: Simulate Conflict

1. Create two branches from main
2. Change the same line in both
3. Merge first branch
4. Try to merge second (conflict!)
5. Resolve it

### Exercise 3: Review a PR

1. Find a PR on a public project
2. Read through the changes
3. Note what makes it good or could be improved

### Exercise 4: GitHub Pages

1. Create a simple repo with index.html
2. Enable GitHub Pages
3. Access your live site!

---

## Module Summary

**Collaboration Commands**

| Command | Purpose |
|---------|---------|
| `git remote add upstream url` | Link to original repo |
| `git fetch upstream` | Get original's changes |
| `git merge upstream/main` | Merge original's changes |

**Workflow**

```
fork → clone → branch → code → push → PR
```

**Conflict Resolution**

1. Identify conflicted files
2. Edit to resolve
3. Remove markers
4. Stage and commit

---

## Level Complete

You've completed Git & GitHub! You can now:

 Track changes with Git
 Use branches for features
 Host code on GitHub
 Collaborate with pull requests
 Contribute to open source

**Git & GitHub Badge** earned! 

---

<div align="center">

**You're a Git collaborator!** 

*Open source awaits your contributions.*

</div>
