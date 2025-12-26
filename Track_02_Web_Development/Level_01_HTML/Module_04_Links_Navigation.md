# Module 04: Links & Navigation

## Level 2.1: HTML Fundamentals

---

## Module Objectives

By the end of this module, you will be able to:

- Create hyperlinks using the anchor tag
- Understand absolute vs relative URLs
- Link to external websites, other pages, and page sections
- Create navigation menus
- Use special link types (email, phone)

---

## Lesson 1: Introduction to Hyperlinks

### What is a Hyperlink?

A **hyperlink** (or just "link") is text or an image that you can click to go to another location. Links are what connect the "web" together.

```html
<a href="https://koompi.com">Visit KOOMPI</a>
```

### The Anchor Element

The `<a>` (anchor) element creates links:

```
<a href="URL">Link Text</a>
│ │ │
│ │ └── What users see and click
│ └── Where the link goes (destination)
└── Anchor tag
```

### Anatomy of a Link

```html
<a href="https://www.google.com" target="_blank" title="Search Engine">Google</a>
 │ │ │ │
 │ │ │ └── Visible text
 │ │ └── Tooltip on hover
 │ └── Open in new tab
 └── Destination URL
```

---

## Lesson 2: Types of URLs

### Absolute URLs

**Absolute URLs** include the full address. Use for external websites.

```html
<a href="https://www.google.com">Google</a>
<a href="https://koompi.com">KOOMPI</a>
<a href="https://github.com">GitHub</a>
```

**Structure of absolute URL:**

```
https://www.example.com/folder/page.html
│ │ │
│ │ └── Path to file
│ └── Domain name
└── Protocol (https = secure)
```

### Relative URLs

**Relative URLs** are paths from your current location. Use for your own website.

```
my-website/
├── index.html ← You are here
├── about.html
├── contact.html
└── pages/
 ├── services.html
 └── team.html
```

**From index.html:**

```html
<!-- Same folder -->
<a href="about.html">About Us</a>
<a href="contact.html">Contact</a>

<!-- Subfolder -->
<a href="pages/services.html">Services</a>
<a href="pages/team.html">Our Team</a>
```

**From pages/services.html:**

```html
<!-- Go up one folder, then to file -->
<a href="../index.html">Home</a>
<a href="../about.html">About</a>

<!-- Same folder -->
<a href="team.html">Our Team</a>
```

### Path Reference

| Path | Meaning |
|------|---------|
| `page.html` | File in same folder |
| `folder/page.html` | File in subfolder |
| `../page.html` | File in parent folder |
| `../../page.html` | File two folders up |
| `/page.html` | File from website root |

---

## Lesson 3: Link Attributes

### Essential Attributes

#### `href` (Hypertext Reference)

The destination URL. **Required** for a link to work.

```html
<a href="about.html">About</a>
```

#### `target` (Where to Open)

| Value | Behavior |
|-------|----------|
| `_self` | Same tab (default) |
| `_blank` | New tab/window |

```html
<!-- Opens in same tab -->
<a href="about.html">About</a>

<!-- Opens in new tab -->
<a href="https://google.com" target="_blank">Google</a>
```

**Best Practice**: Use `target="_blank"` for external links.

#### `title` (Tooltip)

Shows text when hovering over the link:

```html
<a href="about.html" title="Learn more about KOOMPI">About Us</a>
```

### Security for External Links

When using `target="_blank"`, add security attributes:

```html
<a href="https://external-site.com" 
 target="_blank" 
 rel="noopener noreferrer">
 External Link
</a>
```

| Attribute | Purpose |
|-----------|---------|
| `noopener` | Prevents security vulnerabilities |
| `noreferrer` | Doesn't send referrer information |

---

## Lesson 4: Internal Page Navigation

### Linking to Page Sections

You can link to specific parts of the same page using **IDs**.

**Step 1**: Add an ID to the target element

```html
<h2 id="about">About Us</h2>
<h2 id="services">Our Services</h2>
<h2 id="contact">Contact Us</h2>
```

