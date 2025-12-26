# Module 06: Tables & Forms

## Level 2.1: HTML Fundamentals

---

## 🎯 Module Objectives

By the end of this module, you will be able to:

- Create properly structured tables for data display
- Build accessible tables with headers and captions
- Create user input forms
- Use various form input types
- Understand form structure and submission

---

## Part 1: Tables

---

## Lesson 1: Basic Table Structure

### When to Use Tables

Use tables for **tabular data** — information that naturally fits in rows and columns.

| ✅ Good Use | ❌ Bad Use |
|-------------|-----------|
| Student grades | Page layout |
| Product specifications | Visual design |
| Schedules | Navigation |
| Statistics | Positioning content |

### Basic Table Elements

```html
<table>
    <tr>
        <th>Name</th>
        <th>Age</th>
        <th>Country</th>
    </tr>
    <tr>
        <td>Sokha</td>
        <td>22</td>
        <td>Cambodia</td>
    </tr>
    <tr>
        <td>Dara</td>
        <td>25</td>
        <td>Cambodia</td>
    </tr>
</table>
```

### Table Element Reference

| Element | Name | Purpose |
|---------|------|---------|
| `<table>` | Table | Container for entire table |
| `<tr>` | Table Row | A row of cells |
| `<th>` | Table Header | Header cell (bold, centered) |
| `<td>` | Table Data | Regular data cell |

### How It Looks

```
┌────────────┬────────┬────────────┐
│   Name     │  Age   │  Country   │  ← Header row (<th>)
├────────────┼────────┼────────────┤
│   Sokha    │   22   │  Cambodia  │  ← Data row (<td>)
├────────────┼────────┼────────────┤
│   Dara     │   25   │  Cambodia  │  ← Data row (<td>)
└────────────┴────────┴────────────┘
```

---

## Lesson 2: Semantic Table Sections

### Organizing Table Parts

```html
<table>
    <caption>KOOMPI Apprentice Enrollment 2024</caption>
    
    <thead>
        <tr>
            <th>Name</th>
            <th>Track</th>
            <th>Start Date</th>
        </tr>
    </thead>
    
    <tbody>
        <tr>
            <td>Sokha</td>
            <td>Web Development</td>
            <td>January 2024</td>
        </tr>
        <tr>
            <td>Dara</td>
            <td>Web Development</td>
            <td>February 2024</td>
        </tr>
    </tbody>
    
    <tfoot>
        <tr>
            <td colspan="3">Total: 2 apprentices</td>
        </tr>
    </tfoot>
</table>
```

### Table Section Elements

| Element | Purpose |
|---------|---------|
| `<caption>` | Table title/description |
| `<thead>` | Groups header rows |
| `<tbody>` | Groups body rows |
| `<tfoot>` | Groups footer rows |

---

## Lesson 3: Spanning Rows and Columns

### Column Spanning

Use `colspan` to make a cell span multiple columns:

```html
<table>
    <tr>
        <th colspan="2">Contact Information</th>
    </tr>
    <tr>
        <td>Email</td>
        <td>info@koompi.com</td>
    </tr>
    <tr>
        <td>Phone</td>
        <td>+855 12 345 678</td>
    </tr>
</table>
```

```
┌─────────────────────────────────┐
│    Contact Information          │  ← spans 2 columns
├───────────────┬─────────────────┤
│ Email         │ info@koompi.com │
├───────────────┼─────────────────┤
│ Phone         │ +855 12 345 678 │
└───────────────┴─────────────────┘
```

### Row Spanning

Use `rowspan` to make a cell span multiple rows:

```html
<table>
    <tr>
        <th rowspan="2">Housing</th>
        <td>Rent</td>
        <td>$500</td>
    </tr>
    <tr>
        <td>Utilities</td>
        <td>$100</td>
    </tr>
    <tr>
        <th rowspan="2">Transport</th>
        <td>Gas</td>
        <td>$80</td>
    </tr>
    <tr>
        <td>Insurance</td>
        <td>$50</td>
    </tr>
</table>
```

```
┌──────────────┬────────────┬────────┐
│              │ Rent       │  $500  │
│   Housing    ├────────────┼────────┤
│              │ Utilities  │  $100  │
├──────────────┼────────────┼────────┤
│              │ Gas        │   $80  │
│  Transport   ├────────────┼────────┤
│              │ Insurance  │   $50  │
└──────────────┴────────────┴────────┘
```

---

## Lesson 4: Table Accessibility

### Using Scope for Headers

```html
<table>
    <tr>
        <th scope="col">Product</th>
        <th scope="col">Price</th>
        <th scope="col">Stock</th>
    </tr>
    <tr>
        <th scope="row">KOOMPI E13</th>
        <td>$299</td>
        <td>In Stock</td>
    </tr>
    <tr>
        <th scope="row">KOOMPI E15</th>
        <td>$399</td>
        <td>Low Stock</td>
    </tr>
</table>
```

