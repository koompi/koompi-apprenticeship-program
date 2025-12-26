# Module 04: File Management & Organization

## Track 00: Digital Foundations

---

## Module Objectives

By the end of this module, you will be able to:

- Organize files and folders like a professional developer
- Use consistent naming conventions
- Manage projects efficiently
- Keep your digital workspace clean and productive

---

## Lesson 1: Why Organization Matters

### The Cost of Disorganization

```
┌─────────────────────────────────────────────────────────────────────────────┐
│ ORGANIZED vs DISORGANIZED │
├─────────────────────────────────────────────────────────────────────────────┤
│ │
│ DISORGANIZED DEVELOPER ORGANIZED DEVELOPER │
│ ══════════════════════ ════════════════════ │
│ │
│ Desktop/ projects/ │
│ ├── final_v2_FINAL.html ├── koompi-website/ │
│ ├── test.html │ ├── index.html │
│ ├── asdfasdf.js │ ├── css/ │
│ ├── project(1).zip │ │ └── style.css │
│ ├── IMG_20241226.jpg │ └── js/ │
│ ├── New folder/ │ └── main.js │
│ ├── New folder (2)/ └── portfolio/ │
│ └── untitled.txt ├── index.html │
│ └── css/ │
│ Can't find anything Easy to navigate │
│ Wastes time searching Saves hours │
│ Looks unprofessional Shows competence │
│ Hard to share with team Team-friendly │
│ │
└─────────────────────────────────────────────────────────────────────────────┘
```

### Benefits of Good Organization

| Benefit | Explanation |
|---------|-------------|
| **Save Time** | Find files in seconds, not minutes |
| **Reduce Stress** | Know exactly where everything is |
| **Collaborate Better** | Others can understand your structure |
| **Professional Image** | Shows you're a serious developer |
| **Version Control Ready** | Organized projects work better with Git |

---

## Lesson 2: Standard Project Structure

### Web Project Structure

Every web project should follow a similar pattern:

```
project-name/
├── index.html ← Main homepage
├── about.html ← Other HTML pages
├── contact.html
│
├── css/ ← All stylesheets
│ ├── style.css ← Main styles
│ ├── reset.css ← CSS reset (optional)
│ └── responsive.css ← Mobile styles (optional)
│
├── js/ ← All JavaScript files
│ ├── main.js ← Main script
│ └── utils.js ← Helper functions (optional)
│
├── images/ ← All images
│ ├── logo.png
│ ├── hero-banner.jpg
│ └── icons/ ← Subfolder for icons
│ ├── menu.svg
│ └── close.svg
│
├── fonts/ ← Custom fonts (if any)
│
└── README.md ← Project description
```

### Why This Structure?

| Folder | Purpose |
|--------|---------|
| Root (`/`) | HTML files and README |
| `css/` | Keeps styles separate and organized |
| `js/` | Keeps scripts separate |
| `images/` | All visual assets together |
| `fonts/` | Custom typography files |

---

## Lesson 3: File Naming Conventions

### Rules for Naming Files

```
┌─────────────────────────────────────────────────────────────────────────────┐
│ FILE NAMING BEST PRACTICES │
├─────────────────────────────────────────────────────────────────────────────┤
│ │
│ DO DON'T │
│ ═════ ═══════ │
│ │
│ Use lowercase Use UPPERCASE or MixedCase │
│ index.html Index.HTML │
│ │
│ Use hyphens for spaces Use spaces │
│ my-project.html my project.html │
│ │
│ Use underscores for multi-word Use special characters │
│ user_profile.js user@profile!.js │
│ │
│ Be descriptive Be vague │
│ contact-form.css style2.css │
│ │
│ Use proper extensions Forget extensions │
│ script.js script │
│ │
│ Keep it short but clear Use very long names │
│ nav-menu.css navigation-menu-styles-v2.css │
│ │
└─────────────────────────────────────────────────────────────────────────────┘
```

### Naming Patterns

| Type | Convention | Example |
|------|------------|---------|
| HTML pages | lowercase, hyphens | `about-us.html` |
| CSS files | lowercase, hyphens | `main-styles.css` |
| JavaScript | camelCase or hyphens | `formValidation.js` or `form-validation.js` |
| Images | lowercase, descriptive | `hero-banner.jpg` |
| Folders | lowercase, hyphens | `user-images/` |

### Bad vs Good Examples

| Bad | Good | Why |
|--------|---------|-----|
| `My Page.html` | `my-page.html` | No spaces, lowercase |
| `STYLE.CSS` | `style.css` | Lowercase |
| `sdfljk.js` | `form-handler.js` | Descriptive name |
| `image (1).png` | `profile-photo.png` | Clear purpose |
| `finalFINAL_v2.html` | `index.html` | Use version control instead |

---

## Lesson 4: Organizing Your Home Directory

### Recommended Folder Structure

Set up your home directory for success:

```
/home/student/
│
├── Documents/ ← General documents
│ ├── notes/ ← Learning notes
│ ├── certificates/ ← Earned certificates
│ └── resources/ ← Downloaded resources
│
├── projects/ ← ALL coding projects go here
│ ├── learning/ ← Practice projects
│ │ ├── html-practice/
│ │ ├── css-exercises/
│ │ └── js-basics/
│ ├── portfolio/ ← Your personal portfolio
│ └── client-work/ ← Real projects (later)
│
├── Downloads/ ← Temporary downloads
│ ← Clean this regularly!
│
└── Desktop/ ← Keep almost empty!
 └── (only shortcuts)
```

### Setting Up Your Workspace

**Run these commands to set up:**

