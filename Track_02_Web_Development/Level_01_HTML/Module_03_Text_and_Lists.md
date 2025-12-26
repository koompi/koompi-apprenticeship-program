# Module 03: Text Content & Lists

## Level 2.1: HTML Fundamentals

---

## Module Objectives

By the end of this module, you will be able to:

- Use heading tags to create content hierarchy
- Format paragraphs and text properly
- Add emphasis with bold and italic text
- Create ordered, unordered, and description lists

---

## Lesson 1: Headings - Creating Content Hierarchy

### The Six Heading Levels

HTML provides six levels of headings, from `<h1>` (most important) to `<h6>` (least important).

```html
<h1>This is Heading 1 - The Main Title</h1>
<h2>This is Heading 2 - Major Section</h2>
<h3>This is Heading 3 - Subsection</h3>
<h4>This is Heading 4 - Sub-subsection</h4>
<h5>This is Heading 5 - Minor heading</h5>
<h6>This is Heading 6 - Smallest heading</h6>
```

### Heading Hierarchy

- HEADING HIERARCHY
- <h1> Learn Web Development at KOOMPI MAIN TITLE
- (only ONE per page)
- <h2> Track 02: Web Development MAJOR SECTION
- <h3> Level 1: HTML Fundamentals SUBSECTION
- <h4> Module 1: Getting Started SUB-SUBSECTION
- <h4> Module 2: Document Structure
- <h3> Level 2: CSS Styling
- <h2> Track 03: Business Skills

### Important Rules for Headings

| Rule | Why |
|------|-----|
| Only ONE `<h1>` per page | The page should have one main topic |
| Don't skip levels | Go h1 → h2 → h3, not h1 → h3 |
| Use for structure, not size | Don't use h3 just because it looks smaller |
| Make them descriptive | "Our Services" not "Section 2" |

### Example: Article Structure

```html
<article>
 <h1>The Complete Guide to Learning HTML</h1>
 
 <h2>Introduction</h2>
 <p>HTML is the foundation of web development...</p>
 
 <h2>Getting Started</h2>
 
 <h3>What You Need</h3>
 <p>A text editor and a browser...</p>
 
 <h3>Your First Page</h3>
 <p>Create a file called index.html...</p>
 
 <h2>Basic Elements</h2>
 
 <h3>Text Elements</h3>
 <h4>Headings</h4>
 <p>There are six levels of headings...</p>
 
 <h4>Paragraphs</h4>
 <p>Use the p tag for paragraphs...</p>
 
 <h2>Conclusion</h2>
 <p>You now know the basics of HTML...</p>
</article>
```

---

## Lesson 2: Paragraphs and Text Blocks

### The `<p>` Element

The `<p>` element defines a paragraph of text.

```html
<p>This is a paragraph. Browsers automatically add space before and after paragraphs.</p>

<p>This is another paragraph. Notice there's space between them.</p>
```

### Line Breaks

To break a line without starting a new paragraph, use `<br>`:

```html
<p>
 KOOMPI Company<br>
 Phnom Penh, Cambodia<br>
 info@koompi.com
</p>
```

**Note**: `<br>` is a void element (no closing tag).

### Horizontal Rule

The `<hr>` element creates a horizontal line, useful for separating sections:

```html
<h2>Section One</h2>
<p>Content of section one...</p>

<hr>

<h2>Section Two</h2>
<p>Content of section two...</p>
```

### Preformatted Text

The `<pre>` element preserves spaces and line breaks exactly as written:

```html
<pre>
 Name: Sokha
 Age: 22
 Country: Cambodia
</pre>
```

This displays with the exact spacing, unlike normal HTML which collapses multiple spaces.

---

## Lesson 3: Text Formatting and Emphasis

### Semantic vs Presentational Elements

| Semantic (Use These) | Presentational (Avoid) | Visual Effect |
|---------------------|------------------------|---------------|
| `<strong>` | `<b>` | **Bold** |
| `<em>` | `<i>` | *Italic* |

**Why semantic?** Screen readers say "emphasized" for `<em>` but just "italic" for `<i>`.

### Strong (Bold/Important)

Use `<strong>` for text with strong importance:

```html
<p><strong>Warning:</strong> Do not delete system files!</p>

<p>The deadline is <strong>December 31, 2024</strong>.</p>
```

