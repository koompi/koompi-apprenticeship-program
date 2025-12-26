# Module 07: Project - Personal Bio Page

## Level 2.1: HTML Fundamentals

---

## Project Overview

**Congratulations!** You've learned all the HTML fundamentals. Now it's time to put them together and build your first real project: a **Personal Bio Page**.

This project will showcase everything you've learned and become the foundation of your portfolio.

---

## Project Requirements

### Must Have (Required)

Your Bio Page MUST include:

| Requirement | HTML Elements Used |
|-------------|-------------------|
| Proper HTML5 structure | `<!DOCTYPE>`, `<html>`, `<head>`, `<body>` |
| Page title and metadata | `<title>`, `<meta>` |
| Your name as main heading | `<h1>` |
| At least 3 sections with headings | `<h2>`, `<section>` |
| Multiple paragraphs of text | `<p>` |
| At least one list | `<ul>` or `<ol>` |
| At least one image | `<img>` with proper alt |
| Navigation links | `<nav>`, `<a>` |
| Internal page links (anchors) | `<a href="#id">` |
| At least one external link | `<a target="_blank">` |
| Contact section | Email link, possibly form |
| Semantic HTML | `<header>`, `<main>`, `<footer>` |

### Nice to Have (Bonus)

Score extra points with:

| Bonus Feature | What It Shows |
|---------------|---------------|
| Multiple pages | Link skills |
| Contact form | Form skills |
| Table (skills or education) | Table skills |
| Figure with caption | Advanced images |
| Description list | Semantic knowledge |
| Khmer language content | Bilingual skills |

---

## Project Structure

### Folder Setup

```bash
cd ~/projects/portfolio
mkdir personal-bio
cd personal-bio
mkdir images
touch index.html
touch about.html # Optional: separate about page
touch contact.html # Optional: separate contact page
```

### File Structure

```
personal-bio/
├── index.html ← Main page (required)
├── about.html ← About page (optional)
├── contact.html ← Contact page (optional)
├── images/
│ ├── profile.jpg ← Your photo
│ └── ...
└── README.md ← Project description
```

---

## Page Template

Use this as a starting point:

```html
<!DOCTYPE html>
<html lang="en">
<head>
 <meta charset="UTF-8">
 <meta name="viewport" content="width=device-width, initial-scale=1.0">
 <meta name="description" content="Personal bio page of [Your Name], 
 a KOOMPI Apprentice learning web development.">
 <title>[Your Name] - KOOMPI Apprentice</title>
</head>
<body>
 <!-- Header with Navigation -->
 <header>
 <nav>
 <a href="#about">About</a>
 <a href="#skills">Skills</a>
 <a href="#education">Education</a>
 <a href="#contact">Contact</a>
 </nav>
 </header>
 
 <!-- Main Content -->
 <main>
 <!-- Hero Section -->
 <section id="hero">
 <h1>Your Name Here</h1>
 <p>Your title/role here</p>
 </section>
 
 <!-- About Section -->
 <section id="about">
 <h2>About Me</h2>
 <!-- Your content here -->
 </section>
 
 <!-- Skills Section -->
 <section id="skills">
 <h2>My Skills</h2>
 <!-- Your content here -->
 </section>
 
 <!-- Education Section -->
 <section id="education">
 <h2>Education & Training</h2>
 <!-- Your content here -->
 </section>
 
 <!-- Contact Section -->
 <section id="contact">
 <h2>Contact Me</h2>
 <!-- Your content here -->
 </section>
 </main>
 
 <!-- Footer -->
 <footer>
 <p>&copy; 2024 Your Name. Made with at KOOMPI.</p>
 </footer>
</body>
</html>
```

---

## Section-by-Section Guide

### 1. Header & Navigation

```html
<header>
 <h1>Your Name</h1>
 <p>Future Software Engineer | KOOMPI Apprentice</p>
 
 <nav>
 <ul>
 <li><a href="#about">About</a></li>
 <li><a href="#skills">Skills</a></li>
 <li><a href="#goals">Goals</a></li>
 <li><a href="#contact">Contact</a></li>
 </ul>
 </nav>
</header>
```

### 2. About Section

Include:

- A profile image
- 2-3 paragraphs about yourself
- Where you're from
- What you're learning

