# Module 06: DOM Manipulation

## Level 2.3: JavaScript Basics

---

## Module Objectives

By the end of this module, you will be able to:

- Select HTML elements with JavaScript
- Change content, styles, and attributes
- Handle user events (clicks, input)
- Create dynamic web page interactions

---

## Lesson 1: What is the DOM?

### Document Object Model

The DOM is how JavaScript sees HTML:

```
┌─────────────────────────────────────────────────────────────────────────────┐
│ THE DOM TREE │
├─────────────────────────────────────────────────────────────────────────────┤
│ │
│ document │
│ │ │
│ <html> │
│ ╱ ╲ │
│ <head> <body> │
│ │ │ │
│ <title> ┌─┴─────┬─────────┐ │
│ │ │ │ │
│ <header> <main> <footer> │
│ │ │ │ │
│ <h1> <div> <p> │
│ │ │
│ <button> │
│ │
│ Every element becomes a "node" JavaScript can work with. │
│ │
└─────────────────────────────────────────────────────────────────────────────┘
```

### Accessing the DOM

The `document` object is your entry point:

```javascript
console.log(document); // The whole page
console.log(document.title); // Page title
console.log(document.body); // Body element
console.log(document.URL); // Page URL
```

---

## Lesson 2: Selecting Elements

### getElementById

Select one element by its ID:

```html
<h1 id="title">Welcome</h1>
```

```javascript
const title = document.getElementById("title");
console.log(title); // <h1 id="title">Welcome</h1>
```

### querySelector

Select the first matching element (like CSS):

```javascript
// By ID
const title = document.querySelector("#title");

// By class
const card = document.querySelector(".card");

// By tag
const firstParagraph = document.querySelector("p");

// Complex selector
const navLink = document.querySelector("nav a.active");
```

### querySelectorAll

Select ALL matching elements:

```javascript
// Get all paragraphs
const paragraphs = document.querySelectorAll("p");
console.log(paragraphs); // NodeList [p, p, p, ...]

// Loop through them
paragraphs.forEach(p => {
 console.log(p.textContent);
});
```

### Selection Methods Summary

| Method | Returns | Example |
|--------|---------|---------|
| `getElementById()` | Single element | `("myId")` |
| `querySelector()` | First match | `(".class")` |
| `querySelectorAll()` | All matches | `("p")` |
| `getElementsByClassName()` | HTMLCollection | `("class")` |
| `getElementsByTagName()` | HTMLCollection | `("div")` |

**Tip**: Use `querySelector` and `querySelectorAll` for flexibility.

---

## Lesson 3: Changing Content

### textContent

Change text inside an element:

```html
<p id="message">Hello</p>
```

```javascript
const message = document.querySelector("#message");
message.textContent = "Welcome, Sokha!";
// Now: <p id="message">Welcome, Sokha!</p>
```

### innerHTML

Change HTML inside an element:

```javascript
const container = document.querySelector("#container");
container.innerHTML = "<h2>New Heading</h2><p>New paragraph</p>";
```

**Warning**: Be careful with innerHTML and user input (security risk).

### textContent vs innerHTML

| Property | For | Example |
|----------|-----|---------|
| `textContent` | Plain text | `"Hello World"` |
| `innerHTML` | HTML markup | `"<b>Hello</b> World"` |

```javascript
element.textContent = "<b>bold</b>"; // Shows: <b>bold</b>
element.innerHTML = "<b>bold</b>"; // Shows: **bold**
```

---

## Lesson 4: Changing Styles

### Inline Styles

```javascript
const box = document.querySelector("#box");

box.style.backgroundColor = "blue";
box.style.color = "white";
box.style.padding = "20px";
box.style.borderRadius = "8px";
```

**Note**: Use camelCase for CSS properties (background-color → backgroundColor).

### Adding/Removing Classes

Better approach — use CSS classes:

```css
/* styles.css */
.highlight {
 background-color: yellow;
 font-weight: bold;
}

.hidden {
 display: none;
}
```

```javascript
const element = document.querySelector("#myElement");

// Add class
element.classList.add("highlight");

// Remove class
element.classList.remove("highlight");

// Toggle class (add if missing, remove if present)
element.classList.toggle("hidden");

// Check if has class
if (element.classList.contains("highlight")) {
 console.log("It's highlighted!");
}
```

---

## Lesson 5: Event Handling

### What Are Events?

Events are user actions: clicks, typing, scrolling, etc.

### addEventListener

```javascript
const button = document.querySelector("#myButton");

button.addEventListener("click", function() {
 console.log("Button was clicked!");
});

// With arrow function
button.addEventListener("click", () => {
 console.log("Clicked!");
});
```

### Common Events

| Event | Triggers When |
|-------|---------------|
| `click` | Element is clicked |
| `dblclick` | Double-clicked |
| `mouseover` | Mouse enters element |
| `mouseout` | Mouse leaves element |
| `keydown` | Key is pressed |
| `keyup` | Key is released |
| `input` | Input value changes |
| `change` | Input value changes (on blur) |
| `submit` | Form is submitted |
| `load` | Page/image loads |