### Emphasis (Italic)

Use `<em>` for text with emphasis:

```html
<p>You <em>must</em> complete all exercises.</p>

<p>The word <em>semantic</em> means meaningful.</p>
```

### Combining Formatting

You can nest formatting elements:

```html
<p>This is <strong><em>very important</em></strong>.</p>
```

### Other Text Elements

| Element | Purpose | Example |
|---------|---------|---------|
| `<mark>` | Highlighted text | `<mark>highlighted</mark>` |
| `<small>` | Smaller text (fine print) | `<small>Terms apply</small>` |
| `<del>` | Deleted text (strikethrough) | `<del>old price</del>` |
| `<ins>` | Inserted text (underline) | `<ins>new text</ins>` |
| `<sub>` | Subscript | `H<sub>2</sub>O` |
| `<sup>` | Superscript | `x<sup>2</sup>` |
| `<code>` | Code snippet | `<code>console.log()</code>` |

### Example: Formatted Article

```html
<article>
 <h1>HTML Text Formatting</h1>
 
 <p>HTML provides many ways to format text. The most common are 
 <strong>bold</strong> and <em>italic</em>.</p>
 
 <p><strong>Important:</strong> Use semantic elements like 
 <code>&lt;strong&gt;</code> instead of <code>&lt;b&gt;</code>.</p>
 
 <p>Water is written as H<sub>2</sub>O in chemistry.</p>
 
 <p>The area formula is πr<sup>2</sup>.</p>
 
 <p><small>© 2024 KOOMPI. All rights reserved.</small></p>
</article>
```

---

## Lesson 4: Unordered Lists

### What is an Unordered List?

An **unordered list** displays items with bullet points. Order doesn't matter.

```html
<ul>
 <li>Rice</li>
 <li>Fish</li>
 <li>Vegetables</li>
</ul>
```

Displays as:

- Rice
- Fish
- Vegetables

### When to Use Unordered Lists

| Good Use Cases | Bad Use Cases |
|----------------|---------------|
| Shopping list | Step-by-step instructions |
| Feature list | Numbered procedures |
| Navigation menu | Rankings |

### Example: Skills List

```html
<h2>My Skills</h2>
<ul>
 <li>HTML</li>
 <li>CSS</li>
 <li>Linux Terminal</li>
 <li>Basic English</li>
</ul>
```

---

## Lesson 5: Ordered Lists

### What is an Ordered List?

An **ordered list** displays items with numbers. Order matters.

```html
<ol>
 <li>Turn on computer</li>
 <li>Open text editor</li>
 <li>Create new file</li>
 <li>Write HTML code</li>
 <li>Save and preview</li>
</ol>
```

Displays as:

1. Turn on computer
2. Open text editor
3. Create new file
4. Write HTML code
5. Save and preview

### Ordered List Attributes

| Attribute | Purpose | Example |
|-----------|---------|---------|
| `type` | Number style | `type="A"`, `type="a"`, `type="I"`, `type="i"` |
| `start` | Starting number | `start="5"` |
| `reversed` | Count backwards | `<ol reversed>` |

### Examples with Attributes

```html
<!-- Letters instead of numbers -->
<ol type="A">
 <li>First item</li> <!-- Displays as A. -->
 <li>Second item</li> <!-- Displays as B. -->
</ol>

<!-- Start from different number -->
<ol start="5">
 <li>Fifth item</li> <!-- Displays as 5. -->
 <li>Sixth item</li> <!-- Displays as 6. -->
</ol>

<!-- Roman numerals -->
<ol type="I">
 <li>Chapter One</li> <!-- Displays as I. -->
 <li>Chapter Two</li> <!-- Displays as II. -->
</ol>
```

---

## Lesson 6: Nested Lists

### Lists Inside Lists

You can put lists inside other lists:

```html
<h2>Web Development Curriculum</h2>
<ol>
 <li>HTML Fundamentals
 <ul>
 <li>Document Structure</li>
 <li>Text Content</li>
 <li>Links and Images</li>
 </ul>
 </li>
 <li>CSS Styling
 <ul>
 <li>Selectors</li>
 <li>Box Model</li>
 <li>Layout</li>
 </ul>
 </li>
 <li>JavaScript
 <ul>
 <li>Variables</li>
 <li>Functions</li>
 <li>DOM</li>
 </ul>
 </li>
</ol>
```