**Step 2**: Link to the ID using `#`

```html
<a href="#about">Go to About</a>
<a href="#services">Go to Services</a>
<a href="#contact">Go to Contact</a>
```

### Complete Example: Table of Contents

```html
<!DOCTYPE html>
<html lang="en">
<head>
 <meta charset="UTF-8">
 <title>My Article</title>
</head>
<body>
 <h1>Complete Guide to HTML</h1>
 
 <!-- Table of Contents -->
 <nav>
 <h2>Contents</h2>
 <ul>
 <li><a href="#introduction">Introduction</a></li>
 <li><a href="#basics">HTML Basics</a></li>
 <li><a href="#elements">Common Elements</a></li>
 <li><a href="#conclusion">Conclusion</a></li>
 </ul>
 </nav>
 
 <!-- Sections -->
 <section id="introduction">
 <h2>Introduction</h2>
 <p>HTML is the foundation of web pages...</p>
 </section>
 
 <section id="basics">
 <h2>HTML Basics</h2>
 <p>Every HTML page has a structure...</p>
 </section>
 
 <section id="elements">
 <h2>Common Elements</h2>
 <p>The most common elements are...</p>
 </section>
 
 <section id="conclusion">
 <h2>Conclusion</h2>
 <p>Now you understand HTML basics...</p>
 </section>
 
 <!-- Back to top link -->
 <a href="#top">Back to Top</a>
</body>
</html>
```

### Linking to Sections on Other Pages

```html
<!-- Link to specific section on another page -->
<a href="about.html#team">Meet Our Team</a>
<a href="services.html#pricing">See Pricing</a>
```

---

## Lesson 5: Special Link Types

### Email Links

Opens the user's email program with a new message:

```html
<a href="mailto:info@koompi.com">Email Us</a>

<!-- With subject line -->
<a href="mailto:info@koompi.com?subject=Hello">Email with Subject</a>

<!-- With subject and body -->
<a href="mailto:info@koompi.com?subject=Question&body=Hi, I have a question...">
 Contact Support
</a>
```

### Phone Links

Opens phone dialer on mobile devices:

```html
<a href="tel:+85512345678">Call Us: +855 12 345 678</a>
```

### Download Links

The `download` attribute prompts file download:

```html
<a href="files/resume.pdf" download>Download My Resume</a>

<!-- Suggest filename -->
<a href="files/doc.pdf" download="koompi-brochure.pdf">Download Brochure</a>
```

### Summary of Special Links

| Type | URL Format | Example |
|------|------------|---------|
| Email | `mailto:email@domain` | `mailto:info@koompi.com` |
| Phone | `tel:+number` | `tel:+85512345678` |
| SMS | `sms:+number` | `sms:+85512345678` |
| Download | `href + download` | `<a href="file.pdf" download>` |

---

## Lesson 6: Building Navigation Menus

### Basic Navigation

Use the `<nav>` element for navigation:

```html
<nav>
 <a href="index.html">Home</a>
 <a href="about.html">About</a>
 <a href="services.html">Services</a>
 <a href="contact.html">Contact</a>
</nav>
```

### Navigation with List

More common and accessible approach:

```html
<nav>
 <ul>
 <li><a href="index.html">Home</a></li>
 <li><a href="about.html">About</a></li>
 <li><a href="services.html">Services</a></li>
 <li><a href="contact.html">Contact</a></li>
 </ul>
</nav>
```

### Complete Header Example

```html
<header>
 <div class="logo">
 <a href="index.html">KOOMPI</a>
 </div>
 
 <nav>
 <ul>
 <li><a href="index.html">Home</a></li>
 <li><a href="about.html">About Us</a></li>
 <li><a href="products.html">Products</a></li>
 <li><a href="blog.html">Blog</a></li>
 <li><a href="contact.html">Contact</a></li>
 </ul>
 </nav>
</header>
```

### Current Page Indicator

Common patterns to show which page the user is on:

```html
<!-- Using a class -->
<li><a href="about.html" class="active">About</a></li>

<!-- Using aria-current -->
<li><a href="about.html" aria-current="page">About</a></li>
```

