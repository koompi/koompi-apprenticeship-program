# Module 01: Introduction to CSS

## Level 2.2: CSS Styling

---

## Module Objectives

By the end of this module, you will be able to:

- Understand what CSS is and why it's essential
- Add CSS to your HTML pages using three methods
- Write basic CSS rules
- Understand CSS syntax and terminology

---

## Lesson 1: What is CSS?

### CSS Defined

**CSS** stands for **Cascading Style Sheets**.

- **Cascading**: Styles can override each other in a specific order
- **Style**: Appearance and presentation
- **Sheets**: Separate files or sections containing styles

### The Role of CSS

- THE WEB DEVELOPMENT TRIO
- HTML CSS JavaScript
- Structure Style Behavior
- "What's on "How does "What does
- the page?" it look?" it do?"
- Headings Colors Click events
- Paragraphs Fonts Animations
- Images Spacing Data loading
- Links Layout Form validation

### Why Learn CSS?

| Without CSS | With CSS |
|-------------|----------|
| Boring, plain pages | Beautiful, engaging designs |
| Same look everywhere | Unique brand identity |
| Hard to read | Easy to read with good typography |
| Not professional | Professional appearance |
| Desktop only | Works on all devices |

---

## Lesson 2: CSS Syntax

### The Anatomy of a CSS Rule

```css
selector {
 property: value;
 property: value;
}
```

**Example:**

```css
h1 {
 color: blue;
 font-size: 24px;
}
```

### Breaking It Down

- h1 {
- color: blue;
- Value (what to set it to)
- Property (what to change)
- Selector (what to style)
- }

### CSS Terminology

| Term | Description | Example |
|------|-------------|---------|
| **Selector** | What element(s) to style | `h1`, `.class`, `#id` |
| **Property** | What aspect to change | `color`, `font-size` |
| **Value** | What to set the property to | `blue`, `24px` |
| **Declaration** | A property-value pair | `color: blue;` |
| **Rule** | Selector + declarations | The whole block |

### Multiple Declarations

```css
p {
 color: #333333;
 font-size: 16px;
 line-height: 1.6;
 margin-bottom: 20px;
}
```

Every declaration ends with a semicolon (`;`).

---

## Lesson 3: Three Ways to Add CSS

### Method 1: Inline CSS

CSS written directly in HTML elements using the `style` attribute.

```html
<h1 style="color: blue; font-size: 24px;">Hello World</h1>
<p style="color: gray;">This is a paragraph.</p>
```

| Pros | Cons |
|------|------|
| Quick for testing | Hard to maintain |
| Specific to one element | Repeats for each element |
| | Mixes structure and style |
| | Not recommended for real projects |

### Method 2: Internal CSS

CSS written in a `<style>` element in the `<head>` section.

```html
<!DOCTYPE html>
<html lang="en">
<head>
 <meta charset="UTF-8">
 <title>My Page</title>
 <style>
 h1 {
 color: blue;
 font-size: 24px;
 }
 p {
 color: gray;
 line-height: 1.6;
 }
 </style>
</head>
<body>
 <h1>Hello World</h1>
 <p>This is a paragraph.</p>
</body>
</html>
```

| Pros | Cons |
|------|------|
| All styles in one place | Only for that one page |
| Good for single-page sites | Can't reuse across pages |
| Easier than inline | Makes HTML file longer |

### Method 3: External CSS (Recommended!)

CSS in a separate `.css` file, linked to HTML.

**styles.css:**

```css
h1 {
 color: blue;
 font-size: 24px;
}

p {
 color: gray;
 line-height: 1.6;
}
```

**index.html:**

```html
<!DOCTYPE html>
<html lang="en">
<head>
 <meta charset="UTF-8">
 <title>My Page</title>
 <link rel="stylesheet" href="styles.css">
</head>
<body>
 <h1>Hello World</h1>
 <p>This is a paragraph.</p>
</body>
</html>
```

| Pros | Cons |
|------|------|
| Clean separation | Extra file to manage |
| Reuse across all pages | Need to link in each HTML |
| Easy to maintain | |
| Browser can cache it | |
| **Best practice!** | |

---

## Lesson 4: The Link Element

### Linking External CSS

```html
<link rel="stylesheet" href="css/style.css">
```

### Attributes Explained

| Attribute | Value | Purpose |
|-----------|-------|---------|
| `rel` | `stylesheet` | Relationship (this is a stylesheet) |
| `href` | `css/style.css` | Path to the CSS file |

### Common File Structures

```
project/
├── index.html
├── about.html
├── css/
│ └── style.css ← External CSS file
└── images/
```

**From index.html:**

```html
<link rel="stylesheet" href="css/style.css">
```

### Multiple Stylesheets

You can link multiple CSS files:

```html
<head>
 <link rel="stylesheet" href="css/reset.css">
 <link rel="stylesheet" href="css/style.css">
 <link rel="stylesheet" href="css/responsive.css">
</head>
```

Order matters! Later files can override earlier ones.

---

## Lesson 5: Your First Stylesheet

### Setting Up

**Step 1: Create the folder structure**

```bash
cd ~/projects/learning
mkdir css-practice
cd css-practice
mkdir css
touch index.html css/style.css
```

**Step 2: Create the HTML (index.html)**