| Scope Value | Meaning |
|-------------|---------|
| `col` | Header for column below |
| `row` | Header for row to the right |
| `colgroup` | Header for group of columns |
| `rowgroup` | Header for group of rows |

---

## Part 2: Forms

---

## Lesson 5: Form Basics

### The Form Element

Forms collect user input and send it somewhere:

```html
<form action="/submit" method="POST">
    <!-- Form inputs go here -->
</form>
```

### Form Attributes

| Attribute | Purpose | Example |
|-----------|---------|---------|
| `action` | Where to send data | `/submit`, `process.php` |
| `method` | How to send data | `POST` (secure) or `GET` |

### Form Methods

| Method | When to Use | Data Visible? |
|--------|-------------|---------------|
| `GET` | Searches, filters | Yes (in URL) |
| `POST` | Logins, signups, sensitive data | No (hidden) |

---

## Lesson 6: Form Input Types

### Text Inputs

```html
<form>
    <!-- Simple text -->
    <input type="text" name="username" placeholder="Enter username">
    
    <!-- Email (validates email format) -->
    <input type="email" name="email" placeholder="your@email.com">
    
    <!-- Password (hides characters) -->
    <input type="password" name="password" placeholder="Enter password">
    
    <!-- Phone number -->
    <input type="tel" name="phone" placeholder="Phone number">
    
    <!-- Website URL -->
    <input type="url" name="website" placeholder="https://...">
</form>
```

### Number Inputs

```html
<form>
    <!-- Any number -->
    <input type="number" name="quantity" min="1" max="100">
    
    <!-- Range slider -->
    <input type="range" name="volume" min="0" max="100" value="50">
</form>
```

### Date and Time Inputs

```html
<form>
    <!-- Date picker -->
    <input type="date" name="birthday">
    
    <!-- Time picker -->
    <input type="time" name="appointment">
    
    <!-- Date and time -->
    <input type="datetime-local" name="meeting">
</form>
```

### Choice Inputs

```html
<form>
    <!-- Checkboxes (multiple selections) -->
    <input type="checkbox" name="skills" value="html"> HTML
    <input type="checkbox" name="skills" value="css"> CSS
    <input type="checkbox" name="skills" value="js"> JavaScript
    
    <!-- Radio buttons (single selection) -->
    <input type="radio" name="level" value="beginner"> Beginner
    <input type="radio" name="level" value="intermediate"> Intermediate
    <input type="radio" name="level" value="expert"> Expert
</form>
```

### Special Inputs

```html
<form>
    <!-- Color picker -->
    <input type="color" name="favorite_color" value="#ff0000">
    
    <!-- File upload -->
    <input type="file" name="resume" accept=".pdf,.doc">
    
    <!-- Hidden field -->
    <input type="hidden" name="form_id" value="contact_form">
</form>
```

---

## Lesson 7: Labels and Form Structure

### Why Labels Matter

**Labels** tell users what each input is for. They also help accessibility.

```html
<!-- Method 1: Wrap input with label -->
<label>
    Username:
    <input type="text" name="username">
</label>

<!-- Method 2: Use "for" and "id" -->
<label for="email">Email Address:</label>
<input type="email" name="email" id="email">
```

**Important**: Always use labels! Screen readers need them.

### Complete Form Example

```html
<form action="/register" method="POST">
    <h2>KOOMPI Apprenticeship Application</h2>
    
    <!-- Text fields -->
    <div>
        <label for="name">Full Name:</label>
        <input type="text" id="name" name="name" required>
    </div>
    
    <div>
        <label for="email">Email:</label>
        <input type="email" id="email" name="email" required>
    </div>
    
    <div>
        <label for="phone">Phone Number:</label>
        <input type="tel" id="phone" name="phone">
    </div>
    
    <!-- Selection -->
    <div>
        <label for="track">Preferred Track:</label>
        <select id="track" name="track">
            <option value="">Select a track</option>
            <option value="web">Web Development</option>
            <option value="english">English</option>
            <option value="business">Business</option>
        </select>
    </div>
    
    <!-- Radio buttons -->
    <fieldset>
        <legend>Experience Level:</legend>
        <label>
            <input type="radio" name="level" value="beginner" checked>
            Beginner
        </label>
        <label>
            <input type="radio" name="level" value="some">
            Some Experience
        </label>
        <label>
            <input type="radio" name="level" value="experienced">
            Experienced
        </label>
    </fieldset>
    
    <!-- Checkboxes -->
    <fieldset>
        <legend>Skills (select all that apply):</legend>
        <label>
            <input type="checkbox" name="skills" value="typing">
            Typing
        </label>
        <label>
            <input type="checkbox" name="skills" value="english">
            Basic English
        </label>
        <label>
            <input type="checkbox" name="skills" value="computer">
            Computer Basics
        </label>
    </fieldset>
    
    <!-- Textarea -->
    <div>
        <label for="about">Tell us about yourself:</label>
        <textarea id="about" name="about" rows="5" cols="40"></textarea>
    </div>
    
    <!-- Submit button -->
    <button type="submit">Submit Application</button>
</form>
```

