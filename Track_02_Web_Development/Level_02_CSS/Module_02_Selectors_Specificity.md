# Module 02: Selectors & Specificity

## Level 2.2: CSS Styling

---

## 🎯 Module Objectives

By the end of this module, you will be able to:

- Use different types of CSS selectors
- Target elements precisely with classes and IDs
- Combine selectors for complex targeting
- Understand how specificity determines which styles win

---

## Lesson 1: Basic Selectors

### Element (Type) Selectors

Target elements by their tag name:

```css
/* All paragraphs */
p {
    color: gray;
}

/* All headings level 1 */
h1 {
    font-size: 32px;
}

/* All links */
a {
    color: blue;
}

/* All list items */
li {
    margin-bottom: 10px;
}
```

### Universal Selector

The `*` targets everything:

```css
/* Affects every element */
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}
```

### Grouping Selectors

Style multiple elements the same way with commas:

```css
/* All these get the same style */
h1, h2, h3 {
    font-family: Georgia, serif;
    color: #333;
}

/* Headers and paragraphs */
h1, h2, p {
    margin-bottom: 15px;
}
```

---

## Lesson 2: Class Selectors

### What Are Classes?

Classes let you style specific elements. Add a `class` attribute in HTML, then target it with `.classname` in CSS.

**HTML:**

```html
<p class="intro">This is an introduction paragraph.</p>
<p>This is a regular paragraph.</p>
<p class="intro">This also has the intro class.</p>
```

**CSS:**

```css
.intro {
    font-size: 1.2em;
    font-weight: bold;
    color: #2c3e50;
}
```

### Class Rules

- Start with a letter
- Can contain letters, numbers, hyphens, underscores
- Case-sensitive (`.Intro` ≠ `.intro`)
- Start with `.` in CSS

### Multiple Classes

An element can have multiple classes:

```html
<div class="card featured">Featured Product</div>
<div class="card">Regular Product</div>
<div class="card sale">Sale Product</div>
```

```css
.card {
    border: 1px solid #ddd;
    padding: 20px;
    margin: 10px;
}

.featured {
    border-color: gold;
    background-color: #fffdf0;
}

.sale {
    border-color: red;
    background-color: #fff0f0;
}
```

### Naming Classes

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                    CLASS NAMING BEST PRACTICES                               │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│   ❌ BAD (Based on appearance)          ✅ GOOD (Based on purpose)          │
│   ════════════════════════════          ══════════════════════════          │
│                                                                              │
│   .red-text                              .error-message                      │
│   .big-font                              .page-title                         │
│   .left-box                              .sidebar                            │
│   .blue-button                           .primary-button                     │
│   .margin-20                             .card                               │
│                                                                              │
│   WHY? If you change the color from red to orange, ".red-text"              │
│   becomes confusing. ".error-message" stays meaningful.                     │
│                                                                              │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## Lesson 3: ID Selectors

### What Are IDs?

IDs are unique identifiers. Each ID should only appear ONCE per page.

**HTML:**

```html
<header id="main-header">
    <h1>Site Title</h1>
</header>

<nav id="main-nav">
    <a href="#">Home</a>
</nav>
```

**CSS:**

```css
#main-header {
    background-color: #333;
    color: white;
    padding: 20px;
}

#main-nav {
    background-color: #444;
}
```

### Class vs ID

| Feature | Class | ID |
|---------|-------|-----|
| Syntax (HTML) | `class="name"` | `id="name"` |
| Syntax (CSS) | `.name` | `#name` |
| Usage | Multiple elements | One element only |
| Reusability | Highly reusable | Unique per page |
| Specificity | Lower | Higher |
| Best for | Styling | Unique elements, anchors |

### When to Use Each

```css
/* Use CLASSES for: */
.button { }          /* Multiple buttons */
.card { }            /* Multiple cards */
.nav-link { }        /* Multiple nav links */
.error { }           /* Any error message */

/* Use IDs for: */
#main-header { }     /* Only one header */
#footer { }          /* Only one footer */
#contact-form { }    /* Specific form */
#hero-section { }    /* Unique section */
```

