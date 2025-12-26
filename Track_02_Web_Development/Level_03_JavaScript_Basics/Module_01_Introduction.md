# Module 01: Introduction to JavaScript

## Level 2.3: JavaScript Basics

---

## Module Objectives

By the end of this module, you will be able to:

- Understand what JavaScript is and why it's important
- Use the browser console
- Add JavaScript to your web pages
- Write your first JavaScript code

---

## Lesson 1: What is JavaScript?

### JavaScript Defined

```
┌─────────────────────────────────────────────────────────────────────────────┐
│ THE WEB DEVELOPMENT TRIO (REVISITED) │
├─────────────────────────────────────────────────────────────────────────────┤
│ │
│ HTML CSS JavaScript │
│ ═══════ ═══════ ══════════ │
│ │
│ │
│ STRUCTURE STYLE BEHAVIOR │
│ │
│ "What's here" "How it looks" "What it does" │
│ │
│ The skeleton The appearance The brains │
│ │
│ HTML = Nouns CSS = Adjectives JavaScript = Verbs │
│ (Things) (Descriptions) (Actions) │
│ │
└─────────────────────────────────────────────────────────────────────────────┘
```

### What JavaScript Can Do

| Action | Example |
|--------|---------|
| **Respond to events** | When user clicks a button |
| **Change HTML content** | Update text without reloading |
| **Change CSS styles** | Toggle dark mode |
| **Validate forms** | Check if email is valid |
| **Create animations** | Smooth scrolling |
| **Communicate with servers** | Load new data |
| **Store data locally** | Remember user preferences |

### JavaScript is Everywhere

- **Websites** — Every interactive website uses JavaScript
- **Web apps** — Gmail, Google Docs, Facebook
- **Mobile apps** — React Native apps
- **Servers** — Node.js
- **Desktop apps** — Electron apps (VS Code!)
- **Games** — Browser games

---

## Lesson 2: The Browser Console

### Opening the Console

The console is where you can test JavaScript immediately.

**How to open:**

- **Chrome/Edge**: Right-click → Inspect → Console tab
- Or press `F12` → Console tab
- Or press `Ctrl + Shift + J` (Windows/Linux)
- Or press `Cmd + Option + J` (Mac)

### Your First JavaScript

Type this in the console and press Enter:

```javascript
console.log("Hello, Cambodia!");
```

You should see: `Hello, Cambodia!`

### Console Methods

| Command | What it does |
|---------|--------------|
| `console.log()` | Print a message |
| `console.warn()` | Print a warning (yellow) |
| `console.error()` | Print an error (red) |
| `console.clear()` | Clear the console |

### Try These

```javascript
// Print messages
console.log("I am learning JavaScript!");

// Do math
console.log(10 + 5);

// Print multiple things
console.log("My age:", 25);
```

---

## Lesson 3: Adding JavaScript to HTML

### Three Methods

Just like CSS, there are three ways to add JavaScript:

### Method 1: Inline (Not Recommended)

```html
<button onclick="alert('Hello!')">Click Me</button>
```

| Pros | Cons |
|------|------|
| Quick to write | Hard to maintain |
| | Mixes HTML and JS |
| | Not reusable |

### Method 2: Internal Script

```html
<!DOCTYPE html>
<html>
<head>
 <title>My Page</title>
</head>
<body>
 <h1>Hello World</h1>
 
 <script>
 console.log("Hello from internal script!");
 alert("Welcome to my page!");
 </script>
</body>
</html>
```

**Note**: Place `<script>` at the end of `<body>` so HTML loads first.

### Method 3: External File (Recommended!)

**script.js:**

```javascript
console.log("Hello from external file!");
alert("Welcome to my page!");
```

**index.html:**

```html
<!DOCTYPE html>
<html>
<head>
 <title>My Page</title>
</head>
<body>
 <h1>Hello World</h1>
 
 <script src="script.js"></script>
</body>
</html>
```

| Pros | Cons |
|------|------|
| Clean separation | Extra file to manage |
| Reusable across pages | |
| Cacheable by browser | |
| Easier to maintain | |

---

## Lesson 4: JavaScript Syntax Basics

### Statements

Statements are instructions. Each ends with a semicolon (;):

```javascript
console.log("Statement 1");
console.log("Statement 2");
console.log("Statement 3");
```

### Comments

Comments explain your code (ignored by browser):

```javascript
// This is a single-line comment

/*
This is a 
multi-line comment
*/

// Good comments explain WHY, not WHAT
console.log("Hello"); // Prints greeting - obvious, don't need this comment

// Check if user is admin before showing settings - good comment
```

### Case Sensitivity

JavaScript is **case-sensitive**:

```javascript
// These are ALL DIFFERENT:
let name = "Sokha";
let Name = "Dara";
let NAME = "Bopha";

// Common error:
console.log("Works");
Console.log("Error!"); // Console with capital C = error
```