### Event Object

Every event handler receives an event object:

```javascript
button.addEventListener("click", function(event) {
 console.log(event.type); // "click"
 console.log(event.target); // The clicked element
 console.log(event.clientX); // Mouse X position
});

// Often shortened to 'e'
button.addEventListener("click", (e) => {
 e.target.style.backgroundColor = "red";
});
```

---

## Lesson 6: Interactive Examples

### Toggle Dark Mode

```html
<button id="themeToggle">Toggle Dark Mode</button>
```

```javascript
const toggle = document.querySelector("#themeToggle");

toggle.addEventListener("click", () => {
 document.body.classList.toggle("dark-mode");
});
```

```css
.dark-mode {
 background-color: #1a1a1a;
 color: white;
}
```

### Counter

```html
<p>Count: <span id="count">0</span></p>
<button id="increment">+</button>
<button id="decrement">-</button>
```

```javascript
let count = 0;
const countDisplay = document.querySelector("#count");
const incrementBtn = document.querySelector("#increment");
const decrementBtn = document.querySelector("#decrement");

incrementBtn.addEventListener("click", () => {
 count++;
 countDisplay.textContent = count;
});

decrementBtn.addEventListener("click", () => {
 count--;
 countDisplay.textContent = count;
});
```

### Form Input

```html
<input type="text" id="nameInput" placeholder="Enter your name">
<p>Hello, <span id="greeting">Guest</span>!</p>
```

```javascript
const input = document.querySelector("#nameInput");
const greeting = document.querySelector("#greeting");

input.addEventListener("input", (e) => {
 greeting.textContent = e.target.value || "Guest";
});
```

---

## Lesson 7: Creating & Removing Elements

### Create New Elements

```javascript
// Create element
const newDiv = document.createElement("div");
newDiv.textContent = "I am new!";
newDiv.classList.add("card");

// Add to page
document.body.appendChild(newDiv);

// Or add to specific parent
const container = document.querySelector("#container");
container.appendChild(newDiv);
```

### Insert in Specific Position

```javascript
const list = document.querySelector("#myList");
const newItem = document.createElement("li");
newItem.textContent = "New Item";

// At the end
list.appendChild(newItem);

// At the beginning
list.prepend(newItem);

// Before another element
const secondItem = list.children[1];
list.insertBefore(newItem, secondItem);
```

### Remove Elements

```javascript
const element = document.querySelector("#toRemove");
element.remove();

// Or using parent
const parent = document.querySelector("#container");
const child = document.querySelector("#child");
parent.removeChild(child);
```

### Dynamic Todo Example

```javascript
const addBtn = document.querySelector("#addTask");
const taskInput = document.querySelector("#taskInput");
const taskList = document.querySelector("#taskList");

addBtn.addEventListener("click", () => {
 const taskText = taskInput.value.trim();
 
 if (taskText) {
 const li = document.createElement("li");
 li.textContent = taskText;
 
 // Add delete button
 const deleteBtn = document.createElement("button");
 deleteBtn.textContent = "Delete";
 deleteBtn.addEventListener("click", () => li.remove());
 
 li.appendChild(deleteBtn);
 taskList.appendChild(li);
 taskInput.value = "";
 }
});
```

---

## Self-Check Exercises

### Exercise 1: Select and Change

1. Create an HTML file with a heading and paragraph
2. Use JavaScript to:
 - Change the heading text
 - Change the paragraph color
 - Add a class to the paragraph

### Exercise 2: Click Counter

Create a button that:

- Displays how many times it's been clicked
- Changes color after 10 clicks

### Exercise 3: Name Greeter

Create:

- An input field for name
- A paragraph that updates to "Hello, [name]!" as you type

### Exercise 4: Toggle Visibility

Create:

- A paragraph of text
- A button that shows/hides the text when clicked

### Exercise 5: Dynamic List

Create:

- An input field
- An "Add" button
- A list that shows added items
- Each item has a "Delete" button

---

## Module Summary

**Selecting Elements**

| Method | Returns |
|--------|---------|
| `querySelector()` | First match |
| `querySelectorAll()` | All matches |
| `getElementById()` | Element by ID |

**Changing Elements**

| Property/Method | Changes |
|-----------------|---------|
| `textContent` | Text only |
| `innerHTML` | HTML content |
| `style.property` | Inline CSS |
| `classList.add()` | Add CSS class |
| `classList.remove()` | Remove class |
| `classList.toggle()` | Toggle class |

**Events**

| Event | When |
|-------|------|
| `click` | Element clicked |
| `input` | Input changes |
| `submit` | Form submitted |
| `keydown` | Key pressed |

---

## Next Steps

**Before moving to Module 07:**

- [ ] Select elements with JavaScript
- [ ] Change content and styles
- [ ] Handle click events
- [ ] Create dynamic elements
- [ ] Get mentor verification

**Coming Next**: Module 07 - Project: Interactive Quiz

*You will build your complete JavaScript project!*

---

<div align="center">

**JavaScript controls the page!** 

*Now your websites can respond to users.*

</div>