### Proper Nesting

**Important**: The nested list goes INSIDE the `<li>` element:

```html
<!-- CORRECT -->
<ul>
 <li>Item
 <ul>
 <li>Nested item</li>
 </ul>
 </li>
</ul>

<!-- WRONG -->
<ul>
 <li>Item</li>
 <ul>
 <li>Nested item</li>
 </ul>
</ul>
```

---

## Lesson 7: Description Lists

### What is a Description List?

A **description list** pairs terms with their definitions.

```html
<dl>
 <dt>HTML</dt>
 <dd>HyperText Markup Language - the structure of web pages</dd>
 
 <dt>CSS</dt>
 <dd>Cascading Style Sheets - the styling of web pages</dd>
 
 <dt>JavaScript</dt>
 <dd>A programming language - adds interactivity to web pages</dd>
</dl>
```

### Description List Elements

| Element | Meaning | Purpose |
|---------|---------|---------|
| `<dl>` | Description List | Container for all items |
| `<dt>` | Description Term | The word/term being defined |
| `<dd>` | Description Details | The explanation/definition |

### Multiple Definitions

A term can have multiple definitions:

```html
<dl>
 <dt>JavaScript</dt>
 <dd>A programming language for web development</dd>
 <dd>Can run in browsers and on servers (Node.js)</dd>
 <dd>Originally created in 1995</dd>
</dl>
```

### Use Cases for Description Lists

| Good Use | Example |
|----------|---------|
| Glossary | Technical terms and definitions |
| FAQ | Question and answer pairs |
| Metadata | Key-value pairs like "Author: Sokha" |

---

## Self-Check Exercises

### Exercise 1: Heading Practice

Create a page about Cambodia with proper heading structure:

```
h1: Cambodia - Kingdom of Wonder
 h2: Geography
 h3: Location
 h3: Climate
 h2: Culture
 h3: Language
 h3: Food
 h3: Festivals
 h2: Tourism
 h3: Angkor Wat
 h3: Phnom Penh
```

### Exercise 2: Format This Text

Take this plain text and add HTML formatting:

```
Important Notice

The application deadline is January 15 2025. 
All documents must be submitted before midnight.

Required items:
- Resume
- Portfolio
- Cover letter

Note: Late submissions will not be accepted.
```

Use: `<h1>`, `<p>`, `<strong>`, `<em>`, `<ul>`, `<li>`, `<small>`

### Exercise 3: Create a Recipe

Write an HTML page for a Cambodian recipe with:

- Recipe name as `<h1>`
- Description paragraph
- Unordered list of ingredients
- Ordered list of cooking steps

### Exercise 4: Nested Lists

Create the KOOMPI Apprenticeship structure as a nested list:

- Track 00: Digital Foundations (with its modules)
- Track 01: English (with its modules)
- Track 02: Web Development (with its levels and modules)

### Exercise 5: Glossary Page

Create a glossary page using description lists with these terms:

- Client
- Server
- HTML
- CSS
- JavaScript
- Browser

---

## Module Summary

**Elements Learned**

| Category | Elements |
|----------|----------|
| Headings | `<h1>` through `<h6>` |
| Text Blocks | `<p>`, `<br>`, `<hr>`, `<pre>` |
| Emphasis | `<strong>`, `<em>` |
| Other Text | `<mark>`, `<small>`, `<code>`, `<sub>`, `<sup>` |
| Lists | `<ul>`, `<ol>`, `<li>`, `<dl>`, `<dt>`, `<dd>` |

**Key Rules**

1. Only one `<h1>` per page
2. Don't skip heading levels
3. Use semantic elements (`<strong>` not `<b>`)
4. Nested lists go inside `<li>` elements

---

## Next Steps

**Before moving to Module 04:**

- [ ] Complete all exercises
- [ ] Create Cambodia page with headings
- [ ] Write the recipe page
- [ ] Build the glossary
- [ ] Get mentor verification

**Coming Next**: Module 04 - Links & Navigation

*You will learn to connect pages with hyperlinks!*

---

<div align="center">

**Content is king!** 

*Well-structured content is easier to read and find.*

</div>
