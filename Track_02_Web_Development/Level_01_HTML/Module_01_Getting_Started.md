# Module 01: Getting Started with Web Development

## Level 2.1: HTML Fundamentals

---

## Module Objectives

By the end of this module, you will be able to:

- Understand how the internet and websites work
- Explain what HTML is and why it matters
- Set up your development environment
- Create and view your first HTML page

---

## Lesson 1: What is the Internet and How Websites Work

### The Internet: A Global Network

The **Internet** is a global network of interconnected computers that allows users to share information and communicate. Think of it as millions of computers talking to each other.

```
┌─────────────────────────────────────────────────────────────────────────────┐
│ HOW THE INTERNET WORKS │
├─────────────────────────────────────────────────────────────────────────────┤
│ │
│ │
│ Your Computer Website Server │
│ (CLIENT) (SERVER) │
│ │
│ ─────── "I want google.com" ───────▶ │
│ ◀────── sends google.com page ────── │
│ │
│ │
│ The CLIENT asks for information │
│ The SERVER sends the information │
│ │
└─────────────────────────────────────────────────────────────────────────────┘
```

### Key Concepts

#### Client-Server Model

| Role | What it is | Examples |
|------|------------|----------|
| **Client** | Your device that requests information | Your computer, phone, tablet |
| **Server** | A computer that stores and sends website files | Google's servers, KOOMPI's servers |
| **Browser** | Software that displays websites | Chrome, Firefox, Safari |

#### IP Addresses & Domain Names

Every computer on the internet has an address:

| Term | What it is | Example |
|------|------------|---------|
| **IP Address** | Numerical address of a computer | `142.250.190.46` |
| **Domain Name** | Human-readable name | `google.com` |
| **DNS** | System that translates domains to IPs | Like a phonebook |

**Example**: When you type `google.com`, DNS translates it to `142.250.190.46`, then your browser connects to that server.

#### What Browsers Do

When you visit a website, your browser:

1. Takes your request (URL you typed)
2. Finds the server using DNS
3. Downloads the files (HTML, CSS, images)
4. **Renders** (displays) the page for you

---

## Lesson 2: Introduction to HTML

### What is HTML?

**HTML** stands for **HyperText Markup Language**.

- **HyperText**: Text with links to other content
- **Markup**: A way to annotate text for structure
- **Language**: A set of rules computers understand

```
┌─────────────────────────────────────────────────────────────────────────────┐
│ HTML IS LIKE A SKELETON │
├─────────────────────────────────────────────────────────────────────────────┤
│ │
│ HTML + CSS + JavaScript = WEBSITE │
│ (Structure) (Appearance) (Behavior) (Complete) │
│ │
│ │
│ Skeleton Skin/Clothes Movement Living Being │
│ │
│ Defines what Makes it look Makes it The final │
│ content exists beautiful interactive result │
│ │
└─────────────────────────────────────────────────────────────────────────────┘
```

### HTML Tags

HTML uses **tags** to define content. Tags are keywords inside angle brackets.

```html
<tagname>Content goes here</tagname>
```

**Parts of an Element:**

```html
<p>This is a paragraph.</p>
│ │ │
│ │ └── Closing Tag
│ └── Content
└── Opening Tag
```

| Part | Description | Example |
|------|-------------|---------|
| Opening Tag | Starts the element | `<p>` |
| Content | What appears on page | `This is a paragraph.` |
| Closing Tag | Ends the element (has `/`) | `</p>` |

### Self-Closing Tags

Some elements don't have content, so they close themselves:

```html
<img src="photo.jpg" alt="A photo">
<br>
<hr>
```

---

## Lesson 3: Setting Up Your Development Environment

### What You Need

To create websites, you need:

1. **Text Editor** — To write code
2. **Web Browser** — To view your work

### Text Editor: Visual Studio Code

**VS Code** is the most popular code editor for web development.

**Installing VS Code on KOOMPI:**

```bash
# Ask your mentor if VS Code is already installed
# Or install using your package manager
```

If VS Code is already installed, open it:

```bash
code .
```

**Why VS Code?**

