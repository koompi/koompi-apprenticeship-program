# Module 03: Linux Terminal Fundamentals

## Track 00: Digital Foundations

---

## Module Objectives

By the end of this module, you will be able to:

- Understand what the terminal is and why it's powerful
- Navigate the file system using commands
- Create, move, copy, and delete files and folders
- Feel confident using the command line

---

## Lesson 1: Introduction to the Terminal

### What is the Terminal?

The **terminal** (also called **command line** or **shell**) is a text-based way to control your computer. Instead of clicking with a mouse, you type commands.

**GUI vs Terminal:**

| GUI (Graphical) | Terminal (Command Line) |
|-----------------|-------------------------|
| Click with mouse | Type commands |
| See icons and windows | See text |
| Beginner-friendly | Powerful for experts |
| Limited to what menus offer | Full control of system |
| Slower for repetitive tasks | Fast for automation |

### Why Developers Use the Terminal

| Reason | Explanation |
|--------|-------------|
| **Speed** | Typing is faster than clicking through menus |
| **Power** | Access to features not available in GUI |
| **Automation** | Run scripts to repeat tasks automatically |
| **Remote** | Control servers anywhere in the world |
| **Universal** | Works the same on any Linux/Mac system |

### Opening the Terminal

**How to open terminal on KOOMPI:**

- Press `Ctrl + Alt + T`
- Or search for "Terminal" in applications

When you open the terminal, you see a **prompt**:

```bash
username@koompi:~$ 
```

This shows:

- `username` — Your user name
- `koompi` — Your computer's name
- `~` — Your current location (home directory)
- `$` — Ready for your command

---

## Lesson 2: Basic Navigation Commands

### Your File System is a Tree

Think of your files as a tree structure:

```
/                    (root - the top)
├── home/            (home directories)
│   └── student/     (your home folder)
│       ├── Documents/
│       ├── Downloads/
│       ├── Desktop/
│       └── projects/
├── etc/             (system configuration)
├── usr/             (user programs)
└── var/             (logs and data)
```

### Navigation Commands

#### `pwd` — Print Working Directory

Shows where you currently are.

```bash
$ pwd
/home/student
```

**Remember**: pwd = "Present Working Directory"

#### `ls` — List

Shows what's in the current directory.

```bash
$ ls
Desktop Documents Downloads Music Pictures projects
```

**Useful variations:**

| Command | What it does |
|---------|--------------|
| `ls` | List files and folders |
| `ls -l` | Long format (details) |
| `ls -a` | Show hidden files (starting with .) |
| `ls -la` | Both long format and hidden files |

**Example of `ls -la`:**

```bash
$ ls -la
total 32
drwxr-xr-x 8 student student 4096 Dec 26 10:00 .
drwxr-xr-x 3 root root 4096 Dec 25 09:00 ..
-rw-r--r-- 1 student student 220 Dec 25 09:00 .bashrc
drwxr-xr-x 2 student student 4096 Dec 26 09:30 Documents
drwxr-xr-x 2 student student 4096 Dec 26 10:00 Downloads
```

#### `cd` — Change Directory

Move to a different folder.

```bash
cd Documents # Go into Documents folder
cd .. # Go up one level (parent folder)
cd ~ # Go to your home folder
cd / # Go to the root of the system
```

### Path Types

| Type | Example | Meaning |
|------|---------|---------|
| **Absolute** | `/home/student/Documents` | Full path from root |
| **Relative** | `Documents` | Path from where you are now |
| `..` | `cd ..` | Parent directory |
| `.` | `./script.sh` | Current directory |
| `~` | `cd ~` | Home directory |

---

## Lesson 3: Working with Files and Folders

### Creating Directories

#### `mkdir` — Make Directory

```bash
mkdir my_project # Create a folder called "my_project"
mkdir -p projects/web/css # Create nested folders
```

### Creating Files

#### `touch` — Create Empty File

```bash
touch index.html # Create an empty file
touch style.css script.js # Create multiple files
```

### Viewing File Contents

#### `cat` — Concatenate (Display File)

```bash
cat index.html # Show file contents
```

#### `less` — View Long Files

```bash
less long_file.txt # Scroll through (press Q to exit)
```

#### `head` and `tail`

```bash
head file.txt # Show first 10 lines
tail file.txt # Show last 10 lines
head -n 5 file.txt # Show first 5 lines
```

### Copying, Moving, Removing

#### `cp` — Copy

```bash
cp file.txt backup.txt # Copy file
cp -r folder1 folder2 # Copy folder (recursive)
```

#### `mv` — Move (also Rename)

```bash
mv old_name.txt new_name.txt # Rename a file
mv file.txt Documents/ # Move file to Documents
```

#### `rm` — Remove (Delete)

```bash
rm file.txt # Delete a file
rm -r folder # Delete a folder and contents
rm -rf folder # Force delete (BE CAREFUL!)
```

 **WARNING**: There is NO undo for `rm`! Deleted files are gone forever.

---

## Lesson 4: Essential Commands Reference

### Quick Reference Card

**Navigation:**