---

## Lesson 4: Combining Selectors

### Descendant Selector (Space)

Selects elements inside other elements:

```css
/* Paragraphs inside articles */
article p {
    line-height: 1.8;
}

/* Links inside navigation */
nav a {
    text-decoration: none;
    color: white;
}

/* List items inside unordered lists inside nav */
nav ul li {
    display: inline-block;
}
```

### Child Selector (>)

Selects direct children only:

```css
/* Only direct child paragraphs of article */
article > p {
    font-size: 18px;
}
```

**Difference:**

```html
<article>
    <p>Direct child - selected</p>
    <div>
        <p>Nested paragraph - NOT selected with ></p>
    </div>
</article>
```

### Element + Class

Target elements with specific class:

```css
/* Only paragraphs with intro class */
p.intro {
    font-weight: bold;
}

/* Only links with nav-link class */
a.nav-link {
    padding: 10px;
}

/* Only divs with card class */
div.card {
    border-radius: 8px;
}
```

### Multiple Classes

Target elements with multiple classes:

```css
/* Element with BOTH classes */
.card.featured {
    border: 2px solid gold;
}

/* Different from: */
.card .featured {
    /* This selects .featured INSIDE .card */
}
```

---

## Lesson 5: Attribute Selectors

### Selecting by Attribute

```css
/* Links with target attribute */
a[target] {
    font-weight: bold;
}

/* Inputs that are required */
input[required] {
    border-color: red;
}

/* Links that open in new tab */
a[target="_blank"] {
    /* Show external link icon */
}

/* Inputs of type email */
input[type="email"] {
    background-color: #f9f9f9;
}
```

### Common Attribute Selectors

| Selector | Meaning | Example |
|----------|---------|---------|
| `[attr]` | Has attribute | `[required]` |
| `[attr="value"]` | Exact value | `[type="email"]` |
| `[attr^="value"]` | Starts with | `[href^="https"]` |
| `[attr$="value"]` | Ends with | `[href$=".pdf"]` |
| `[attr*="value"]` | Contains | `[class*="btn"]` |

### Practical Examples

```css
/* External links (start with http) */
a[href^="http"] {
    color: blue;
}

/* PDF downloads (end with .pdf) */
a[href$=".pdf"]::after {
    content: " (PDF)";
}

/* All button classes */
[class*="button"] {
    cursor: pointer;
}
```

---

## Lesson 6: Pseudo-classes

### What Are Pseudo-classes?

Pseudo-classes select elements based on their **state** or **position**.

### Interactive States

```css
/* Mouse hover */
a:hover {
    color: orange;
    text-decoration: underline;
}

/* Being clicked */
button:active {
    transform: scale(0.98);
}

/* Keyboard focus */
input:focus {
    border-color: blue;
    outline: none;
}

/* Visited links */
a:visited {
    color: purple;
}
```

### Position-based

```css
/* First child */
li:first-child {
    font-weight: bold;
}

/* Last child */
li:last-child {
    border-bottom: none;
}

/* Nth child (every 2nd item) */
tr:nth-child(2n) {
    background-color: #f2f2f2;
}

/* Nth child (every 3rd item starting from 1st) */
li:nth-child(3n+1) {
    color: red;
}
```

### Form States

```css
/* Disabled inputs */
input:disabled {
    background-color: #ccc;
    cursor: not-allowed;
}

/* Checked checkboxes */
input:checked {
    /* Styles for checked state */
}

/* Valid input */
input:valid {
    border-color: green;
}

/* Invalid input */
input:invalid {
    border-color: red;
}
```

---

## Lesson 7: Specificity

### What is Specificity?

When multiple styles target the same element, **specificity** determines which wins.

