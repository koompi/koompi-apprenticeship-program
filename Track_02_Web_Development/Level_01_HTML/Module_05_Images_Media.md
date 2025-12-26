# Module 05: Images & Media

## Level 2.1: HTML Fundamentals

---

## 🎯 Module Objectives

By the end of this module, you will be able to:

- Embed images using the `<img>` element
- Write proper alternative text for accessibility
- Understand image file formats and when to use each
- Work with relative and absolute image paths
- Use images as links
- Add captions with `<figure>` and `<figcaption>`

---

## Lesson 1: The Image Element

### Basic Image Syntax

The `<img>` element displays images. It's a **void element** (no closing tag).

```html
<img src="photo.jpg" alt="Description of the image">
```

### Required Attributes

| Attribute | Purpose | Required? |
|-----------|---------|-----------|
| `src` | Image file location | ✅ Yes |
| `alt` | Alternative text (accessibility) | ✅ Yes |

### Anatomy of an Image Element

```html
<img src="images/koompi-laptop.jpg" 
     alt="KOOMPI laptop computer on a wooden desk" 
     width="800" 
     height="600">
```

| Attribute | Value | Purpose |
|-----------|-------|---------|
| `src` | `images/koompi-laptop.jpg` | Where to find the image |
| `alt` | Description | What screen readers say |
| `width` | `800` | Width in pixels |
| `height` | `600` | Height in pixels |

---

## Lesson 2: Image Paths

### Folder Structure Example

```
my-website/
├── index.html
├── about.html
├── images/
│   ├── logo.png
│   ├── hero-banner.jpg
│   ├── team/
│   │   ├── sokha.jpg
│   │   └── dara.jpg
│   └── products/
│       ├── laptop-1.jpg
│       └── laptop-2.jpg
└── pages/
    └── contact.html
```

### Relative Paths from index.html

```html
<!-- Image in images folder -->
<img src="images/logo.png" alt="Logo">

<!-- Image in images/team subfolder -->
<img src="images/team/sokha.jpg" alt="Sokha">

<!-- Image in images/products subfolder -->
<img src="images/products/laptop-1.jpg" alt="Laptop">
```

### Relative Paths from pages/contact.html

```html
<!-- Go up one folder, then into images -->
<img src="../images/logo.png" alt="Logo">
<img src="../images/team/sokha.jpg" alt="Sokha">
```

### Absolute Paths (External Images)

```html
<!-- From other websites -->
<img src="https://example.com/images/photo.jpg" alt="External photo">
```

**Note**: Avoid using images from other websites without permission.

### Path Reference

| From | To | Path |
|------|-----|------|
| `index.html` | `images/logo.png` | `images/logo.png` |
| `index.html` | `images/team/sokha.jpg` | `images/team/sokha.jpg` |
| `pages/contact.html` | `images/logo.png` | `../images/logo.png` |
| `pages/contact.html` | `images/team/sokha.jpg` | `../images/team/sokha.jpg` |

---

## Lesson 3: Alternative Text (Alt Text)

### Why Alt Text Matters

Alt text is crucial for:

- **Accessibility**: Screen readers read it to blind users
- **Broken images**: Shows when image won't load
- **SEO**: Search engines use it to understand images

### Writing Good Alt Text

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                    ALT TEXT BEST PRACTICES                                   │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│   ❌ BAD                              ✅ GOOD                                │
│   ═════                               ══════                                │
│                                                                              │
│   alt="image"                         alt="KOOMPI laptop computer"          │
│   alt="photo123.jpg"                  alt="Students learning to code"       │
│   alt=""  (for meaningful images)     alt="Angkor Wat temple at sunrise"    │
│   alt="Click here"                    alt="Download button icon"            │
│                                                                              │
│   TIPS:                                                                      │
│   • Be specific and descriptive                                             │
│   • Don't start with "Image of..." or "Photo of..."                        │
│   • Keep it concise (under 125 characters)                                 │
│   • Describe what's important in context                                   │
│                                                                              │
└─────────────────────────────────────────────────────────────────────────────┘
```

### When to Use Empty Alt Text

Use `alt=""` for decorative images that don't add content:

```html
<!-- Decorative: adds no information -->
<img src="decorative-border.png" alt="">