- Free and open-source
- Syntax highlighting (colors your code)
- Auto-completion (suggests code as you type)
- Extensions for extra features
- Used by millions of developers

### Web Browser

Use **Firefox** or **Chromium** (included in KOOMPI) to view your websites.

**Important feature: Developer Tools (DevTools)**

- Right-click on any webpage → "Inspect" or press `F12`
- See the HTML structure of any website
- Very useful for learning and debugging

---

## Lesson 4: Your First HTML Page - "Hello World"

### Create Your First Website

**Step 1: Create project folder**

```bash
cd ~/projects/learning/html-fundamentals
mkdir hello-world
cd hello-world
```

**Step 2: Create the HTML file**

```bash
touch index.html
```

**Step 3: Open in VS Code**

```bash
code index.html
```

**Step 4: Type this code**

```html
<!DOCTYPE html>
<html lang="en">
<head>
 <meta charset="UTF-8">
 <meta name="viewport" content="width=device-width, initial-scale=1.0">
 <title>My First Webpage</title>
</head>
<body>
 <h1>Hello World!</h1>
 <p>This is my very first HTML page.</p>
 <p>I am learning web development at KOOMPI.</p>
</body>
</html>
```

**Step 5: Save the file**
Press `Ctrl + S`

**Step 6: View in browser**

Option 1: Open file manager, navigate to your folder, double-click `index.html`

Option 2: In terminal:

```bash
firefox index.html
# or
xdg-open index.html
```

### Congratulations! You've built your first webpage

---

## Lesson 5: Understanding the Code

Let's break down each part of your first HTML page:

### `<!DOCTYPE html>`

```html
<!DOCTYPE html>
```

- Not an HTML tag, but a **declaration**
- Tells the browser: "This is an HTML5 document"
- Must be the **first line** of every HTML file

### `<html>` Element

```html
<html lang="en">
 ...
</html>
```

- The **root element** (everything goes inside)
- `lang="en"` tells browsers the language is English
- Contains `<head>` and `<body>`

### `<head>` Element

```html
<head>
 <meta charset="UTF-8">
 <meta name="viewport" content="width=device-width, initial-scale=1.0">
 <title>My First Webpage</title>
</head>
```

Contains **metadata** (information about the page, not visible content):

| Element | Purpose |
|---------|---------|
| `<meta charset="UTF-8">` | Allows all characters, including Khmer ខ្មែរ |
| `<meta name="viewport">` | Makes page work on mobile devices |
| `<title>` | Shows in browser tab |

### `<body>` Element

```html
<body>
 <h1>Hello World!</h1>
 <p>This is my very first HTML page.</p>
 <p>I am learning web development at KOOMPI.</p>
</body>
```

Contains **visible content** — what users see:

| Element | Purpose |
|---------|---------|
| `<h1>` | Main heading (biggest) |
| `<p>` | Paragraph of text |

---

## Lesson 6: Using Browser Developer Tools

### Why DevTools?

Developer Tools let you:

- See the HTML structure of any webpage
- Find and fix problems in your code
- Learn how other websites are built
- Test changes without breaking your files

### Opening DevTools

| Browser | Shortcut |
|---------|----------|
| Firefox | `F12` or `Ctrl + Shift + I` |
| Chrome | `F12` or `Ctrl + Shift + I` |

Or: Right-click anywhere on page → "Inspect"

### DevTools Panels

```
┌─────────────────────────────────────────────────────────────────────────────┐
│ DEVELOPER TOOLS PANELS │
├─────────────────────────────────────────────────────────────────────────────┤
│ │
│ ELEMENTS PANEL (or "Inspector" in Firefox) │
│ ───────────────────────────────────────── │
│ • See all HTML elements │
│ • Click to select elements on page │
│ • Edit HTML temporarily │
│ • Most important for HTML learning! │
│ │
│ CONSOLE PANEL │
│ ───────────── │
│ • Shows errors (very useful!) │
│ • Run JavaScript (later) │
│ │
│ NETWORK PANEL │
│ ───────────── │
│ • See all files being loaded │
│ • Loading times │
│ │
└─────────────────────────────────────────────────────────────────────────────┘
```

