# Module 03: GitHub & Remote Repositories

## Level 2.5: Git & GitHub

---

## Module Objectives

By the end of this module, you will be able to:

- Create a GitHub account
- Push local repositories to GitHub
- Clone repositories from GitHub
- Keep local and remote in sync

---

## Lesson 1: What is GitHub?

### GitHub Defined

- GIT + GITHUB
- YOUR COMPUTER GITHUB (CLOUD)
- Local Repo push ► Remote Repo
- ◄ pull
- Your work
- Your history
- Teammates
- Portfolio
- Backup
- Sharing

### Why Use GitHub?

| Benefit | Description |
|---------|-------------|
| **Backup** | Code stored safely in cloud |
| **Portfolio** | Show your work to employers |
| **Collaboration** | Work with others |
| **Open Source** | Contribute to projects |
| **History** | Access from anywhere |

---

## Lesson 2: Creating a GitHub Account

### Step-by-Step

1. Go to [github.com](https://github.com)
2. Click "Sign up"
3. Enter your email
4. Create a password
5. Choose a username (this is your public identity!)
6. Verify your account

### Username Tips

- Use your real name or professional alias
- Keep it simple and memorable
- Avoid numbers if possible
- This will be your brand!

**Examples**: `sokha-meas`, `dara-dev`, `vanna-codes`

---

## Lesson 3: Creating a Repository on GitHub

### New Repository

1. Click "+" in top right → "New repository"
2. Fill in details:
 - Repository name: `my-portfolio`
 - Description: "My personal portfolio website"
 - Public or Private
 - Don't add README (we have local files)
3. Click "Create repository"

### You'll See Instructions Like

```bash
# Push an existing repository
git remote add origin https://github.com/username/my-portfolio.git
git branch -M main
git push -u origin main
```

---

## Lesson 4: Connecting Local to Remote

### Add Remote

```bash
# In your local project folder
git remote add origin https://github.com/username/my-portfolio.git
```

### Verify Remote

```bash
git remote -v

# Output:
# origin https://github.com/username/my-portfolio.git (fetch)
# origin https://github.com/username/my-portfolio.git (push)
```

### Push to GitHub

```bash
# First push (set upstream)
git push -u origin main

# Future pushes
git push
```

### What Just Happened?

1. Your local commits were sent to GitHub
2. GitHub now has a copy of your project
3. Anyone (if public) can see it

---

## Lesson 5: Cloning Repositories

### Clone = Download + Connect

```bash
# Clone a repository
git clone https://github.com/username/repository.git

# Clone into specific folder
git clone https://github.com/username/repository.git my-folder
```

### What Clone Does

1. Downloads all files
2. Downloads entire history
3. Sets up remote connection
4. Ready to push/pull

### Clone Your Own Repo to Another Computer

```bash
git clone https://github.com/yourusername/my-portfolio.git
cd my-portfolio
# Now you can work and push changes
```

---

## Lesson 6: Push and Pull

### Push — Send Local Changes to GitHub

```bash
# After committing locally
git push

# First time for a branch
git push -u origin branch-name
```

### Pull — Get GitHub Changes Locally

```bash
# Get latest changes
git pull

# Same as:
git fetch
git merge origin/main
```

### Workflow with Remote

```bash
# Start of day: get latest
git pull

# Work...
git add .
git commit -m "Add feature"

# End of work: push
git push
```

---

## Lesson 7: Authentication

### HTTPS with Token

GitHub no longer accepts passwords. Use tokens:

1. GitHub → Settings → Developer settings → Personal access tokens
2. Generate new token
3. Copy and save it
4. Use as password when pushing

### SSH (Recommended)

More secure and convenient:

```bash
# Generate SSH key
ssh-keygen -t ed25519 -C "your@email.com"

# Start SSH agent
eval "$(ssh-agent -s)"

# Add key
ssh-add ~/.ssh/id_ed25519

# Copy public key
cat ~/.ssh/id_ed25519.pub
```

Add public key to GitHub:

1. Settings → SSH and GPG keys
2. New SSH key
3. Paste your key

Now use SSH URLs:

```bash
git remote set-url origin git@github.com:username/repo.git
```

---

## Self-Check Exercises

### Exercise 1: Create GitHub Account

1. Sign up at github.com
2. Complete your profile
3. Add a profile picture

### Exercise 2: First Repository

1. Create a new repo on GitHub
2. Push your portfolio project to it
3. Verify it's visible on GitHub

### Exercise 3: Clone Practice

1. Clone your own repo to a different folder
2. Make a change
3. Commit and push
4. Pull in original folder

### Exercise 4: README

1. Add a README.md to your repo
2. Write a good description
3. Push to GitHub
4. See it displayed on the repo page

---

## Module Summary

**Key Commands**

| Command | Purpose |
|---------|---------|
| `git remote add origin url` | Connect to GitHub |
| `git push` | Send commits to GitHub |
| `git pull` | Get commits from GitHub |
| `git clone url` | Download a repository |
| `git remote -v` | View remote connections |

**Workflow**

```bash
# One-time setup
git remote add origin url
git push -u origin main

# Daily workflow
git pull # Get updates
# work...
git add .
git commit -m "msg"
git push # Send updates
```

---

## Next Steps

**Before moving to Module 04:**

- [ ] GitHub account created
- [ ] Portfolio on GitHub
- [ ] Can push and pull
- [ ] Get mentor verification

**Coming Next**: Module 04 - Collaboration Workflow

*You will learn to work with others!*

---

<div align="center">

**Your code is online!** 

*GitHub is your professional portfolio.*

</div>