### Specificity Hierarchy

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                    SPECIFICITY HIERARCHY                                     │
│                    (from lowest to highest)                                  │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│   1. Element selectors           p, h1, div, a                    (0,0,1)  │
│                                                                              │
│   2. Class selectors             .intro, .button, .nav-link       (0,1,0)  │
│      Attribute selectors         [type="email"]                             │
│      Pseudo-classes              :hover, :first-child                       │
│                                                                              │
│   3. ID selectors                #header, #main-nav               (1,0,0)  │
│                                                                              │
│   4. Inline styles               style="color: red"              (1,0,0,0) │
│                                                                              │
│   5. !important                  color: red !important;           (wins)    │
│                                                                              │
└─────────────────────────────────────────────────────────────────────────────┘
```

### Calculating Specificity

Count selectors in each category: (ID, Class, Element)

```css
p { }                    /* (0,0,1) = 1 */
.intro { }               /* (0,1,0) = 10 */
p.intro { }              /* (0,1,1) = 11 */
#header { }              /* (1,0,0) = 100 */
#header p { }            /* (1,0,1) = 101 */
#header .intro { }       /* (1,1,0) = 110 */
#header p.intro { }      /* (1,1,1) = 111 */
```

### Example: Which Wins?

```html
<p id="intro" class="highlight">Hello World</p>
```

```css
p { color: black; }                    /* (0,0,1) */
.highlight { color: yellow; }          /* (0,1,0) - wins over p */
p.highlight { color: orange; }         /* (0,1,1) - wins over .highlight */
#intro { color: blue; }                /* (1,0,0) - WINS! Highest specificity */
```

Result: **blue** wins!

### Avoid !important

```css
/* DON'T do this */
p {
    color: red !important;  /* Overrides everything - bad practice */
}

/* Instead, use more specific selectors */
article p.intro {
    color: red;
}
```

`!important` makes debugging difficult. Use specificity properly instead.

---

## 🧪 Self-Check Exercises

### Exercise 1: Selector Types

What type of selector is each?

1. `header { }`
2. `.navigation { }`
3. `#main-content { }`
4. `nav a { }`
5. `a:hover { }`

### Exercise 2: Create Classes

Add classes to this HTML and style them:

```html
<div>Regular card</div>
<div>Featured card with special border</div>
<div>Sale card with red accent</div>
```

### Exercise 3: Specificity Battle

Which color wins for each element?

```css
p { color: black; }
.text { color: blue; }
#special { color: red; }
p.text { color: green; }
```

```html
<p class="text">Paragraph 1</p>
<p id="special" class="text">Paragraph 2</p>
```

### Exercise 4: Navigation Styling

Style a navigation using:

- Element selectors for `nav` and `ul`
- Class selectors for `.nav-link`
- Pseudo-class for hover effect

### Exercise 5: Form Styling

Style a form using:

- Attribute selectors for input types
- Pseudo-classes for focus and invalid states
- Classes for the submit button

---

## 📝 Module Summary

**Selector Types**

| Selector | Syntax | Specificity |
|----------|--------|-------------|
| Element | `p` | (0,0,1) |
| Class | `.name` | (0,1,0) |
| ID | `#name` | (1,0,0) |
| Descendant | `div p` | Sum of parts |
| Child | `div > p` | Sum of parts |
| Attribute | `[type]` | (0,1,0) |
| Pseudo-class | `:hover` | (0,1,0) |

**Key Rules**

1. IDs beat classes beat elements
2. More specific selectors win
3. Later rules win if specificity is equal
4. Avoid `!important`

---

## 🎯 Next Steps

**Before moving to Module 03:**

- [ ] Practice all selector types
- [ ] Style navigation with classes
- [ ] Add hover effects
- [ ] Understand specificity
- [ ] Get mentor verification

**Coming Next**: Module 03 - Colors, Backgrounds & Typography

*You will learn to add beautiful colors and fonts!*

---

<div align="center">

**Precision targeting unlocked!** 🎯

*Now you can style exactly what you want.*

</div>