---

## Lesson 7: Link Best Practices

### Writing Good Link Text

```
┌─────────────────────────────────────────────────────────────────────────────┐
│ LINK TEXT BEST PRACTICES │
├─────────────────────────────────────────────────────────────────────────────┤
│ │
│ BAD GOOD │
│ ═════ ══════ │
│ │
│ Click here Read our privacy policy │
│ Read more View all products │
│ Link Download the brochure │
│ Here Contact our support team │
│ │
│ BAD: "To learn more, click here." │
│ GOOD: "Learn more about our services." │
│ │
│ BAD: "For info, click here, here, and here." │
│ GOOD: "Read about our team, products, and mission." │
│ │
└─────────────────────────────────────────────────────────────────────────────┘
```

**Why good link text matters:**

- Screen readers read links out of context
- Users scan pages looking for links
- Search engines use link text for ranking

### Accessibility Tips

| Practice | Why |
|----------|-----|
| Use descriptive text | Screen readers announce it |
| Don't use "click here" | Meaningless when heard alone |
| Indicate external links | Users know they're leaving |
| Indicate file downloads | Users know what to expect |

### Example: Good Navigation

```html
<nav aria-label="Main navigation">
 <ul>
 <li><a href="index.html">Home</a></li>
 <li><a href="about.html">About KOOMPI</a></li>
 <li><a href="products.html">Our Products</a></li>
 <li><a href="blog.html">Read Our Blog</a></li>
 <li><a href="contact.html">Contact Us</a></li>
 </ul>
</nav>

<p>
 Read our <a href="privacy.html">privacy policy</a> for information 
 about how we protect your data.
</p>

<p>
 Learn more at 
 <a href="https://wikipedia.org" target="_blank" rel="noopener noreferrer">
 Wikipedia (opens in new tab)
 </a>.
</p>
```

---

## Self-Check Exercises

### Exercise 1: Create a Multi-Page Site

Create three HTML files that link to each other:

```
my-site/
├── index.html (Home - links to about and contact)
├── about.html (About - links to home and contact)
└── contact.html (Contact - links to home and about)
```

Each page should have navigation that works correctly.

### Exercise 2: Absolute vs Relative Quiz

Which type of URL would you use?

1. Link to your about page: _______
2. Link to Google: _______
3. Link to a file in a subfolder: _______
4. Link to Facebook: _______
5. Link from subfolder back to home: _______

### Exercise 3: Page with Sections

Create a long page with:

- A table of contents with 4 links
- 4 sections with IDs matching the links
- "Back to top" link at the bottom

### Exercise 4: Contact Page

Create a contact page with:

- Email link (to your email or example)
- Phone link
- Link to open a map (Google Maps URL)
- Download link for a resume/CV

### Exercise 5: Navigation Menu

Create a complete navigation menu with:

- Logo that links to home
- 5 navigation links
- Current page indicator on one link
- At least one external link that opens in new tab

---

## Module Summary

**Elements & Attributes**

| Element/Attribute | Purpose |
|-------------------|---------|
| `<a>` | Creates hyperlinks |
| `href` | Link destination |
| `target` | Where link opens |
| `title` | Tooltip text |
| `download` | Download file |
| `rel` | Link relationship |

**URL Types**

| Type | When to Use | Example |
|------|-------------|---------|
| Absolute | External sites | `https://google.com` |
| Relative | Your own site | `about.html`, `../index.html` |
| Anchor | Same page sections | `#section-id` |
| Email | Contact links | `mailto:email@example.com` |
| Phone | Call links | `tel:+85512345678` |

---

## Next Steps

**Before moving to Module 05:**

- [ ] Create multi-page site with working links
- [ ] Build page with internal navigation
- [ ] Create contact page with special links
- [ ] Get mentor verification

**Coming Next**: Module 05 - Images & Media

*You will learn to add images to your web pages!*

---

<div align="center">

**Links connect the web!** 

*Good navigation makes happy users.*

</div>