### Practice: Inspect Your Page

1. Open your "Hello World" page in browser
2. Press `F12` to open DevTools
3. Click on the `<h1>` element in the Elements panel
4. Notice it highlights on the page
5. Try double-clicking to edit the text (temporary change)

---

## Lesson 7: Essential Web Terminology

### Key Terms You Must Know

```
┌─────────────────────────────────────────────────────────────────────────────┐
│ WEB DEVELOPMENT VOCABULARY │
├─────────────────────────────────────────────────────────────────────────────┤
│ │
│ TAG │
│ ─── │
│ The markers that define elements │
│ Example: <p>, </p>, <h1> │
│ │
│ ELEMENT │
│ ─────── │
│ The complete unit: opening tag + content + closing tag │
│ Example: <p>This is a paragraph.</p> │
│ │
│ ATTRIBUTE │
│ ───────── │
│ Extra information in the opening tag │
│ Format: name="value" │
│ Example: <html lang="en"> ← 'lang' is an attribute │
│ │
│ NESTING │
│ ─────── │
│ Putting elements inside other elements │
│ Example: <body><p>Text</p></body> │
│ (p is nested inside body) │
│ │
│ VOID ELEMENT │
│ ──────────── │
│ Elements that don't have closing tags │
│ Example: <img>, <br>, <hr> │
│ │
└─────────────────────────────────────────────────────────────────────────────┘
```

### Example with All Parts

```html
<a href="https://koompi.com" target="_blank">Visit KOOMPI</a>
 │ │ │ │
 │ │ │ └── Content
 │ │ └── Second Attribute
 │ └── First Attribute Value
 └── Tag Name
```

- **Element**: The entire line
- **Tag**: `<a>` (opening) and `</a>` (closing)
- **Attributes**: `href` and `target`
- **Content**: "Visit KOOMPI"

---

## Self-Check Exercises

### Exercise 1: Vocabulary Quiz

Answer these questions:

1. What does HTML stand for?
2. What's the difference between a tag and an element?
3. What does the `<head>` section contain?
4. What does the `<body>` section contain?
5. What is an attribute? Give an example.

### Exercise 2: Code From Memory

Without looking at notes, create a new HTML file called `practice.html` with:

- Correct DOCTYPE
- HTML element with language attribute
- Head with title "My Practice Page"
- Body with one heading and two paragraphs

### Exercise 3: Explore with DevTools

1. Open `https://koompi.com` in your browser
2. Open Developer Tools (F12)
3. Find the main heading of the page
4. What tag is it using?
5. Can you find any images? What are their `src` attributes?

### Exercise 4: Experiment

Take your "Hello World" page and:

1. Change the title
2. Add a third paragraph
3. Change the heading text
4. Save and refresh to see changes

### Exercise 5: Create "About Me" Page

Create a new file `about-me.html` with:

- Your name as the main heading
- A paragraph about where you're from
- A paragraph about what you want to learn
- A paragraph about your goals

---

## Module Summary

**Key Vocabulary**

| English | Khmer | Meaning |
|---------|-------|---------|
| Internet | អ៊ីនធឺណិត | Global network of computers |
| Browser | កម្មវិធីរុករក | Software to view websites |
| Tag | ស្លាក | Markers defining HTML elements |
| Element | ធាតុ | Complete HTML component |
| Attribute | គុណលក្ខណៈ | Extra information in tags |

**What You Learned**

- How the internet works (client-server)
- What HTML is and its role in websites
- Setting up VS Code for development
- Creating your first HTML page
- Using browser DevTools
- HTML terminology: tags, elements, attributes

---

## Next Steps

**Before moving to Module 02:**

- [ ] Complete all self-check exercises
- [ ] Create the "About Me" page
- [ ] Explore at least 3 websites using DevTools
- [ ] Get mentor verification

**Coming Next**: Module 02 - HTML Document Structure

*You will learn the complete structure of HTML documents and semantic elements!*

---

<div align="center">

**You've taken your first step!** 

*The journey of a web developer begins with "Hello World"*

</div>
