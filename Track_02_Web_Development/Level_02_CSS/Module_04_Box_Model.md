# Module 04: The Box Model

## Level 2.2: CSS Styling

---

## Module Objectives

By the end of this module, you will be able to:

- Understand the CSS box model completely
- Control spacing with margin and padding
- Apply borders and outlines
- Use box-sizing for predictable layouts
- Control element dimensions

---

## Lesson 1: Understanding the Box Model

### Everything is a Box

In CSS, every element is a rectangular box. The box model describes how space is calculated.

```
┌─────────────────────────────────────────────────────────────────────────────┐
│ THE CSS BOX MODEL │
├─────────────────────────────────────────────────────────────────────────────┤
│ │
│ ┌─────────────────────────────────────────────────────────────────────┐ │
│ │ MARGIN │ │
│ │ ┌─────────────────────────────────────────────────────────────┐ │ │
│ │ │ BORDER │ │ │
│ │ │ ┌─────────────────────────────────────────────────────┐ │ │ │
│ │ │ │ PADDING │ │ │ │
│ │ │ │ ┌─────────────────────────────────────────────┐ │ │ │ │
│ │ │ │ │ │ │ │ │ │
│ │ │ │ │ CONTENT │ │ │ │ │
│ │ │ │ │ (text, images, etc.) │ │ │ │ │
│ │ │ │ │ │ │ │ │ │
│ │ │ │ └─────────────────────────────────────────────┘ │ │ │ │
│ │ │ │ │ │ │ │
│ │ │ └─────────────────────────────────────────────────────┘ │ │ │
│ │ │ │ │ │
│ │ └─────────────────────────────────────────────────────────────┘ │ │
│ │ │ │
│ └─────────────────────────────────────────────────────────────────────┘ │
│ │
└─────────────────────────────────────────────────────────────────────────────┘
```

### Box Model Components

| Component | Description |
|-----------|-------------|
| **Content** | The actual content (text, image) |
| **Padding** | Space INSIDE the box, around content |
| **Border** | The edge of the box |
| **Margin** | Space OUTSIDE the box, between elements |

---

## Lesson 2: Content - Width and Height

### Setting Dimensions

```css
.box {
 width: 300px;
 height: 200px;
}
```

### Width Options

```css
/* Fixed width */
width: 300px;

/* Percentage of parent */
width: 50%;

/* Maximum width (responsive) */
max-width: 800px;

/* Minimum width */
min-width: 200px;

/* Viewport width */
width: 100vw;
```

### Height Options

```css
/* Fixed height */
height: 200px;

/* Minimum height (content can grow) */
min-height: 400px;

/* Full viewport height */
height: 100vh;

/* Auto - based on content */
height: auto;
```

### Best Practice: Responsive

```css
/* Instead of fixed width */
.container {
 max-width: 1200px; /* Never wider than this */
 width: 100%; /* Fill available space */
 margin: 0 auto; /* Center it */
}
```

---

## Lesson 3: Padding

### Padding: Space Inside

Padding creates space between the content and the border.

```css
.box {
 padding: 20px; /* All four sides */
}
```

### Individual Sides

```css
.box {
 padding-top: 10px;
 padding-right: 20px;
 padding-bottom: 10px;
 padding-left: 20px;
}
```

### Shorthand Notation

```css
/* All sides */
padding: 20px;

/* Vertical | Horizontal */
padding: 10px 20px;

/* Top | Horizontal | Bottom */
padding: 10px 20px 30px;

/* Top | Right | Bottom | Left (clockwise) */
padding: 10px 20px 30px 40px;
```

**Remember**: Start at top, go clockwise (like a clock!)

### Practical Examples

```css
/* Button */
.button {
 padding: 12px 24px; /* More horizontal space */
}

/* Card */
.card {
 padding: 20px;
}

/* Header */
header {
 padding: 10px 20px;
}

/* Section */
section {
 padding: 60px 20px; /* More vertical breathing room */
}
```

---

## Lesson 4: Border

### Border Property

```css
.box {
 border: 1px solid black;
}
```

### Border Shorthand

```css
border: [width] [style] [color];

/* Examples */
border: 1px solid #333;
border: 2px dashed blue;
border: 3px dotted red;
```

### Border Styles

```css
border-style: solid; /* ────────── */
border-style: dashed; /* - - - - - */
border-style: dotted; /* .......... */
border-style: double; /* ══════════ */
border-style: groove; /* 3D groove */
border-style: ridge; /* 3D ridge */
border-style: none; /* No border */
```

### Individual Border Sides

```css
border-top: 2px solid black;
border-right: 1px dashed gray;
border-bottom: 3px solid blue;
border-left: none;
```

### Border Radius (Rounded Corners)

```css
/* All corners */
border-radius: 10px;

/* Circle (if width = height) */
border-radius: 50%;

/* Individual corners */
border-radius: 10px 20px 10px 20px; /* TL TR BR BL */

/* Different horizontal/vertical */
border-radius: 20px / 10px;
```

### Practical Border Examples

```css
/* Card */
.card {
 border: 1px solid #ddd;
 border-radius: 8px;
}

/* Button */
.button {
 border: 2px solid #3498db;
 border-radius: 4px;
}

/* Circle avatar */
.avatar {
 width: 100px;
 height: 100px;
 border-radius: 50%;
 border: 3px solid white;
}

/* Bottom border only (underline effect) */
.tab {
 border: none;
 border-bottom: 3px solid #3498db;
}
```