- `pwd` - Print current directory
- `ls` - List files
- `ls -la` - List all files with details
- `cd folder` - Go to folder
- `cd ..` - Go up one level
- `cd ~` - Go home

**Files & Folders:**

- `mkdir name` - Create folder
- `touch file` - Create empty file
- `cp src dst` - Copy file
- `mv src dst` - Move/rename file
- `rm file` - Delete file (careful!)
- `rm -r folder` - Delete folder (careful!)

**Viewing Files:**

- `cat file` - Show file contents
- `less file` - View long file (Q to exit)
- `head file` - Show first lines
- `tail file` - Show last lines

**Helpful:**

- `clear` - Clear the screen
- `history` - Show command history
- `man command` - Show manual
- `--help` - Most commands support this

**Shortcuts:**

- Tab - Auto-complete
- Up/Down arrows - Navigate history
- Ctrl+C - Cancel command
- Ctrl+L - Clear screen

---

## Lesson 5: Practical Examples

### Example 1: Setting Up a Web Project

```bash
# Create project folder structure
$ mkdir -p my-website/css my-website/js my-website/images

# Go into the project
$ cd my-website

# Create the main files
$ touch index.html css/style.css js/script.js

# See what we created
$ ls -la
$ ls css/
$ ls js/
```

### Example 2: Backing Up Your Work

```bash
# Copy entire project folder
$ cp -r my-website my-website-backup

# Rename to add date
$ mv my-website-backup my-website-backup-2024-12-26
```

### Example 3: Finding and Cleaning Up

```bash
# See all files in current folder
$ ls -la

# Remove a file you don't need
$ rm old-file.txt

# Remove an empty folder
$ rmdir empty-folder

# Remove a folder with contents
$ rm -r old-project
```

---

## Lesson 6: Tab Completion and Shortcuts

### Tab Completion — Your Best Friend

Press **Tab** to auto-complete:

```bash
cd Doc[TAB] # Completes to: cd Documents/
ls Down[TAB] # Completes to: ls Downloads/
```

If there are multiple options, press **Tab twice** to see them all.

### Command History

| Action | How |
|--------|-----|
| Previous command | Press `↑` (up arrow) |
| Next command | Press `↓` (down arrow) |
| Search history | `Ctrl + R`, then type to search |
| See all history | Type `history` |

### Other Useful Shortcuts

| Shortcut | Action |
|----------|--------|
| `Ctrl + C` | Cancel current command |
| `Ctrl + L` | Clear screen |
| `Ctrl + A` | Jump to beginning of line |
| `Ctrl + E` | Jump to end of line |
| `Ctrl + U` | Delete line before cursor |
| `Ctrl + W` | Delete word before cursor |

---

## Self-Check Exercises

### Exercise 1: Navigation Practice

Open terminal and complete these steps:

```bash
# 1. Check where you are
pwd

# 2. List what's in your home folder
ls -la

# 3. Go to Documents
cd Documents

# 4. Check where you are now
pwd

# 5. Go back home
cd ~
```

### Exercise 2: Create a Project Structure

Create this folder structure for a web project:

```
my-first-website/
├── index.html
├── about.html
├── css/
│ └── style.css
├── js/
│ └── main.js
└── images/
```

**Commands to use:**

```bash
# Try yourself first, then check the answer:
mkdir -p my-first-website/css my-first-website/js my-first-website/images
cd my-first-website
touch index.html about.html css/style.css js/main.js
ls -la
```

### Exercise 3: Copy and Rename

1. Copy your `my-first-website` folder to `my-first-website-backup`
2. Rename `my-first-website-backup` to `backup-2024`

### Exercise 4: Clean Up

1. Create a folder called `temp`
2. Create a file inside called `test.txt`
3. Delete the file
4. Delete the folder

 Be careful with `rm`!

### Exercise 5: Speed Challenge

Using only the keyboard (Tab completion and shortcuts), navigate to three different directories and back to home in under 30 seconds.

---

## Module Summary

**Key Vocabulary**

| Term | Meaning |
|------|---------|
| Terminal | Text-based interface to control computer |
| Shell | The program that interprets your commands |
| Directory | Another word for folder |
| Path | The location of a file or folder |
| Root | The top of the file system (`/`) |
| Home | Your personal folder (`~` or `/home/username`) |

**Commands Learned**

| Category | Commands |
|----------|----------|
| Navigation | `pwd`, `ls`, `cd` |
| Files/Folders | `mkdir`, `touch`, `cp`, `mv`, `rm` |
| Viewing | `cat`, `less`, `head`, `tail` |
| Help | `man`, `--help`, `history` |

---

## Next Steps

**Before moving to Module 04:**

- [ ] Complete all exercises without looking at answers
- [ ] Practice navigation until it feels natural
- [ ] Create at least 3 project folder structures
- [ ] Get mentor verification

**Coming Next**: Module 04 - File Management & Organization

*You will learn best practices for organizing your files and projects!*

---

<div align="center">

**The terminal is your superpower!**

*Practice every day. Soon it will feel natural.*

</div>
