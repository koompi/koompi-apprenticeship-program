# Module 06: Flexbox & Responsive Design

## Level 2.2: CSS Styling

---

## 🎯 Module Objectives

By the end of this module, you will be able to:

- Create layouts with Flexbox
- Align and distribute items easily
- Make responsive designs with media queries
- Build mobile-first layouts
- Add smooth CSS transitions

---

## Lesson 1: Introduction to Flexbox

### What is Flexbox?

Flexbox is a modern CSS layout system that makes it easy to:

- Align items horizontally or vertically
- Distribute space between items
- Create responsive layouts
- Reorder elements

### Enabling Flexbox

```css
.container {
    display: flex;
}
```

All direct children become **flex items**.

### Flex Container vs Flex Items

```html
<div class="container">     <!-- Flex Container -->
    <div class="item">1</div>    <!-- Flex Item -->
    <div class="item">2</div>    <!-- Flex Item -->
    <div class="item">3</div>    <!-- Flex Item -->
</div>
```

```css
.container {
    display: flex;  /* Makes this a flex container */
}

.item {
    /* These are automatically flex items */
}
```

---

## Lesson 2: Main Flexbox Properties

### Flex Direction

```css
.container {
    display: flex;
    flex-direction: row;          /* Default - horizontal */
    flex-direction: row-reverse;  /* Horizontal, reversed */
    flex-direction: column;        /* Vertical */
    flex-direction: column-reverse;
}
```

```
row:           [1] [2] [3]
row-reverse:   [3] [2] [1]

column:        [1]
               [2]
               [3]
```

### Justify Content (Main Axis)

Distributes items along the main axis:

```css
.container {
    display: flex;
    justify-content: flex-start;    /* Default - start */
    justify-content: flex-end;      /* End */
    justify-content: center;        /* Center */
    justify-content: space-between; /* Space between items */
    justify-content: space-around;  /* Space around items */
    justify-content: space-evenly;  /* Equal space everywhere */
}
```

```
flex-start:     [1][2][3]............
flex-end:       ............[1][2][3]
center:         .....[1][2][3].....
space-between:  [1].....[2].....[3]
space-around:   ..[1]....[2]....[3]..
space-evenly:   ...[1]...[2]...[3]...
```

### Align Items (Cross Axis)

Aligns items perpendicular to main axis:

```css
.container {
    display: flex;
    align-items: stretch;     /* Default - stretch to fill */
    align-items: flex-start;  /* Top */
    align-items: flex-end;    /* Bottom */
    align-items: center;      /* Center vertically */
    align-items: baseline;    /* Align text baselines */
}
```

---

## Lesson 3: Flex Item Properties

### Flex Grow

How much item should grow to fill space:

```css
.item {
    flex-grow: 0;  /* Default - don't grow */
    flex-grow: 1;  /* Grow to fill available space */
}
```

### Flex Shrink

How much item should shrink when space is limited:

```css
.item {
    flex-shrink: 1;  /* Default - can shrink */
    flex-shrink: 0;  /* Don't shrink */
}
```

### Flex Basis

Initial size before growing/shrinking:

```css
.item {
    flex-basis: auto;   /* Use width/height */
    flex-basis: 200px;  /* Start at 200px */
    flex-basis: 50%;    /* Start at 50% */
}
```

### Flex Shorthand

```css
.item {
    flex: 1;           /* flex: 1 1 0% */
    flex: 0 0 200px;   /* Don't grow, don't shrink, 200px base */
}
```

---

## Lesson 4: Flexbox Examples

### Centered Content

```css
.container {
    display: flex;
    justify-content: center;
    align-items: center;
    min-height: 100vh;
}
```

### Navigation Bar

```css
.navbar {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 15px 20px;
    background-color: #333;
}

.nav-links {
    display: flex;
    list-style: none;
    gap: 20px;
}
```

### Card Grid

```css
.card-container {
    display: flex;
    flex-wrap: wrap;
    gap: 20px;
}

.card {
    flex: 1 1 300px;  /* Grow, shrink, min 300px */
    max-width: 400px;
}
```

### Footer with Columns

```css
.footer {
    display: flex;
    justify-content: space-between;
    gap: 40px;
}

.footer-column {
    flex: 1;
}
```

---

## Lesson 5: Responsive Design Principles

### What is Responsive Design?

Responsive design makes websites work on all screen sizes.

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                    RESPONSIVE DESIGN                                         │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│   Desktop              Tablet                 Mobile                         │
│   ═══════              ══════                 ══════                         │
│                                                                              │
│   ┌──────────────┐    ┌──────────┐           ┌─────┐                        │
│   │ [Nav]        │    │ [Nav]    │           │[≡]  │                        │
│   │ ┌────┬─────┐ │    │ ┌──────┐ │           │     │                        │
│   │ │Side│Main │ │    │ │ Main │ │           │Main │                        │
│   │ │bar │     │ │    │ │      │ │           │     │                        │
│   │ │    │     │ │    │ └──────┘ │           │     │                        │
│   │ └────┴─────┘ │    │ [Side]   │           │     │                        │
│   │ [Footer]     │    │ [Footer] │           │Side │                        │
│   └──────────────┘    └──────────┘           │Foot │                        │
│                                               └─────┘                        │
│                                                                              │
│   Same website, different layouts based on screen size                      │
│                                                                              │
└─────────────────────────────────────────────────────────────────────────────┘
```

### Mobile-First Approach

Start with mobile styles, then add styles for larger screens:

```css
/* Mobile styles first (default) */
.container {
    padding: 10px;
}