### Common Errors

```javascript
// Unclosed string
console.log("Hello); // Missing closing quote

// Missing semicolon (usually okay, but can cause issues)
console.log("Hello")

// Typos in function names
consol.log("Hello"); // consol instead of console

// Using undefined variables
console.log(myName); // myName hasn't been defined
```

---

## Lesson 5: Basic Interactions

### Alert

Shows a popup message:

```javascript
alert("Hello, user!");
```

### Confirm

Shows popup with OK/Cancel, returns true/false:

```javascript
let result = confirm("Are you sure?");
console.log(result); // true if OK, false if Cancel
```

### Prompt

Shows popup asking for input:

```javascript
let name = prompt("What is your name?");
console.log("Hello, " + name + "!");
```

### Example: Interactive Welcome

```html
<!DOCTYPE html>
<html>
<head>
 <title>Welcome</title>
</head>
<body>
 <h1 id="greeting">Welcome!</h1>
 
 <script>
 let name = prompt("What is your name?");
 alert("Hello, " + name + "! Welcome to KOOMPI.");
 console.log(name + " visited the page.");
 </script>
</body>
</html>
```

---

## Lesson 6: Your First Project Setup

### Create Project Structure

```bash
mkdir javascript-practice
cd javascript-practice
touch index.html script.js
```

### index.html

```html
<!DOCTYPE html>
<html lang="en">
<head>
 <meta charset="UTF-8">
 <meta name="viewport" content="width=device-width, initial-scale=1.0">
 <title>JavaScript Practice</title>
 <style>
 body {
 font-family: Arial, sans-serif;
 padding: 20px;
 max-width: 800px;
 margin: 0 auto;
 }
 h1 {
 color: #333;
 }
 #output {
 background-color: #f0f0f0;
 padding: 20px;
 border-radius: 8px;
 min-height: 100px;
 }
 </style>
</head>
<body>
 <h1>JavaScript Practice</h1>
 
 <div id="output">
 <p>Output will appear here...</p>
 </div>
 
 <script src="script.js"></script>
</body>
</html>
```

### script.js

```javascript
// JavaScript Practice
console.log("JavaScript file loaded!");

// Your code here
```

---

## Lesson 7: Debugging Basics

### Reading Errors

When you make an error, check the console:

```
Uncaught SyntaxError: Unexpected token ')' at script.js:5
```

This tells you:

- **Error type**: SyntaxError
- **Problem**: Unexpected token ')'
- **Location**: script.js, line 5

### Common Beginner Errors

| Error | Cause | Fix |
|-------|-------|-----|
| `Unexpected token` | Typo or missing character | Check punctuation |
| `is not defined` | Using undeclared variable | Define the variable first |
| `is not a function` | Calling non-function | Check function name |
| `null` or `undefined` | Missing element or value | Check if element exists |

### Debugging Tips

1. **Read the error** — It tells you what's wrong
2. **Check the line number** — Look at that specific line
3. **Use console.log** — Print values to check them
4. **Comment out code** — Isolate the problem
5. **Search the error** — Google the exact message

---

## Self-Check Exercises

### Exercise 1: Console Practice

Open the console and try:

```javascript
console.log("Hello!");
console.log(2 + 2);
console.log("My name is " + "Sokha");
```

### Exercise 2: Alert Welcome

Create a page that:

1. Asks for user's name with prompt()
2. Shows an alert welcoming them
3. Logs the name to console

### Exercise 3: Calculator in Console

Use the console to calculate:

- 25 + 17
- 100 - 33
- 12 * 5
- 144 / 12

### Exercise 4: External Script

Create a project with:

- index.html
- script.js
- Make script.js log "JavaScript is working!"

### Exercise 5: Comments

Write a code file with:

- A single-line comment explaining what the file does
- A multi-line comment with your name and date
- Code that prints "Hello World"

---

## Module Summary

**Key Terminology**

| Term | Meaning |
|------|---------|
| JavaScript | Programming language for web interactivity |
| Console | Browser tool to run and test JavaScript |
| Statement | Single instruction |
| Script | JavaScript code file or block |
| Syntax | Rules for how code must be written |

**Three Ways to Add JavaScript**

| Method | Best For |
|--------|----------|
| Inline | Never use |
| Internal `<script>` | Small tests |
| External file | Real projects |

---

## Next Steps

**Before moving to Module 02:**

- [ ] Practiced with browser console
- [ ] Created external JavaScript file
- [ ] Made interactive page with prompts
- [ ] Understand error messages
- [ ] Get mentor verification

**Coming Next**: Module 02 - Variables & Data Types

*You will learn to store and work with data!*

---

<div align="center">

**You're now a JavaScript developer!** 

*The browser console is your new playground.*

</div>