### Form Structure Elements

| Element | Purpose |
|---------|---------|
| `<form>` | Container for all inputs |
| `<label>` | Describes an input |
| `<input>` | User's input data |
| `<select>` | Dropdown menu |
| `<option>` | Option in dropdown |
| `<textarea>` | Multi-line text input |
| `<button>` | Submit or action button |
| `<fieldset>` | Groups related inputs |
| `<legend>` | Title for fieldset |

---

## Lesson 8: Input Attributes

### Common Attributes

| Attribute | Purpose | Example |
|-----------|---------|---------|
| `required` | Must be filled | `<input required>` |
| `placeholder` | Hint text | `placeholder="Enter name"` |
| `value` | Default value | `value="default"` |
| `disabled` | Can't interact | `<input disabled>` |
| `readonly` | Can't edit | `<input readonly>` |
| `maxlength` | Max characters | `maxlength="100"` |
| `min`, `max` | Number range | `min="1" max="10"` |
| `pattern` | Regex validation | `pattern="[0-9]{3}"` |
| `autofocus` | Focus on load | `<input autofocus>` |

### Validation Example

```html
<form>
    <!-- Required field -->
    <label for="name">Name (required):</label>
    <input type="text" id="name" name="name" required>
    
    <!-- Length limits -->
    <label for="username">Username (5-20 characters):</label>
    <input type="text" id="username" name="username" 
           minlength="5" maxlength="20" required>
    
    <!-- Number range -->
    <label for="age">Age (16-100):</label>
    <input type="number" id="age" name="age" 
           min="16" max="100" required>
    
    <!-- Pattern (phone number) -->
    <label for="phone">Phone (format: 012-345-678):</label>
    <input type="tel" id="phone" name="phone" 
           pattern="[0-9]{3}-[0-9]{3}-[0-9]{3}"
           placeholder="012-345-678">
    
    <button type="submit">Submit</button>
</form>
```

---

## 🧪 Self-Check Exercises

### Exercise 1: Create a Data Table

Create a table showing:

- 5 Cambodian provinces
- Their population
- Their area (km²)

Include caption, thead, tbody, and proper header scope.

### Exercise 2: Spanning Practice

Create a schedule table with:

- Days of the week as columns
- Time slots as rows
- Some classes that span 2 hours (rowspan)
- A lunch break that spans all days (colspan)

### Exercise 3: Contact Form

Build a contact form with:

- Name (required)
- Email (required, validates email)
- Phone (optional)
- Subject dropdown (3-4 options)
- Message textarea
- Submit button

### Exercise 4: Registration Form

Create a KOOMPI Apprentice registration form:

- Personal information section
- Educational background
- Track preference (radio buttons)
- Available skills (checkboxes)
- Why do you want to join? (textarea)
- Submit button

### Exercise 5: Survey Form

Create a survey form with:

- All different input types you learned
- Proper labels for everything
- At least one fieldset with legend
- Required and optional fields
- Form validation (required, min/max, etc.)

---

## 📝 Module Summary

**Table Elements**

| Element | Purpose |
|---------|---------|
| `<table>` | Table container |
| `<caption>` | Table title |
| `<thead>`, `<tbody>`, `<tfoot>` | Table sections |
| `<tr>` | Table row |
| `<th>` | Header cell |
| `<td>` | Data cell |
| `colspan`, `rowspan` | Cell spanning |

**Form Elements**

| Element | Purpose |
|---------|---------|
| `<form>` | Form container |
| `<input>` | User input (many types) |
| `<label>` | Input description |
| `<select>`, `<option>` | Dropdown |
| `<textarea>` | Multi-line text |
| `<button>` | Action button |
| `<fieldset>`, `<legend>` | Group inputs |

---

## 🎯 Next Steps

**Before moving to Module 07:**

- [ ] Create province table
- [ ] Build schedule with spanning
- [ ] Complete contact form
- [ ] Create registration form
- [ ] Get mentor verification

**Coming Next**: Module 07 - Personal Bio Page Project

*You will combine everything to build your first complete website!*

---

<div align="center">

**Tables organize, forms connect!** 📊📝

*Now you can display data and collect user input.*

</div>