```html
<section id="about">
 <h2>About Me</h2>
 
 <figure>
 <img src="images/profile.jpg" 
 alt="Photo of [Your Name] smiling"
 width="200" height="200">
 <figcaption>That's me!</figcaption>
 </figure>
 
 <p>Hello! My name is <strong>[Your Name]</strong>. I am from 
 [Your Province], Cambodia. I am currently an apprentice at KOOMPI, 
 learning to become a software engineer.</p>
 
 <p>I started my journey in [Month Year]. Before this, I was 
 [your previous activity]. I decided to learn technology because 
 [your reason].</p>
 
 <p>When I'm not coding, I enjoy [your hobbies].</p>
</section>
```

### 3. Skills Section

Use a list to show your skills:

```html
<section id="skills">
 <h2>My Skills</h2>
 
 <h3>Technical Skills</h3>
 <ul>
 <li><strong>HTML</strong> - Building web page structure</li>
 <li><strong>Linux Terminal</strong> - Command line navigation</li>
 <li><strong>Typing</strong> - Touch typing in English and Khmer</li>
 <li><strong>File Management</strong> - Organizing projects</li>
 </ul>
 
 <h3>Currently Learning</h3>
 <ul>
 <li>CSS - Styling web pages</li>
 <li>JavaScript - Adding interactivity</li>
 <li>English - Improving communication</li>
 </ul>
 
 <h3>Soft Skills</h3>
 <ul>
 <li>Problem Solving</li>
 <li>Teamwork</li>
 <li>Customer Service</li>
 </ul>
</section>
```

Or use a table:

```html
<section id="skills">
 <h2>My Skills</h2>
 
 <table>
 <caption>Technical Skills Progress</caption>
 <thead>
 <tr>
 <th scope="col">Skill</th>
 <th scope="col">Level</th>
 <th scope="col">Status</th>
 </tr>
 </thead>
 <tbody>
 <tr>
 <td>HTML</td>
 <td>Intermediate</td>
 <td>Completed </td>
 </tr>
 <tr>
 <td>CSS</td>
 <td>Beginner</td>
 <td>Learning </td>
 </tr>
 <tr>
 <td>JavaScript</td>
 <td>Not Started</td>
 <td>Coming Soon </td>
 </tr>
 </tbody>
 </table>
</section>
```

### 4. Education / Journey Section

```html
<section id="education">
 <h2>Education & Training</h2>
 
 <h3>KOOMPI Apprenticeship</h3>
 <p><strong>Period:</strong> [Start Date] - Present</p>
 <p><strong>Focus:</strong> Web Development, English, Business Skills</p>
 <p>Currently in Track 02: Web Development, learning to build 
 modern websites and applications.</p>
 
 <h3>Previous Education</h3>
 <p>[Your school/previous education]</p>
 
 <h3>Certifications</h3>
 <ul>
 <li>Digital Citizen (KOOMPI) - [Date]</li>
 <li>HTML Fundamentals (In Progress)</li>
 </ul>
</section>
```

### 5. Goals Section

```html
<section id="goals">
 <h2>My Goals</h2>
 
 <h3>Short-term Goals (6 months)</h3>
 <ol>
 <li>Complete HTML and CSS certification</li>
 <li>Build 3 complete websites</li>
 <li>Improve English speaking skills</li>
 </ol>
 
 <h3>Long-term Goals (2 years)</h3>
 <ol>
 <li>Become a full-stack developer</li>
 <li>Get a job in the tech industry</li>
 <li>Start my own project or business</li>
 <li>Help other Cambodian youth learn technology</li>
 </ol>
</section>
```

### 6. Contact Section

```html
<section id="contact">
 <h2>Contact Me</h2>
 
 <p>I'd love to hear from you! Whether you have a question, 
 want to collaborate, or just want to say hi, feel free to reach out.</p>
 
 <dl>
 <dt>Email</dt>
 <dd><a href="mailto:your.email@example.com">your.email@example.com</a></dd>
 
 <dt>Phone</dt>
 <dd><a href="tel:+85512345678">+855 12 345 678</a></dd>
 
 <dt>GitHub</dt>
 <dd>
 <a href="https://github.com/yourusername" 
 target="_blank" 
 rel="noopener noreferrer">
 github.com/yourusername
 </a>
 </dd>
 
 <dt>Location</dt>
 <dd>Phnom Penh, Cambodia</dd>
 </dl>
</section>
```

Or with a form:

```html
<section id="contact">
 <h2>Contact Me</h2>
 
 <form action="#" method="POST">
 <div>
 <label for="name">Your Name:</label>
 <input type="text" id="name" name="name" required>
 </div>
 
 <div>
 <label for="email">Your Email:</label>
 <input type="email" id="email" name="email" required>
 </div>
 
 <div>
 <label for="message">Message:</label>
 <textarea id="message" name="message" rows="5" required></textarea>
 </div>
 
 <button type="submit">Send Message</button>
 </form>
</section>
```

### 7. Footer

```html
<footer>
 <nav>
 <a href="#hero">Back to Top</a>
 </nav>
 
 <p>Connect with me:</p>
 <ul>
 <li><a href="mailto:you@example.com">Email</a></li>
 <li><a href="https://github.com/you" target="_blank" rel="noopener">GitHub</a></li>
 </ul>
 
 <p>&copy; 2024 [Your Name]. Made with at KOOMPI, Cambodia.</p>
</footer>
```

---

## Checklist Before Submission

### Technical Requirements

- [ ] Valid HTML5 structure (DOCTYPE, html, head, body)
- [ ] Page title appears in browser tab
- [ ] Charset and viewport meta tags present
- [ ] At least one `<h1>` (only one per page)
- [ ] Proper heading hierarchy (h1 → h2 → h3)
- [ ] All images have alt text
- [ ] All links work correctly
- [ ] Internal navigation with anchors works
- [ ] External links open in new tab
- [ ] Semantic elements used (header, main, footer, nav, section)

### Content Requirements

- [ ] Your real name (or preferred name)
- [ ] About section with multiple paragraphs
- [ ] Skills listed (technical and soft)
- [ ] Education or journey information
- [ ] Goals for the future
- [ ] Contact information

### Quality Check

- [ ] No spelling errors
- [ ] Content is honest and accurate
- [ ] Professional but personal tone
- [ ] Clean, indented code
- [ ] Files organized properly
- [ ] Works when opened in browser

---

## Evaluation Rubric

Your project will be evaluated on:

| Criteria | Points | Description |
|----------|--------|-------------|
| **Structure** | 25 | Proper HTML5 structure, semantics |
| **Content** | 25 | Complete, relevant, personal |
| **Technical** | 25 | Links work, images load, forms function |
| **Quality** | 15 | Clean code, good organization |
| **Creativity** | 10 | Personal touch, goes beyond basics |
| **Total** | 100 | |

### Grading Scale

| Score | Result |
|-------|--------|
| 90-100 | Master Badge |
| 75-89 | Builder Badge |
| 60-74 | Foundation Badge |
| Below 60 | Needs improvement (retry) |

---

## Submission Process

1. **Complete your project** following all requirements
2. **Test it** by opening in browser, clicking all links
3. **Show your mentor** for verification
4. **Push to GitHub** (if you've learned Git)
5. **Present** to fellow apprentices (optional but encouraged)

---

## Example Projects

### What Makes a Good Bio Page

```
┌─────────────────────────────────────────────────────────────────────────────┐
│ GOOD BIO PAGE │
├─────────────────────────────────────────────────────────────────────────────┤
│ │
│ • Personal yet professional │
│ • Shows personality through content │
│ • Includes specific details about journey │
│ • Lists actual skills with honesty │
│ • Has clear goals and aspirations │
│ • Easy to navigate │
│ • All links and images work │
│ • Clean, readable code │
│ │
└─────────────────────────────────────────────────────────────────────────────┘
```

### Common Mistakes to Avoid

```
┌─────────────────────────────────────────────────────────────────────────────┐
│ AVOID THESE │
├─────────────────────────────────────────────────────────────────────────────┤
│ │
│ • Lorem ipsum or placeholder text │
│ • Missing alt text on images │
│ • Broken links │
│ • Wrong heading order (h1 → h3) │
│ • No navigation │
│ • Copied content from examples │
│ • Unclear or vague descriptions │
│ • Overly long pages with no structure │
│ │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## Congratulations

Once you complete this project, you will have:

 Built your first real website
 Applied all HTML fundamentals
 Created the foundation of your portfolio
 Earned your **HTML Fundamentals Badge**
 Qualified for **Web Developer Apprentice** certification (after CSS)

---

## What's Next?

After completing your HTML Bio Page:

1. **Get feedback** from your mentor
2. **Improve** based on feedback
3. **Move to Level 2.2: CSS Styling**
4. **Come back** and make your bio page beautiful with CSS!

---

<div align="center">

**You did it!** 

*Your first website is a huge achievement.*

*This page will grow with you throughout your journey.*



</div>