```bash
# Go home
cd ~

# Create the structure
mkdir -p projects/learning
mkdir -p projects/portfolio
mkdir -p projects/client-work
mkdir -p Documents/notes
mkdir -p Documents/certificates
mkdir -p Documents/resources

# Verify
ls -la projects/
```

---

## Lesson 5: File Management Best Practices

### Daily Habits

```
┌─────────────────────────────────────────────────────────────────────────────┐
│ DAILY FILE MANAGEMENT HABITS │
├─────────────────────────────────────────────────────────────────────────────┤
│ │
│ START OF DAY │
│ ─────────────── │
│ • Open terminal, check your projects folder │
│ • Know what you're working on today │
│ │
│ DURING WORK │
│ ───────────── │
│ • Save files frequently (Ctrl+S) │
│ • Keep files in the right folders │
│ • Name files clearly immediately │
│ │
│ END OF DAY │
│ ─────────── │
│ • Clean up Downloads folder │
│ • Delete temporary/test files │
│ • Make sure work is saved │
│ │
│ WEEKLY │
│ ──────── │
│ • Clear trash │
│ • Review and organize Desktop │
│ • Back up important work │
│ │
└─────────────────────────────────────────────────────────────────────────────┘
```

### The Downloads Folder Problem

Your Downloads folder is a **temporary zone**, not storage!

**Rule**: After downloading something:

1. If you need it → Move it to the right folder
2. If you don't need it → Delete it
3. Never leave files there for more than 1 week

### README Files

Every project should have a `README.md` file that explains:

```markdown
# Project Name

## Description
What does this project do?

## Setup
How to run this project?

## Files
- index.html - Main page
- css/style.css - Styles
- js/main.js - JavaScript

## Author
Your name

## Date
When you created this
```

---

## Lesson 6: Using the File Manager (GUI)

### Terminal + File Manager Together

While the terminal is powerful, the file manager is helpful for:

- Viewing images
- Quick drag-and-drop operations
- Visual overview of folders

### File Manager Features

| Feature | How to Use | When to Use |
|---------|------------|-------------|
| **Navigate** | Click on folders | Browsing |
| **Create Folder** | Right-click → New Folder | Organizing |
| **Rename** | Right-click → Rename or F2 | Fixing names |
| **Delete** | Right-click → Delete or Delete key | Cleaning up |
| **View Hidden** | Ctrl+H | Seeing dotfiles |
| **Open Terminal** | Right-click → Open in Terminal | Quick access |

### Keyboard Shortcuts in File Manager

| Shortcut | Action |
|----------|--------|
| `Ctrl + H` | Show/hide hidden files |
| `Ctrl + L` | Type path directly |
| `F2` | Rename selected item |
| `Delete` | Move to trash |
| `Shift + Delete` | Permanent delete (careful!) |
| `Ctrl + Shift + N` | Create new folder |

---

## Self-Check Exercises

### Exercise 1: Create Standard Web Project

Create a properly structured web project:

```bash
mkdir -p ~/projects/learning/my-portfolio
cd ~/projects/learning/my-portfolio
mkdir css js images
touch index.html about.html css/style.css js/main.js README.md
ls -la
```

### Exercise 2: Fix Bad Names

Rename these badly named files (pretend they exist):

| Bad Name | Good Name | Command |
|----------|-----------|---------|
| `My Page.html` | ? | `mv "My Page.html" ?` |
| `STYLES.CSS` | ? | |
| `image (1).png` | ? | |
| `sdfsd.js` | ? | |

**Think of good names first, then practice the commands.**

### Exercise 3: Organize Downloads

1. Go to your Downloads folder
2. List all files
3. Identify what should be moved or deleted
4. Create proper folders for files you want to keep
5. Move files to correct locations
6. Delete files you don't need

### Exercise 4: Create a README

Create a README.md for a project with this content:

```markdown
# My First Website

## Description
A simple personal website to practice HTML and CSS.

## Files
- index.html - Homepage
- about.html - About me page
- css/style.css - All styles

## Author
[Your Name]

## Created
December 2024
```

### Exercise 5: Weekly Cleanup

Perform a complete cleanup:

- [ ] Clean Downloads folder
- [ ] Clear Desktop of unnecessary files
- [ ] Empty Trash
- [ ] Verify projects folder is organized
- [ ] Create any missing folders in your structure

---

## Module Summary

**Key Concepts**

| Concept | Meaning |
|---------|---------|
| File Structure | How folders and files are organized |
| Naming Convention | Rules for naming files consistently |
| README | Documentation file explaining a project |
| Home Directory | Your personal folder (~ or /home/username) |

**Best Practices Learned**

- Standard web project structure
- Lowercase, hyphenated file names
- Organized home directory
- Daily and weekly cleanup habits
- README documentation

---

## Track 00 Complete

**Congratulations!** You have completed Track 00: Digital Foundations.

**Skills You Now Have:**

- Computer basics and KOOMPI OS navigation
- Touch typing with proper finger placement
- Linux terminal commands
- Professional file organization

**Next Steps:**

1. Ensure 30+ WPM typing speed
2. Complete all module exercises
3. Get mentor verification
4. **Begin Track 02: Web Development (HTML)**

---

## Ready for Certification?

**Digital Citizen Certificate Requirements:**

- [ ] All Track 00 modules completed
- [ ] Can type 30+ WPM in English
- [ ] Can navigate terminal with basic commands
- [ ] Files and folders are properly organized
- [ ] Mentor verification received

**When ready**, ask your mentor to verify your skills and award your **Digital Citizen** certificate!

---

<div align="center">

**You're ready to start building websites!** 

*Track 02: Web Development awaits you.*

</div>