<!-- Meaningful: needs description -->
<img src="team-photo.jpg" alt="The KOOMPI team at our office in Phnom Penh">
```

### Examples of Good Alt Text

| Image Type | Alt Text |
|------------|----------|
| Logo | `alt="KOOMPI"` or `alt="KOOMPI logo"` |
| Product photo | `alt="KOOMPI E13 laptop, silver, open showing screen"` |
| Team photo | `alt="Four KOOMPI team members smiling in office"` |
| Chart | `alt="Bar chart showing 50% increase in users from 2023 to 2024"` |
| Icon button | `alt="Search"` or `alt="Submit form"` |

---

## Lesson 4: Image Dimensions

### Setting Width and Height

```html
<!-- Using attributes -->
<img src="photo.jpg" alt="Photo" width="800" height="600">

<!-- Values are in pixels (don't include "px") -->
```

### Why Set Dimensions?

Setting dimensions prevents **layout shift** — the page jumping around while images load.

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                    WITHOUT DIMENSIONS                                        │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│   1. Page loads text:       2. Image loads:        3. Content jumps!        │
│                                                                              │
│   ┌───────────────┐        ┌───────────────┐      ┌───────────────┐         │
│   │ Title         │        │ Title         │      │ Title         │         │
│   │ Text here... │        │ ┌───────────┐ │      │ ┌───────────┐ │         │
│   │               │   →    │ │  IMAGE    │ │  →   │ │  IMAGE    │ │        │
│   │               │        │ └───────────┘ │      │ └───────────┘ │         │
│   │               │        │               │      │ Text here... │         │
│   └───────────────┘        └───────────────┘      └───────────────┘         │
│                                                                              │
│   WITH DIMENSIONS: Space is reserved, no jumping!                           │
│                                                                              │
└─────────────────────────────────────────────────────────────────────────────┘
```

### Responsive Images (Preview)

For now, you can make images responsive with simple CSS:

```html
<img src="photo.jpg" alt="Photo" style="max-width: 100%; height: auto;">
```

This makes images shrink on small screens but never grow larger than their natural size.

---

## Lesson 5: Image File Formats

### Common Web Image Formats

| Format | Best For | Features |
|--------|----------|----------|
| **JPEG/JPG** | Photographs | Small file size, no transparency |
| **PNG** | Graphics, logos, screenshots | Transparency support, larger files |
| **SVG** | Icons, logos, illustrations | Vector (scales perfectly), tiny file |
| **WebP** | Modern websites | Best compression, transparency |
| **GIF** | Simple animations | Animation support, limited colors |

### Visual Guide

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                    CHOOSING IMAGE FORMAT                                     │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│   Is it a photograph?                                                        │
│   └── YES → Use JPEG                                                         │
│   └── NO  → Does it need transparency?                                      │
│             └── YES → Use PNG (or WebP)                                     │
│             └── NO  → Is it an icon/logo?                                   │
│                       └── YES → Use SVG                                     │
│                       └── NO  → Is it animated?                             │
│                                 └── YES → Use GIF (or WebP)                │
│                                 └── NO  → Use PNG or WebP                  │
│                                                                              │
│   MODERN TIP: WebP works for almost everything and has the best            │
│   compression. Use it when browser support isn't a concern.                │
│                                                                              │
└─────────────────────────────────────────────────────────────────────────────┘
```

### Format Examples

```html
<!-- Photograph: JPEG -->
<img src="team-photo.jpg" alt="Team photo">

<!-- Logo with transparency: PNG -->
<img src="logo.png" alt="Company logo">

<!-- Scalable icon: SVG -->
<img src="icons/menu.svg" alt="Menu">

<!-- Modern format: WebP -->
<img src="banner.webp" alt="Banner image">
```

---

## Lesson 6: Images as Links

### Wrapping Images with Links

Make images clickable by wrapping them in an anchor tag:

```html
<a href="https://koompi.com">
    <img src="koompi-logo.png" alt="KOOMPI - Visit our website">
</a>
```

### Image Links with Text

```html
<a href="products.html">
    <img src="laptop.jpg" alt="">
    <span>View Our Products</span>
</a>
```

**Note**: When an image is a link, the alt text should describe the link destination, not just the image.

### Common Use Cases

```html
<!-- Logo links to homepage -->
<a href="index.html">
    <img src="logo.png" alt="KOOMPI Home">
</a>

<!-- Product thumbnail links to product page -->
<a href="products/koompi-e13.html">
    <img src="images/koompi-e13-thumb.jpg" alt="View KOOMPI E13 details">
</a>

<!-- Social media icon -->
<a href="https://facebook.com/koompi" target="_blank" rel="noopener noreferrer">
    <img src="icons/facebook.svg" alt="KOOMPI on Facebook">
</a>
```

---

## Lesson 7: Figure and Figcaption

### Semantic Image Containers

The `<figure>` element wraps images (or other content) with a caption.

```html
<figure>
    <img src="angkor-wat.jpg" alt="Angkor Wat temple complex at sunrise">
    <figcaption>Angkor Wat, a UNESCO World Heritage Site in Cambodia</figcaption>
</figure>
```

### When to Use Figure

Use `<figure>` when:

- The image has a caption
- The content is referenced in text ("see Figure 1")
- You're displaying diagrams, charts, or illustrations

### Multiple Images in One Figure

```html
<figure>
    <img src="before.jpg" alt="Website before redesign">
    <img src="after.jpg" alt="Website after redesign">
    <figcaption>Website design: before and after the modernization</figcaption>
</figure>
```

### Figure for Code Examples

`<figure>` isn't just for images:

```html
<figure>
    <pre><code>&lt;img src="photo.jpg" alt="Description"&gt;</code></pre>
    <figcaption>HTML code for adding an image</figcaption>
</figure>
```

---

## 🧪 Self-Check Exercises

### Exercise 1: Image Gallery

Create a page with:

- At least 4 images
- Each with proper `alt` text
- Images organized in an `images/` folder
- Different image formats (at least 2 types)

### Exercise 2: Fix the Alt Text

Improve these alt texts:

```html
<img src="laptop.jpg" alt="image">
<img src="team.jpg" alt="photo123.jpg">
<img src="logo.png" alt="logo">
<img src="graph.png" alt="chart">
```

### Exercise 3: Image Paths Challenge

Given this structure:

```
project/
├── index.html
├── pages/
│   └── about.html
└── assets/
    └── images/
        ├── logo.png
        └── hero.jpg
```

Write the correct paths from both files to both images.

### Exercise 4: Image Links

Create a page with:

- Logo at top that links to homepage
- 3 product images that link to (fake) product pages
- Social media icons that link to external sites

### Exercise 5: Figure Gallery

Create a photo gallery of Cambodia using `<figure>`:

- At least 3 photos
- Each with a `<figcaption>` describing the location
- Organized semantically

---

## 📝 Module Summary

**Elements Learned**

| Element | Purpose |
|---------|---------|
| `<img>` | Displays an image |
| `<figure>` | Container for images with captions |
| `<figcaption>` | Caption for figure content |

**Key Attributes**

| Attribute | Purpose | Required? |
|-----------|---------|-----------|
| `src` | Image location | Yes |
| `alt` | Alternative text | Yes |
| `width` | Image width (pixels) | Recommended |
| `height` | Image height (pixels) | Recommended |

**Formats Summary**

| Format | Use For |
|--------|---------|
| JPEG | Photos |
| PNG | Graphics with transparency |
| SVG | Icons, logos (vectors) |
| WebP | Everything (modern) |

---

## 🎯 Next Steps

**Before moving to Module 06:**

- [ ] Create image gallery page
- [ ] Fix alt text exercise
- [ ] Complete path challenge
- [ ] Build figure gallery
- [ ] Get mentor verification

**Coming Next**: Module 06 - Tables & Forms

*You will learn to create data tables and user input forms!*

---

<div align="center">

**A picture is worth a thousand words!** 🖼️

*But only if everyone can "see" it (with good alt text).*

</div>
