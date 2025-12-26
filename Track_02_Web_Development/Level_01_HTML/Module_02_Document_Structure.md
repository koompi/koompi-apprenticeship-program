# Module 02: HTML Document Structure

## Level 2.1: HTML Fundamentals

---

## 🎯 Module Objectives

By the end of this module, you will be able to:

- Understand the complete structure of HTML documents
- Use the DOCTYPE declaration correctly
- Work with `<html>`, `<head>`, and `<body>` elements
- Add metadata and configure your pages properly

---

## Lesson 1: The Complete HTML5 Structure

### Every HTML Page Has This Structure

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <!-- Metadata goes here (not visible) -->
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Page Title</title>
</head>
<body>
    <!-- Visible content goes here -->
</body>
</html>
```

### Visual Representation

```
┌─────────────────────────────────────────────────────────────────────────────┐
│  <!DOCTYPE html>  ← Declaration (tells browser this is HTML5)              │
├─────────────────────────────────────────────────────────────────────────────┤
│  <html lang="en">  ← Root element (contains everything)                    │
│  ├─────────────────────────────────────────────────────────────────────┐   │
│  │  <head>  ← Metadata container (invisible info)                      │   │
│  │  │                                                                   │   │
│  │  │  <meta charset="UTF-8">                                          │   │
│  │  │  <meta name="viewport" content="...">                            │   │
│  │  │  <title>Page Title</title>                                       │   │
│  │  │  <link rel="stylesheet" href="style.css">                       │   │
│  │  │                                                                   │   │
│  │  </head>                                                             │   │
│  ├─────────────────────────────────────────────────────────────────────┤   │
│  │  <body>  ← Content container (visible content)                      │   │
│  │  │                                                                   │   │
│  │  │  <h1>Welcome</h1>                                                │   │
│  │  │  <p>This is visible on the page!</p>                            │   │
│  │  │                                                                   │   │
│  │  </body>                                                             │   │
│  └─────────────────────────────────────────────────────────────────────┘   │
│  </html>                                                                    │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## Lesson 2: The DOCTYPE Declaration

### What is DOCTYPE?

The `<!DOCTYPE html>` declaration:

- Tells the browser which version of HTML to expect
- Must be the **very first line** (no spaces or comments before it)
- Is NOT case-sensitive (but lowercase is convention)
- Is NOT an HTML tag

### Why It Matters

Without DOCTYPE, browsers enter **"quirks mode"** — they try to guess how to display the page, often incorrectly.

With DOCTYPE, browsers use **"standards mode"** — they follow modern web standards.

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                    QUIRKS MODE vs STANDARDS MODE                             │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│   WITHOUT DOCTYPE                        WITH DOCTYPE                        │
│   ═══════════════                        ═════════════                        │
│                                                                              │
│   ❌ Quirks Mode                          ✅ Standards Mode                   │
│   • Unpredictable behavior               • Consistent behavior               │
│   • Different across browsers            • Same across browsers              │
│   • Old CSS bugs                         • Modern CSS support                │
│   • Harder to debug                      • Easier to debug                   │
│                                                                              │
└─────────────────────────────────────────────────────────────────────────────┘
```

### Modern HTML5 DOCTYPE

```html
<!DOCTYPE html>
```

This simple declaration is all you need for HTML5. Previous versions had longer, complex DOCTYPEs.

---

## Lesson 3: The `<html>` Element

### The Root Element

Everything in your HTML document (except DOCTYPE) goes inside the `<html>` element.

```html
<html lang="en">
    <!-- All other elements go here -->
</html>
```

### The `lang` Attribute

The `lang` attribute specifies the primary language of the document.

| Code | Language |
|------|----------|
| `en` | English |
| `km` | Khmer (ភាសាខ្មែរ) |
| `zh` | Chinese |
| `ja` | Japanese |
| `th` | Thai |

**Why use `lang`?**

- Screen readers use it to pronounce words correctly
- Search engines use it for language-specific results
- Translation tools detect the language
- Required for accessibility

### Khmer Language Example

```html
<!DOCTYPE html>
<html lang="km">
<head>
    <meta charset="UTF-8">
    <title>គេហទំព័រខ្មែរ</title>