/* Tablet and up */
@media (min-width: 768px) {
    .container {
        padding: 20px;
    }
}

/* Desktop and up */
@media (min-width: 1024px) {
    .container {
        padding: 40px;
    }
}
```

---

## Lesson 6: Media Queries

### Basic Syntax

```css
@media (condition) {
    /* Styles apply when condition is true */
}
```

### Common Breakpoints

```css
/* Mobile (default) */
/* No media query needed */

/* Tablet */
@media (min-width: 768px) { }

/* Desktop */
@media (min-width: 1024px) { }

/* Large desktop */
@media (min-width: 1200px) { }
```

### Responsive Example

```css
/* Mobile: single column */
.cards {
    display: flex;
    flex-direction: column;
    gap: 20px;
}

/* Tablet: 2 columns */
@media (min-width: 768px) {
    .cards {
        flex-direction: row;
        flex-wrap: wrap;
    }
    
    .card {
        flex: 0 0 calc(50% - 10px);
    }
}

/* Desktop: 3 columns */
@media (min-width: 1024px) {
    .card {
        flex: 0 0 calc(33.333% - 14px);
    }
}
```

### Hide/Show Elements

```css
/* Hide on mobile */
.desktop-only {
    display: none;
}

@media (min-width: 768px) {
    .desktop-only {
        display: block;
    }
}

/* Hide on desktop */
.mobile-only {
    display: block;
}

@media (min-width: 768px) {
    .mobile-only {
        display: none;
    }
}
```

---

## Lesson 7: CSS Transitions

### Basic Transitions

Make property changes smooth:

```css
.button {
    background-color: #3498db;
    transition: background-color 0.3s;
}

.button:hover {
    background-color: #2980b9;
}
```

### Transition Properties

```css
transition: property duration timing-function delay;

/* Examples */
transition: all 0.3s ease;
transition: background-color 0.3s ease-in-out;
transition: transform 0.2s ease, opacity 0.3s;
```

### Multiple Transitions

```css
.card {
    background-color: white;
    transform: translateY(0);
    box-shadow: 0 2px 4px rgba(0,0,0,0.1);
    transition: transform 0.3s, box-shadow 0.3s;
}

.card:hover {
    transform: translateY(-5px);
    box-shadow: 0 10px 20px rgba(0,0,0,0.15);
}
```

### Transform Examples

```css
/* Grow on hover */
.grow:hover {
    transform: scale(1.1);
}

/* Move up */
.lift:hover {
    transform: translateY(-10px);
}

/* Rotate */
.spin:hover {
    transform: rotate(180deg);
}
```

---

## 🧪 Self-Check Exercises

### Exercise 1: Flexbox Navigation

Create a navigation bar with:

- Logo on left
- Links on right
- Vertically centered

### Exercise 2: Card Layout

Create a responsive card grid:

- 1 column on mobile
- 2 columns on tablet
- 3 columns on desktop
- Use `flex-wrap`

### Exercise 3: Center Everything

Create a full-screen centered box:

- Use flexbox centering
- 100vh height

### Exercise 4: Responsive Portfolio

Make your bio page responsive:

- Single column on mobile
- Side-by-side on desktop
- Adjust font sizes

### Exercise 5: Smooth Interactions

Add transitions to:

- Buttons (background color)
- Cards (shadow and lift)
- Links (color change)

---

## 📝 Module Summary

**Flexbox Properties**

| Property | On | Controls |
|----------|-----|----------|
| `flex-direction` | Container | Direction of items |
| `justify-content` | Container | Main axis alignment |
| `align-items` | Container | Cross axis alignment |
| `flex-wrap` | Container | Wrapping behavior |
| `flex` | Item | Grow/shrink/basis |

**Common Breakpoints**

| Device | Breakpoint |
|--------|------------|
| Mobile | < 768px |
| Tablet | ≥ 768px |
| Desktop | ≥ 1024px |
| Large | ≥ 1200px |

---

## 🎯 Next Steps

**Before moving to Module 07:**

- [ ] Master flexbox alignment
- [ ] Create responsive layouts
- [ ] Use media queries properly
- [ ] Add smooth transitions
- [ ] Get mentor verification

**Coming Next**: Module 07 - Project: Styled Portfolio

*You will create your complete styled website!*

---

<div align="center">

**Modern layouts unlocked!** 🚀

*Flexbox + Media Queries = Responsive mastery*

</div>
