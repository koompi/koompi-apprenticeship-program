# Module 07: Project - Styled Portfolio

## Level 2.2: CSS Styling

---

## Project Overview

It's time to combine everything you've learned! You will transform your HTML Bio Page into a beautiful, professional, responsive portfolio website.

---

## Project Requirements

### Must Have (Required)

| Requirement | CSS Concepts Used |
|-------------|------------------|
| External CSS file(s) | External stylesheets |
| Custom color scheme | Color properties |
| Custom fonts (Google Fonts) | Typography |
| Styled navigation with hover effects | Selectors, transitions |
| Proper spacing (margin/padding) | Box model |
| Cards or styled sections | Borders, backgrounds |
| Responsive design (mobile + desktop) | Media queries |
| Smooth transitions on interactions | Transitions |
| Flexbox for layout | Flexbox |
| Centered container | Max-width, margin auto |

### Nice to Have (Bonus)

| Feature | Skills Shown |
|---------|--------------|
| Background image or gradient | Background properties |
| Sticky navigation | Position fixed |
| Animated buttons | Transform, transition |
| Custom scrollbar | Advanced styling |
| Dark/light sections | Color contrast |
| Icon integration | External assets |

---

## Project Structure

```
portfolio/
├── index.html
├── about.html (optional)
├── contact.html (optional)
├── css/
│ └── style.css
├── images/
│ ├── profile.jpg
│ └── ...
└── README.md
```

---

## Step-by-Step Guide

### Step 1: CSS Reset & Base Styles

```css
/* css/style.css */

/* ==========================================
 CSS RESET & BASE
 ========================================== */

*, *::before, *::after {
 margin: 0;
 padding: 0;
 box-sizing: border-box;
}

html {
 scroll-behavior: smooth;
}

body {
 font-family: 'Open Sans', Arial, sans-serif;
 font-size: 16px;
 line-height: 1.6;
 color: #333;
 background-color: #f5f5f5;
}

img {
 max-width: 100%;
 height: auto;
}

a {
 text-decoration: none;
 color: inherit;
}

ul {
 list-style: none;
}
```

### Step 2: CSS Variables (Optional but Recommended)

```css
/* ==========================================
 CSS VARIABLES (Custom Properties)
 ========================================== */

:root {
 /* Colors */
 --primary: #3498db;
 --primary-dark: #2980b9;
 --secondary: #2ecc71;
 --dark: #2c3e50;
 --light: #ecf0f1;
 --text: #333333;
 --text-light: #666666;
 --white: #ffffff;
 
 /* Spacing */
 --space-xs: 5px;
 --space-sm: 10px;
 --space-md: 20px;
 --space-lg: 40px;
 --space-xl: 80px;
 
 /* Transitions */
 --transition: 0.3s ease;
 
 /* Border radius */
 --radius: 8px;
 
 /* Shadows */
 --shadow: 0 2px 10px rgba(0,0,0,0.1);
 --shadow-lg: 0 10px 30px rgba(0,0,0,0.15);
}
```

### Step 3: Layout Classes

```css
/* ==========================================
 LAYOUT
 ========================================== */

.container {
 max-width: 1200px;
 margin: 0 auto;
 padding: 0 var(--space-md);
}

.section {
 padding: var(--space-xl) 0;
}

.section-dark {
 background-color: var(--dark);
 color: var(--white);
}

.section-light {
 background-color: var(--white);
}

.flex {
 display: flex;
}

.flex-center {
 display: flex;
 justify-content: center;
 align-items: center;
}

.flex-between {
 display: flex;
 justify-content: space-between;
 align-items: center;
}
```

### Step 4: Navigation Styling

```css
/* ==========================================
 NAVIGATION
 ========================================== */

.navbar {
 position: fixed;
 top: 0;
 left: 0;
 width: 100%;
 background-color: var(--dark);
 padding: var(--space-sm) 0;
 z-index: 1000;
 box-shadow: var(--shadow);
}

.navbar .container {
 display: flex;
 justify-content: space-between;
 align-items: center;
}

.logo {
 font-size: 1.5rem;
 font-weight: 700;
 color: var(--white);
}

.nav-links {
 display: flex;
 gap: var(--space-md);
}

.nav-links a {
 color: var(--light);
 padding: var(--space-sm) var(--space-md);
 border-radius: var(--radius);
 transition: var(--transition);
}

.nav-links a:hover {
 background-color: var(--primary);
 color: var(--white);
}

/* Space for fixed navbar */
body {
 padding-top: 60px;
}
```

### Step 5: Hero Section

```css
/* ==========================================
 HERO SECTION
 ========================================== */

.hero {
 min-height: 80vh;
 display: flex;
 align-items: center;
 background: linear-gradient(135deg, var(--dark) 0%, var(--primary) 100%);
 color: var(--white);
 text-align: center;
}

.hero h1 {
 font-size: 3rem;
 margin-bottom: var(--space-md);
}

.hero p {
 font-size: 1.25rem;
 opacity: 0.9;
 margin-bottom: var(--space-lg);
}

.hero-image {
 width: 150px;
 height: 150px;
 border-radius: 50%;
 border: 4px solid var(--white);
 margin-bottom: var(--space-md);
}
```

### Step 6: Cards & Content

```css
/* ==========================================
 CARDS
 ========================================== */

.cards {
 display: flex;
 flex-wrap: wrap;
 gap: var(--space-md);
}

.card {
 flex: 1 1 300px;
 background-color: var(--white);
 border-radius: var(--radius);
 box-shadow: var(--shadow);
 padding: var(--space-lg);
 transition: var(--transition);
}

.card:hover {
 transform: translateY(-5px);
 box-shadow: var(--shadow-lg);
}

.card h3 {
 color: var(--dark);
 margin-bottom: var(--space-sm);
}

.card p {
 color: var(--text-light);
}
```

