# Module 03: Colors, Backgrounds & Typography

## Level 2.2: CSS Styling

---

## 🎯 Module Objectives

By the end of this module, you will be able to:

- Use different color formats (names, hex, RGB, HSL)
- Apply background colors and images
- Style text with fonts, sizes, and spacing
- Create visually appealing and readable designs

---

## Lesson 1: Color Values

### Color Formats in CSS

```css
/* All of these create the same blue color */

/* Named colors (limited options) */
color: blue;

/* Hexadecimal (most common) */
color: #0000ff;

/* RGB (Red, Green, Blue) */
color: rgb(0, 0, 255);

/* RGBA (with transparency) */
color: rgba(0, 0, 255, 0.5);

/* HSL (Hue, Saturation, Lightness) */
color: hsl(240, 100%, 50%);

/* HSLA (with transparency) */
color: hsla(240, 100%, 50%, 0.5);
```

### Hexadecimal Colors

```
#RRGGBB  or  #RGB (shorthand)

#ff0000 = red    (#f00)
#00ff00 = green  (#0f0)
#0000ff = blue   (#00f)
#ffffff = white  (#fff)
#000000 = black  (#000)
#808080 = gray
```

Common hex colors to memorize:

| Color | Hex | Shorthand |
|-------|-----|-----------|
| Black | `#000000` | `#000` |
| White | `#ffffff` | `#fff` |
| Red | `#ff0000` | `#f00` |
| Green | `#00ff00` | `#0f0` |
| Blue | `#0000ff` | `#00f` |
| Gray | `#808080` | — |

### RGB Colors

```css
/* rgb(red, green, blue) - values 0-255 */
color: rgb(255, 0, 0);      /* Red */
color: rgb(0, 255, 0);      /* Green */
color: rgb(0, 0, 255);      /* Blue */
color: rgb(128, 128, 128);  /* Gray */

/* With transparency (0-1) */
color: rgba(255, 0, 0, 0.5);  /* 50% transparent red */
```

### HSL Colors

HSL is often more intuitive:

```css
/* hsl(hue, saturation, lightness) */
color: hsl(0, 100%, 50%);    /* Red */
color: hsl(120, 100%, 50%);  /* Green */
color: hsl(240, 100%, 50%);  /* Blue */

/* Adjusting lightness */
color: hsl(0, 100%, 25%);    /* Dark red */
color: hsl(0, 100%, 50%);    /* Normal red */
color: hsl(0, 100%, 75%);    /* Light red */
```

---

## Lesson 2: Applying Colors

### Text Color

```css
h1 {
    color: #2c3e50;
}

p {
    color: #666666;
}

a {
    color: #3498db;
}

a:hover {
    color: #2980b9;
}
```

### Background Color

```css
body {
    background-color: #f5f5f5;
}

header {
    background-color: #2c3e50;
    color: white;
}

.highlight {
    background-color: #ffff00;
}

.card {
    background-color: white;
}
```

### Color Schemes

```css
/* Professional color scheme example */
:root {
    --primary: #3498db;      /* Main brand color */
    --secondary: #2ecc71;    /* Accent color */
    --dark: #2c3e50;         /* Dark backgrounds, headings */
    --light: #ecf0f1;        /* Light backgrounds */
    --text: #333333;         /* Body text */
    --text-light: #7f8c8d;   /* Muted text */
}

body {
    background-color: var(--light);
    color: var(--text);
}

h1 {
    color: var(--dark);
}

a {
    color: var(--primary);
}

button {
    background-color: var(--primary);
    color: white;
}
```

---

## Lesson 3: Background Properties

### Background Image

```css
.hero {
    background-image: url('images/hero-bg.jpg');
}
```

### Background Size

```css
.hero {
    background-image: url('images/hero-bg.jpg');
    background-size: cover;  /* Covers entire element */
}

/* Options */
background-size: cover;      /* Scale to cover, may crop */
background-size: contain;    /* Scale to fit, may leave space */
background-size: 100% 100%;  /* Stretch to fill */
background-size: 300px 200px; /* Specific size */
```

### Background Position

```css
.hero {
    background-image: url('images/hero-bg.jpg');
    background-size: cover;
    background-position: center;  /* Center the image */
}

/* Options */
background-position: center;
background-position: top left;
background-position: bottom right;
background-position: 50% 50%;
background-position: 20px 40px;
```