</head>
<body>
    <h1>សួស្តី ពិភពលោក!</h1>
    <p>នេះគឺជាទំព័រដំបូងរបស់ខ្ញុំ។</p>
</body>
</html>
```

---

## Lesson 4: The `<head>` Element

### Metadata Container

The `<head>` contains information **about** the page, not the page content itself. Nothing in `<head>` is visible on the page (except `<title>` in the browser tab).

### Essential Head Elements

```html
<head>
    <!-- Character encoding - ALWAYS include first -->
    <meta charset="UTF-8">
    
    <!-- Responsive design - ALWAYS include -->
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    
    <!-- Page title - ALWAYS include -->
    <title>Your Page Title</title>
    
    <!-- Description for search engines -->
    <meta name="description" content="A brief description of your page">
    
    <!-- Link to CSS stylesheet -->
    <link rel="stylesheet" href="css/style.css">
    
    <!-- Favicon (icon in browser tab) -->
    <link rel="icon" href="favicon.ico">
</head>
```

### Understanding Each Element

#### `<meta charset="UTF-8">`

Defines character encoding. UTF-8 supports all characters including:

- English: Hello
- Khmer: សួស្តី
- Chinese: 你好
- Emoji: 😀

**Always put this first** in your `<head>`.

#### `<meta name="viewport">`

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

Makes your page work on mobile devices:

- `width=device-width`: Use the device's width
- `initial-scale=1.0`: Start at 100% zoom

#### `<title>`

```html
<title>KOOMPI - Technology for Everyone</title>
```

The title appears:

- In the browser tab
- In bookmarks
- In search engine results
- When sharing on social media

**Good titles:**

- Are descriptive
- Are 50-60 characters
- Include the page topic and site name

| Bad ❌ | Good ✅ |
|-------|---------|
| `index` | `Home - KOOMPI Apprenticeship` |
| `My Page` | `About Me - Sokha's Portfolio` |
| `Page 1` | `Getting Started with HTML - Tutorial` |

---

## Lesson 5: The `<body>` Element

### Content Container

The `<body>` contains everything users see and interact with.

```html
<body>
    <header>
        <!-- Site header, navigation -->
    </header>
    
    <main>
        <!-- Main content -->
    </main>
    
    <footer>
        <!-- Site footer -->
    </footer>
</body>
```

### Common Body Elements (Preview)

| Element | Purpose |
|---------|---------|
| `<header>` | Page or section header |
| `<nav>` | Navigation links |
| `<main>` | Main content (use only once) |
| `<article>` | Self-contained content |
| `<section>` | Thematic grouping |
| `<aside>` | Sidebar content |
| `<footer>` | Page or section footer |

### Semantic HTML

**Semantic** means "meaningful." Using the right tags helps:

- Screen readers navigate the page
- Search engines understand content
- Developers read the code

```html
<!-- Non-semantic (bad) -->
<div id="header">
    <div id="nav">Links here</div>
</div>

<!-- Semantic (good) -->
<header>
    <nav>Links here</nav>
</header>
```

---

## Lesson 6: HTML Comments

### What Are Comments?

Comments are notes in your code that browsers ignore. Only developers see them.

```html
<!-- This is a comment -->
```

### Using Comments

```html
<body>
    <!-- Main Navigation -->
    <nav>
        <a href="index.html">Home</a>
        <a href="about.html">About</a>
    </nav>
    
    <!-- Main Content Section -->
    <main>
        <h1>Welcome</h1>
        
        <!-- TODO: Add more content here -->
        
    </main>
    
    <!-- Footer -->
    <footer>
        <p>© 2024 KOOMPI</p>
    </footer>
</body>
```