### Step 7: Buttons

```css
/* ==========================================
 BUTTONS
 ========================================== */

.btn {
 display: inline-block;
 padding: 12px 30px;
 border-radius: var(--radius);
 font-weight: 600;
 cursor: pointer;
 transition: var(--transition);
 border: none;
}

.btn-primary {
 background-color: var(--primary);
 color: var(--white);
}

.btn-primary:hover {
 background-color: var(--primary-dark);
 transform: translateY(-2px);
}

.btn-outline {
 background-color: transparent;
 border: 2px solid var(--white);
 color: var(--white);
}

.btn-outline:hover {
 background-color: var(--white);
 color: var(--dark);
}
```

### Step 8: Footer

```css
/* ==========================================
 FOOTER
 ========================================== */

.footer {
 background-color: var(--dark);
 color: var(--light);
 padding: var(--space-lg) 0;
 text-align: center;
}

.footer a {
 color: var(--primary);
 transition: var(--transition);
}

.footer a:hover {
 color: var(--white);
}
```

### Step 9: Responsive Design

```css
/* ==========================================
 RESPONSIVE DESIGN
 ========================================== */

/* Tablet */
@media (max-width: 768px) {
 .hero h1 {
 font-size: 2rem;
 }
 
 .hero p {
 font-size: 1rem;
 }
 
 .nav-links {
 display: none; /* Add hamburger menu later */
 }
 
 .section {
 padding: var(--space-lg) 0;
 }
 
 .card {
 flex: 1 1 100%;
 }
}

/* Mobile */
@media (max-width: 480px) {
 .hero h1 {
 font-size: 1.75rem;
 }
 
 .container {
 padding: 0 var(--space-sm);
 }
 
 .btn {
 display: block;
 width: 100%;
 text-align: center;
 }
}
```

---

## Complete HTML Template

```html
<!DOCTYPE html>
<html lang="en">
<head>
 <meta charset="UTF-8">
 <meta name="viewport" content="width=device-width, initial-scale=1.0">
 <title>Your Name - Portfolio</title>
 
 <!-- Google Fonts -->
 <link href="https://fonts.googleapis.com/css2?family=Open+Sans:wght@400;600;700&display=swap" rel="stylesheet">
 
 <!-- Your CSS -->
 <link rel="stylesheet" href="css/style.css">
</head>
<body>
 <!-- Navigation -->
 <nav class="navbar">
 <div class="container flex-between">
 <a href="#" class="logo">Your Name</a>
 <ul class="nav-links">
 <li><a href="#about">About</a></li>
 <li><a href="#skills">Skills</a></li>
 <li><a href="#projects">Projects</a></li>
 <li><a href="#contact">Contact</a></li>
 </ul>
 </div>
 </nav>
 
 <!-- Hero Section -->
 <section class="hero">
 <div class="container">
 <img src="images/profile.jpg" alt="Your Name" class="hero-image">
 <h1>Hi, I'm [Your Name]</h1>
 <p>KOOMPI Apprentice | Future Software Engineer</p>
 <a href="#about" class="btn btn-outline">Learn More</a>
 </div>
 </section>
 
 <!-- About Section -->
 <section id="about" class="section section-light">
 <div class="container">
 <h2>About Me</h2>
 <p>Your story here...</p>
 </div>
 </section>
 
 <!-- Skills Section -->
 <section id="skills" class="section">
 <div class="container">
 <h2>My Skills</h2>
 <div class="cards">
 <div class="card">
 <h3>HTML</h3>
 <p>Building structured web pages</p>
 </div>
 <div class="card">
 <h3>CSS</h3>
 <p>Styling beautiful interfaces</p>
 </div>
 <div class="card">
 <h3>JavaScript</h3>
 <p>Coming soon...</p>
 </div>
 </div>
 </div>
 </section>
 
 <!-- Contact Section -->
 <section id="contact" class="section section-dark">
 <div class="container">
 <h2>Get In Touch</h2>
 <p>email@example.com</p>
 <a href="mailto:email@example.com" class="btn btn-primary">Email Me</a>
 </div>
 </section>
 
 <!-- Footer -->
 <footer class="footer">
 <div class="container">
 <p>&copy; 2024 Your Name. Built at KOOMPI </p>
 </div>
 </footer>
</body>
</html>
```

---

## Evaluation Checklist

### Technical (60 points)

- [ ] External CSS file linked (5)
- [ ] CSS reset applied (5)
- [ ] Custom color scheme with variables (10)
- [ ] Google Fonts integrated (5)
- [ ] Navigation styled with hover effects (10)
- [ ] Flexbox used for layout (10)
- [ ] Responsive design works on mobile (10)
- [ ] Transitions on interactive elements (5)

### Visual Design (25 points)

- [ ] Consistent color palette (5)
- [ ] Good typography hierarchy (5)
- [ ] Appropriate spacing (5)
- [ ] Visual balance and alignment (5)
- [ ] Professional appearance (5)

### Code Quality (15 points)

- [ ] Well-organized CSS with comments (5)
- [ ] Meaningful class names (5)
- [ ] No unused code (5)

---

## Level Complete

Upon submitting your styled portfolio:

 **CSS Styling Badge** earned
 **Web Developer Apprentice Certificate** awarded (combined with HTML)
 Ready for **Level 2.3: JavaScript**

---

<div align="center">

**You did it!** 

*Your first portfolio website is complete!*

*This is the beginning of your professional presence online.*



</div>
