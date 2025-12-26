# Module 05: Layout & Positioning

## Level 2.2: CSS Styling

---

## 🎯 Module Objectives

By the end of this module, you will be able to:

- Understand the display property values
- Use positioning (static, relative, absolute, fixed)
- Create layouts with floats (legacy knowledge)
- Build navigation bars
- Create multi-column layouts

---

## Lesson 1: The Display Property

### Block vs Inline

Every element has a default display value:

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                    BLOCK vs INLINE                                           │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│   BLOCK ELEMENTS                       INLINE ELEMENTS                       │
│   ═══════════════                      ═════════════════                     │
│                                                                              │
│   ┌────────────────────────────────┐   text ┌───┐ more ┌────┐ text         │
│   │ Takes full width               │        │box│      │ box│              │
│   └────────────────────────────────┘        └───┘      └────┘              │
│   ┌────────────────────────────────┐                                        │
│   │ Stacks vertically              │   • Flows with text                   │
│   └────────────────────────────────┘   • Only as wide as content           │
│                                        • Can't set width/height             │
│   • Full width available                                                    │
│   • Stacks below previous                                                   │
│   • Can set width/height                                                    │
│                                                                              │
│   Examples:                            Examples:                            │
│   div, p, h1-h6, section              span, a, strong, em, img             │
│                                                                              │
└─────────────────────────────────────────────────────────────────────────────┘
```

### Display Values

```css
/* Block - full width, stacks vertically */
display: block;

/* Inline - flows with text */
display: inline;

/* Inline-block - inline but with width/height */
display: inline-block;

/* None - completely hidden */
display: none;

/* Flex - flexbox layout (next module) */
display: flex;

/* Grid - grid layout (advanced) */
display: grid;
```

### Inline-Block: Best of Both

```css
.button {
    display: inline-block;
    width: 200px;          /* Can set width (like block) */
    padding: 10px 20px;    
    /* Sits inline with other elements (like inline) */
}
```

**Use inline-block for:**

- Horizontal navigation
- Buttons side by side
- Image galleries

### Display: None vs Visibility

```css
/* Completely removes element */
display: none;

/* Hides but keeps space */
visibility: hidden;
```

---

## Lesson 2: Position Property

### Position Values

```css
position: static;    /* Default - normal flow */
position: relative;  /* Relative to normal position */
position: absolute;  /* Relative to positioned parent */
position: fixed;     /* Relative to viewport */
position: sticky;    /* Hybrid relative/fixed */
```

### Static (Default)

```css
.box {
    position: static;  /* Default - follows normal document flow */
}
```

Elements appear where they naturally would.

### Relative

Offset from its **normal position**:

```css
.box {
    position: relative;
    top: 20px;     /* Move down 20px */
    left: 30px;    /* Move right 30px */
}
```

- Original space is preserved
- Other elements not affected

### Absolute

Positioned relative to **nearest positioned ancestor**:

```css
.parent {
    position: relative;  /* Creates positioning context */
}

.child {
    position: absolute;
    top: 10px;
    right: 10px;
}
```

- Removed from normal flow
- Other elements ignore it
- Parent needs `position: relative`

### Fixed

Positioned relative to **viewport** (browser window):

```css
.navbar {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
}
```

- Stays in place when scrolling
- Removed from document flow

### Sticky

Hybrid of relative and fixed:

```css
.header {
    position: sticky;
    top: 0;  /* Sticks when reaching top */
}
```

- Acts relative until scroll position reached
- Then acts fixed

---

## Lesson 3: Positioning Offsets

### Offset Properties

```css
top: 20px;     /* Distance from top */
right: 20px;   /* Distance from right */
bottom: 20px;  /* Distance from bottom */
left: 20px;    /* Distance from left */
```

### Centering with Position

```css
/* Center absolutely */
.centered {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
}
```

### Z-Index (Stacking)

When elements overlap, `z-index` controls which is on top:

```css
.behind {
    position: relative;
    z-index: 1;
}

.in-front {
    position: relative;
    z-index: 2;  /* Higher = on top */
}
```

**Note**: Only works on positioned elements (not static).

---

## Lesson 4: Creating a Navigation Bar

### Horizontal Navigation

**HTML:**

```html
<nav class="main-nav">
    <ul>
        <li><a href="#">Home</a></li>
        <li><a href="#">About</a></li>
        <li><a href="#">Services</a></li>
        <li><a href="#">Contact</a></li>
    </ul>
</nav>
```

**CSS:**

```css
.main-nav ul {
    list-style: none;
    margin: 0;
    padding: 0;
    background-color: #333;
}

.main-nav li {
    display: inline-block;
}

.main-nav a {
    display: block;
    padding: 15px 20px;
    color: white;
    text-decoration: none;
}

.main-nav a:hover {
    background-color: #555;
}
```

### Fixed Navigation

```css
.main-nav {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    z-index: 1000;
}