### Comment Best Practices

| Do ✅ | Don't ❌ |
|-------|----------|
| Mark sections | Comment obvious code |
| Leave TODO notes | Write novels in comments |
| Explain complex parts | Leave debugging comments in final code |

---

## Lesson 7: Complete Page Template

### Your Starting Template

Save this as your template for new projects:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <!-- Character encoding -->
    <meta charset="UTF-8">
    
    <!-- Responsive design -->
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    
    <!-- Page info -->
    <title>Page Title - Site Name</title>
    <meta name="description" content="Brief description of this page">
    
    <!-- Styles -->
    <link rel="stylesheet" href="css/style.css">
</head>
<body>
    <!-- Header -->
    <header>
        <nav>
            <a href="index.html">Home</a>
            <a href="about.html">About</a>
            <a href="contact.html">Contact</a>
        </nav>
    </header>
    
    <!-- Main Content -->
    <main>
        <h1>Page Heading</h1>
        <p>Page content goes here.</p>
    </main>
    
    <!-- Footer -->
    <footer>
        <p>© 2024 Your Name. All rights reserved.</p>
    </footer>
    
    <!-- Scripts (if needed) -->
    <script src="js/main.js"></script>
</body>
</html>
```

---

## 🧪 Self-Check Exercises

### Exercise 1: Structure Quiz

Answer these questions:

1. What must be the first line of every HTML file?
2. What are the two main sections inside `<html>`?
3. What goes in `<head>`?
4. What goes in `<body>`?
5. Why do we use `lang="en"` or `lang="km"`?

### Exercise 2: Fix the Errors

This code has errors. Find and fix them:

```html
<html>
<head>
<body>
    <h1>My Page</h1>
</body>
</head>
</html>
```

**Errors to find:**

1. Missing DOCTYPE
2. Missing `<title>`
3. Missing `<meta charset>`
4. Tags in wrong order

### Exercise 3: Create Multi-Language Pages

Create two pages:

**english.html:**

```html
<!-- Create a page in English with lang="en" -->
<!-- Title: Welcome -->
<!-- Content: A greeting and introduction -->
```

**khmer.html:**

```html
<!-- Create a page in Khmer with lang="km" -->
<!-- Title: សួស្តី -->
<!-- Content: A greeting and introduction in Khmer -->
```

### Exercise 4: Add Metadata

Take one of your pages and add:

1. A proper `<title>` (descriptive)
2. A `<meta name="description">` tag
3. Proper comments marking each section

### Exercise 5: Build From Memory

Without looking at notes, create a complete HTML page structure including:

- DOCTYPE
- html with lang
- head with charset, viewport, title
- body with header, main, footer
- Comments marking each section

---

## 📝 Module Summary

**Key Vocabulary**

| Term | Meaning |
|------|---------|
| DOCTYPE | Declaration that specifies HTML version |
| Root element | The `<html>` element containing everything |
| Metadata | Information about the page (in head) |
| Semantic | Using meaningful, descriptive tags |
| Character encoding | System for representing characters (UTF-8) |

**Structure Summary**

```
<!DOCTYPE html>
├── <html lang="en">
│   ├── <head>
│   │   ├── <meta charset="UTF-8">
│   │   ├── <meta name="viewport">
│   │   ├── <title>
│   │   └── <link>, <meta>, etc.
│   │
│   └── <body>
│       ├── <header>
│       ├── <main>
│       └── <footer>
│
└── </html>
```

---

## 🎯 Next Steps

**Before moving to Module 03:**

- [ ] Complete all exercises
- [ ] Create the template file
- [ ] Build English and Khmer pages
- [ ] Get mentor verification

**Coming Next**: Module 03 - Text Content & Lists

*You will learn to structure text with headings, paragraphs, and lists!*

---

<div align="center">

**Great structure = Great websites!** 🏗️

*Every professional website starts with proper structure.*

</div>