```html
<!DOCTYPE html>
<html lang="en">
<head>
 <meta charset="UTF-8">
 <meta name="viewport" content="width=device-width, initial-scale=1.0">
 <title>My First Styled Page</title>
 <link rel="stylesheet" href="css/style.css">
</head>
<body>
 <header>
 <h1>Welcome to My Website</h1>
 <p>This is my first styled page!</p>
 </header>
 
 <main>
 <section>
 <h2>About This Page</h2>
 <p>I am learning CSS at KOOMPI. CSS makes websites beautiful!</p>
 <p>With CSS, I can change colors, fonts, spacing, and layout.</p>
 </section>
 
 <section>
 <h2>What I'm Learning</h2>
 <ul>
 <li>HTML structure</li>
 <li>CSS styling</li>
 <li>Web development</li>
 </ul>
 </section>
 </main>
 
 <footer>
 <p>&copy; 2024 My Name. Learning at KOOMPI.</p>
 </footer>
</body>
</html>
```

**Step 3: Add basic styles (css/style.css)**

```css
/* My First Stylesheet */

/* Body styles - applies to whole page */
body {
 font-family: Arial, sans-serif;
 line-height: 1.6;
 margin: 0;
 padding: 20px;
 background-color: #f4f4f4;
 color: #333;
}

/* Header styles */
header {
 background-color: #35424a;
 color: white;
 padding: 20px;
 text-align: center;
}

/* Main heading */
h1 {
 margin: 0;
}

/* Section headings */
h2 {
 color: #35424a;
 border-bottom: 2px solid #35424a;
 padding-bottom: 10px;
}

/* Paragraphs */
p {
 margin-bottom: 15px;
}

/* Lists */
ul {
 background-color: white;
 padding: 20px;
 padding-left: 40px;
}

li {
 margin-bottom: 10px;
}

/* Footer */
footer {
 background-color: #35424a;
 color: white;
 text-align: center;
 padding: 10px;
 margin-top: 20px;
}
```

**Step 4: View in browser**

```bash
firefox index.html
```

---

## Lesson 6: CSS Comments

### Writing Comments

Comments help you organize and explain your CSS:

```css
/* This is a single-line comment */

/*
 * This is a multi-line comment
 * It can span several lines
 * Use it to explain complex code
 */

/* ==========================================
 HEADER STYLES
 ========================================== */
header {
 background-color: #333;
}

/* Navigation */
nav {
 /* TODO: Add responsive styles */
}
```

### Comment Best Practices

| Do | Don't |
|-------|----------|
| Explain why, not what | Comment obvious code |
| Mark sections | Leave TODO comments in production |
| Note browser fixes | Write novels |

---

## Lesson 7: CSS Reset and Best Practices

### Why Reset?

Different browsers have different default styles. A CSS reset creates a consistent starting point.

### Simple Reset

```css
/* Simple CSS Reset */
* {
 margin: 0;
 padding: 0;
 box-sizing: border-box;
}
```

The `*` selector targets ALL elements.

### Best Practices Summary

```
┌─────────────────────────────────────────────────────────────────────────────┐
│ CSS BEST PRACTICES │
├─────────────────────────────────────────────────────────────────────────────┤
│ │
│ USE EXTERNAL CSS │
│ • Keep styles in .css files │
│ • Link from HTML <head> │
│ │
│ ORGANIZE YOUR CODE │
│ • Use comments to mark sections │
│ • Group related styles together │
│ • Keep consistent indentation │
│ │
│ USE MEANINGFUL NAMES │
│ • Name classes by purpose, not appearance │
│ • .error not .red-text │
│ • .primary-button not .big-blue-button │
│ │
│ START WITH A RESET │
│ • Normalize browser differences │
│ • Creates consistent base │
│ │
│ TEST IN BROWSER │
│ • Refresh often to see changes │
│ • Use DevTools to experiment │
│ │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## Self-Check Exercises

### Exercise 1: CSS Terminology

Match the terms:

1. `h1` is a ______
2. `color` is a ______
3. `blue` is a ______
4. `color: blue;` is a ______

Options: selector, property, value, declaration

### Exercise 2: Add Inline CSS

Add inline styles to make:

- The `<h1>` red
- The `<p>` blue with 20px font size

```html
<h1>Title</h1>
<p>Paragraph text</p>
```

### Exercise 3: Create Internal CSS

Convert your inline CSS to internal CSS in the `<head>`.

### Exercise 4: Create External CSS

1. Create a new project folder
2. Create `index.html` and `css/style.css`
3. Link the stylesheet
4. Style at least 5 different elements

### Exercise 5: Style Your Bio Page

Take your HTML Bio Page from Level 2.1 and:

1. Create a `css` folder
2. Create `style.css`
3. Link it to your HTML
4. Add basic styles for body, headings, and paragraphs

---

## Module Summary

**Key Vocabulary**

| Term | Meaning |
|------|---------|
| CSS | Cascading Style Sheets |
| Selector | What element(s) to style |
| Property | What aspect to change |
| Value | What to set the property to |
| Declaration | Property-value pair |
| Rule | Complete CSS block |

**Three Methods**

| Method | Best For |
|--------|----------|
| Inline | Quick tests only |
| Internal | Single-page sites |
| External | Real projects |

---

## Next Steps

**Before moving to Module 02:**

- [ ] Complete all exercises
- [ ] Create first external stylesheet
- [ ] Apply basic styles to bio page
- [ ] Get mentor verification

**Coming Next**: Module 02 - Selectors & Specificity

*You will learn to target exactly the elements you want!*

---

<div align="center">

**You're starting to paint the web!** 

*CSS turns structure into beauty.*

</div>