/* Add padding to body to prevent content hiding behind nav */
body {
    padding-top: 60px;  /* Height of navbar */
}
```

### Navigation with Logo

```css
.main-nav {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 0 20px;
    background-color: #333;
}

.logo {
    color: white;
    font-size: 1.5rem;
    font-weight: bold;
}

.nav-links {
    list-style: none;
    display: flex;
    margin: 0;
    padding: 0;
}

.nav-links a {
    display: block;
    padding: 15px 20px;
    color: white;
    text-decoration: none;
}
```

---

## Lesson 5: Floats (Legacy Layout)

### Understanding Floats

Floats were used for layout before Flexbox. Know them for older code.

```css
.left-column {
    float: left;
    width: 30%;
}

.right-column {
    float: right;
    width: 70%;
}
```

### Clearing Floats

Floats can cause layout problems. Clear them:

```css
/* Clearfix - add to parent of floated elements */
.clearfix::after {
    content: "";
    display: table;
    clear: both;
}
```

### Float for Text Wrapping

Floats are still useful for wrapping text around images:

```css
.article-image {
    float: left;
    margin-right: 20px;
    margin-bottom: 10px;
}
```

**Modern recommendation**: Use Flexbox or Grid for layouts, floats for text wrapping only.

---

## Lesson 6: Two-Column Layout

### Using Float (Legacy)

```css
.container {
    max-width: 1200px;
    margin: 0 auto;
}

.sidebar {
    float: left;
    width: 25%;
    padding: 20px;
}

.main-content {
    float: right;
    width: 75%;
    padding: 20px;
}

.container::after {
    content: "";
    display: table;
    clear: both;
}
```

### Using Inline-Block

```css
.sidebar {
    display: inline-block;
    width: 24%;  /* Slightly less than 25% for spacing */
    vertical-align: top;
    padding: 20px;
}

.main-content {
    display: inline-block;
    width: 74%;
    vertical-align: top;
    padding: 20px;
}
```

### Using Flexbox (Modern - Preview)

```css
.container {
    display: flex;
}

.sidebar {
    width: 25%;
    padding: 20px;
}

.main-content {
    flex: 1;  /* Takes remaining space */
    padding: 20px;
}
```

---

## Lesson 7: Practical Layout Examples

### Card Grid

```css
.cards-container {
    max-width: 1200px;
    margin: 0 auto;
}

.card {
    display: inline-block;
    width: calc(33.333% - 20px);  /* 3 columns with gap */
    margin: 10px;
    vertical-align: top;
    box-sizing: border-box;
    padding: 20px;
    border: 1px solid #ddd;
    border-radius: 8px;
}
```

### Sticky Footer

```css
html, body {
    height: 100%;
}

.wrapper {
    min-height: 100%;
    display: flex;
    flex-direction: column;
}

main {
    flex: 1;  /* Grows to fill space */
}

footer {
    background-color: #333;
    color: white;
    padding: 20px;
}
```

### Overlay

```css
.modal-overlay {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.5);
    z-index: 1000;
}

.modal-content {
    position: fixed;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    background-color: white;
    padding: 30px;
    border-radius: 8px;
    z-index: 1001;
}
```

---

## 🧪 Self-Check Exercises

### Exercise 1: Display Types

Change these elements' display:

- Make links display as blocks
- Make divs display inline
- Make spans display as inline-block with width

### Exercise 2: Fixed Header

Create a fixed navigation bar that:

- Stays at top when scrolling
- Has proper z-index
- Content doesn't hide behind it

### Exercise 3: Absolute Positioning

Create a card with:

- A "Sale" badge in the top-right corner (absolute)
- Card is the positioning parent (relative)

### Exercise 4: Two-Column Layout

Create a blog layout with:

- Sidebar (25% width) on the left
- Main content (75% width) on the right
- Both using inline-block or flexbox

### Exercise 5: Complete Navigation

Build navigation with:

- Logo on the left
- Links on the right
- Fixed position
- Hover effects

---

## 📝 Module Summary

**Display Values**

| Value | Behavior |
|-------|----------|
| `block` | Full width, stacks vertically |
| `inline` | Flows with text, no width/height |
| `inline-block` | Inline but with dimensions |
| `none` | Hidden completely |
| `flex` | Flexbox container |

**Position Values**

| Value | Relative To |
|-------|-------------|
| `static` | Normal flow (default) |
| `relative` | Normal position |
| `absolute` | Positioned parent |
| `fixed` | Viewport |
| `sticky` | Scroll position |

---

## 🎯 Next Steps

**Before moving to Module 06:**

- [ ] Master display property
- [ ] Understand all position values
- [ ] Create fixed navigation
- [ ] Build two-column layout
- [ ] Get mentor verification

**Coming Next**: Module 06 - Flexbox & Responsive Design

*You will learn modern, flexible layouts!*

---

<div align="center">

**Layout master!** 📐

*Now you control where everything goes.*

</div>