### Background Repeat

```css
/* Default: repeats */
background-repeat: repeat;

/* No repeat */
background-repeat: no-repeat;

/* Repeat horizontally only */
background-repeat: repeat-x;

/* Repeat vertically only */
background-repeat: repeat-y;
```

### Complete Background Example

```css
.hero {
    background-image: url('images/hero-bg.jpg');
    background-size: cover;
    background-position: center;
    background-repeat: no-repeat;
    background-attachment: fixed;  /* Parallax effect */
    height: 100vh;
}

/* Shorthand */
.hero {
    background: url('images/hero-bg.jpg') center/cover no-repeat fixed;
    height: 100vh;
}
```

### Gradient Backgrounds

```css
/* Linear gradient */
.gradient {
    background: linear-gradient(to right, #3498db, #2ecc71);
}

/* Angled gradient */
.gradient {
    background: linear-gradient(45deg, #3498db, #2ecc71);
}

/* Multiple colors */
.gradient {
    background: linear-gradient(to bottom, #3498db, #9b59b6, #e74c3c);
}

/* Radial gradient */
.gradient {
    background: radial-gradient(circle, #3498db, #2c3e50);
}
```

---

## Lesson 4: Typography - Font Properties

### Font Family

```css
body {
    font-family: Arial, Helvetica, sans-serif;
}

h1 {
    font-family: Georgia, 'Times New Roman', serif;
}

code {
    font-family: 'Courier New', Consolas, monospace;
}
```

**Font Stack**: List fonts in order of preference. The browser uses the first available one.

### Web-Safe Fonts

Fonts available on most computers:

| Serif | Sans-Serif | Monospace |
|-------|------------|-----------|
| Georgia | Arial | Courier New |
| Times New Roman | Helvetica | Consolas |
| Palatino | Verdana | Monaco |

### Google Fonts

Free fonts from Google:

**Step 1: Choose fonts at [fonts.google.com](https://fonts.google.com)**

**Step 2: Add link in HTML `<head>`**

```html
<link href="https://fonts.googleapis.com/css2?family=Open+Sans:wght@400;700&family=Roboto&display=swap" rel="stylesheet">
```

**Step 3: Use in CSS**

```css
body {
    font-family: 'Open Sans', sans-serif;
}

h1 {
    font-family: 'Roboto', sans-serif;
}
```

### Font Size

```css
/* Pixels - fixed size */
p { font-size: 16px; }

/* Em - relative to parent */
p { font-size: 1.2em; }

/* Rem - relative to root (html) */
p { font-size: 1rem; }

/* Percentage */
p { font-size: 100%; }
```

| Unit | Best For |
|------|----------|
| `px` | Precise sizes |
| `rem` | Scalable layouts ✅ |
| `em` | Component-relative sizing |
| `%` | Relative to parent |

### Font Weight

```css
/* Keywords */
font-weight: normal;    /* 400 */
font-weight: bold;      /* 700 */

/* Numbers (100-900) */
font-weight: 100;  /* Thin */
font-weight: 300;  /* Light */
font-weight: 400;  /* Normal */
font-weight: 500;  /* Medium */
font-weight: 700;  /* Bold */
font-weight: 900;  /* Black */
```

### Font Style

```css
font-style: normal;
font-style: italic;
font-style: oblique;
```

---

## Lesson 5: Text Properties

### Text Alignment

```css
text-align: left;      /* Default for LTR */
text-align: right;
text-align: center;
text-align: justify;   /* Stretches to fill width */
```

### Text Decoration

```css
/* Underline, line-through, etc. */
text-decoration: none;           /* Remove underline from links */
text-decoration: underline;
text-decoration: line-through;   /* Strikethrough */
text-decoration: overline;
```

### Text Transform

```css
text-transform: none;
text-transform: uppercase;   /* ALL CAPS */
text-transform: lowercase;   /* all lowercase */
text-transform: capitalize;  /* First Letter Of Each Word */
```

### Line Height

```css
/* Controls space between lines */
line-height: 1.6;      /* Recommended for body text */
line-height: 1.2;      /* Tighter for headings */
line-height: 24px;     /* Exact pixels */
```

### Letter Spacing

```css
/* Space between letters */
letter-spacing: 1px;
letter-spacing: 0.1em;
letter-spacing: -0.5px;  /* Tighter */
```

### Word Spacing

```css
word-spacing: 5px;
```

---

## Lesson 6: Complete Typography Example

```css
/* Base typography */
body {
    font-family: 'Open Sans', Arial, sans-serif;
    font-size: 16px;
    line-height: 1.6;
    color: #333;
}

/* Headings */
h1, h2, h3, h4, h5, h6 {
    font-family: 'Roboto', Helvetica, sans-serif;
    font-weight: 700;
    line-height: 1.2;
    color: #2c3e50;
    margin-bottom: 0.5em;
}

h1 { font-size: 2.5rem; }
h2 { font-size: 2rem; }
h3 { font-size: 1.75rem; }
h4 { font-size: 1.5rem; }

/* Paragraphs */
p {
    margin-bottom: 1rem;
}

/* Links */
a {
    color: #3498db;
    text-decoration: none;
}

a:hover {
    text-decoration: underline;
}

/* Intro paragraph */
.intro {
    font-size: 1.25rem;
    font-weight: 300;
    color: #555;
}

/* All caps heading */
.section-title {
    text-transform: uppercase;
    letter-spacing: 2px;
    font-size: 0.875rem;
    color: #666;
}
```

---

## Lesson 7: Color & Typography Best Practices

### Readability Rules

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                    READABILITY BEST PRACTICES                                │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│   CONTRAST                                                                   │
│   • Dark text on light background (or vice versa)                           │
│   • Avoid low-contrast combinations                                         │
│   • Test readability!                                                        │
│                                                                              │
│   FONT SIZE                                                                  │
│   • Body text: minimum 16px                                                 │
│   • Never go below 12px                                                     │
│                                                                              │
│   LINE HEIGHT                                                                │
│   • Body text: 1.5 - 1.7                                                   │
│   • Headings: 1.1 - 1.3                                                    │
│                                                                              │
│   LINE LENGTH                                                                │
│   • Ideal: 50-75 characters per line                                       │
│   • Too wide = hard to read                                                 │
│                                                                              │
│   FONT CHOICES                                                               │
│   • Maximum 2-3 fonts per site                                             │
│   • One for headings, one for body                                          │
│                                                                              │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## 🧪 Self-Check Exercises

### Exercise 1: Color Formats

Write these colors in hex, RGB, and named format:

- Red
- White
- A dark gray

### Exercise 2: Color Scheme

Create a color scheme with:

- Primary color
- Secondary color
- Dark color for text
- Light color for backgrounds

### Exercise 3: Hero Section

Create a hero section with:

- Background image
- Cover sizing
- Centered content
- Text overlay (hint: use semi-transparent background)

### Exercise 4: Typography System

Create a complete typography system:

- Body font (Google Fonts)
- Heading font
- Sizes for h1 through p
- Line heights
- Color scheme

### Exercise 5: Style Your Bio Page

Apply to your bio page:

- Custom color scheme
- Google Fonts
- Background colors for sections
- Readable typography

---

## 📝 Module Summary

**Color Formats**

| Format | Example | Best For |
|--------|---------|----------|
| Named | `blue` | Quick prototyping |
| Hex | `#3498db` | Most common |
| RGB | `rgb(52, 152, 219)` | Transparency needs |
| HSL | `hsl(204, 70%, 53%)` | Easy variations |

**Typography Properties**

| Property | Controls |
|----------|----------|
| `font-family` | Which font |
| `font-size` | How big |
| `font-weight` | How bold |
| `line-height` | Space between lines |
| `text-align` | Horizontal alignment |
| `text-decoration` | Underlines, etc. |
| `text-transform` | Uppercase, etc. |

---

## 🎯 Next Steps

**Before moving to Module 04:**

- [ ] Master color formats
- [ ] Implement Google Fonts
- [ ] Create typography system
- [ ] Style bio page with colors and fonts
- [ ] Get mentor verification

**Coming Next**: Module 04 - The Box Model

*You will learn how spacing works in CSS!*

---

<div align="center">

**Your designs are coming to life!** 🎨

*Colors and fonts transform plain pages into beautiful ones.*

</div>