---

## Lesson 5: Margin

### Margin: Space Outside

Margin creates space between elements.

```css
.box {
 margin: 20px; /* All four sides */
}
```

### Individual Sides

```css
.box {
 margin-top: 10px;
 margin-right: 20px;
 margin-bottom: 10px;
 margin-left: 20px;
}
```

### Shorthand (Same as Padding)

```css
/* All sides */
margin: 20px;

/* Vertical | Horizontal */
margin: 10px 20px;

/* Top | Right | Bottom | Left */
margin: 10px 20px 30px 40px;
```

### Auto Margin (Centering)

```css
.container {
 max-width: 800px;
 margin: 0 auto; /* 0 top/bottom, auto left/right = centered */
}
```

### Margin Collapse

When vertical margins touch, they **collapse** (only the larger one applies):

```css
h1 { margin-bottom: 20px; }
p { margin-top: 15px; }

/* You might expect 35px gap, but you get 20px (the larger one) */
```

**This only happens with vertical margins, not horizontal.**

### Negative Margins

```css
/* Pull element up/left */
.overlap {
 margin-top: -20px;
}
```

---

## Lesson 6: Box Sizing

### The Problem

By default, width and height only apply to content. Padding and border add to total size!

```css
.box {
 width: 200px;
 padding: 20px;
 border: 5px solid black;
}

/* Actual width = 200 + 20 + 20 + 5 + 5 = 250px! */
```

### The Solution: box-sizing

```css
.box {
 box-sizing: border-box;
 width: 200px;
 padding: 20px;
 border: 5px solid black;
}

/* Now width IS 200px (including padding and border) */
```

### Apply Globally (Best Practice)

```css
/* Add to your CSS reset */
*, *::before, *::after {
 box-sizing: border-box;
}
```

### Visual Comparison

```
┌─────────────────────────────────────────────────────────────────────────────┐
│ BOX-SIZING COMPARISON │
├─────────────────────────────────────────────────────────────────────────────┤
│ │
│ content-box (default) border-box (recommended) │
│ ═══════════════════════ ════════════════════════ │
│ │
│ width: 200px width: 200px │
│ padding: 20px padding: 20px │
│ border: 5px border: 5px │
│ │
│ ┌──────────────────────────────┐ ┌────────────────────┐ │
│ │ 250px total │ │ 200px total │ │
│ │ ┌──────────────────────┐ │ │ ┌──────────────┐ │ │
│ │ │ 200px content │ │ │ │ content │ │ │
│ │ └──────────────────────┘ │ │ │ (smaller) │ │ │
│ └──────────────────────────────┘ │ └──────────────┘ │ │
│ └────────────────────┘ │
│ Total width = content + padding + border │
│ Total width = width (includes padding + border) │
│ │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## Lesson 7: Putting It All Together

### Complete Card Example

```css
.card {
 /* Box sizing */
 box-sizing: border-box;
 
 /* Dimensions */
 width: 300px;
 min-height: 200px;
 
 /* Padding (inside) */
 padding: 20px;
 
 /* Border */
 border: 1px solid #ddd;
 border-radius: 8px;
 
 /* Margin (outside) */
 margin: 15px;
 
 /* Colors */
 background-color: white;
}

.card-title {
 margin: 0 0 15px 0; /* Only bottom margin */
 padding-bottom: 10px;
 border-bottom: 1px solid #eee;
}

.card-content {
 margin: 0;
}
```

### Debug with DevTools

In browser DevTools, you can see the box model:

1. Right-click element → Inspect
2. Look at the box model diagram
3. See content, padding, border, margin values
4. Hover to highlight each part

---

## Self-Check Exercises

### Exercise 1: Box Model Quiz

A box has:

- width: 200px
- padding: 20px
- border: 5px solid
- margin: 10px

With default box-sizing, what's the total width including margin?

### Exercise 2: Create a Card

Create a card with:

- White background
- Light gray border
- 20px padding inside
- Rounded corners
- 15px margin between cards

### Exercise 3: Center a Container

Create a container that:

- Has max-width of 1000px
- Is centered horizontally
- Has 20px padding

### Exercise 4: Button Styling

Create a button with:

- Padding: 12px vertical, 24px horizontal
- Border: 2px solid
- Border radius: 4px
- No margin on top, 20px on bottom

### Exercise 5: Apply to Bio Page

Update your bio page with:

- Proper box-sizing reset
- Consistent padding in sections
- Margins between elements
- Cards with borders and rounded corners

---

## Module Summary

**Box Model Properties**

| Property | Description |
|----------|-------------|
| `width/height` | Content dimensions |
| `padding` | Space inside (content to border) |
| `border` | The box edge |
| `margin` | Space outside (between boxes) |
| `box-sizing` | How size is calculated |

**Shorthand Pattern (Clockwise)**

```
 TOP
 ↓
LEFT → ───── → RIGHT
 ↓
 BOTTOM
```

`padding: top right bottom left;`

---

## Next Steps

**Before moving to Module 05:**

- [ ] Understand all box model parts
- [ ] Use box-sizing: border-box
- [ ] Create cards with proper spacing
- [ ] Style bio page with good spacing
- [ ] Get mentor verification

**Coming Next**: Module 05 - Layout & Positioning

*You will learn to control where elements appear on the page!*

---

<div align="center">

**Master of spacing!** 

*Understanding the box model is key to CSS layouts.*

</div>
