# Module 01: Introduction to React

## Level 2.6: React Fundamentals

---

## Module Objectives

By the end of this module, you will be able to:

- Understand what React is and why it's popular
- Set up a React development environment
- Understand JSX syntax
- Create your first React component

---

## Lesson 1: What is React?

### React Defined

- WHAT IS REACT?
- React is a JavaScript LIBRARY for building user interfaces.
- Created by: Facebook (2013)
- Used by: Instagram, Facebook, Netflix, Airbnb, Discord, Notion
- KEY CONCEPTS:
- 1. COMPONENTS
- Build UI from small, reusable pieces
- 2. DECLARATIVE
- Describe WHAT you want, not HOW to do it
- 3. VIRTUAL DOM
- Only updates what changed (fast!)
- 4. ONE-WAY DATA FLOW
- Data flows from parent to child

### Why React?

| Benefit | Description |
|---------|-------------|
| **Component-Based** | Break UI into reusable pieces |
| **Fast Updates** | Virtual DOM minimizes real DOM changes |
| **Large Ecosystem** | Tons of libraries and tools |
| **Job Market** | #1 most wanted frontend skill |
| **Learn Once** | Use for web, mobile (React Native) |

---

## Lesson 2: Setting Up

### Create a React App with Vite

Vite is fast and modern:

```bash
# Create new project
npm create vite@latest my-react-app -- --template react

# Navigate to project
cd my-react-app

# Install dependencies
npm install

# Start development server
npm run dev
```

### Project Structure

```
my-react-app/
├── node_modules/
├── public/
│ └── vite.svg
├── src/
│ ├── assets/
│ ├── App.css
│ ├── App.jsx ← Main component
│ ├── index.css
│ └── main.jsx ← Entry point
├── index.html
├── package.json
└── vite.config.js
```

### Key Files

**main.jsx** - Entry point:

```jsx
import React from 'react'
import ReactDOM from 'react-dom/client'
import App from './App.jsx'
import './index.css'

ReactDOM.createRoot(document.getElementById('root')).render(
 <React.StrictMode>
 <App />
 </React.StrictMode>,
)
```

**App.jsx** - Main component:

```jsx
function App() {
 return (
 <div>
 <h1>Hello React!</h1>
 </div>
 )
}

export default App
```

---

## Lesson 3: Understanding JSX

### What is JSX?

JSX = **J**ava**S**cript **X**ML

It lets you write HTML-like code in JavaScript:

```jsx
// This is JSX
const element = <h1>Hello, World!</h1>;

// It compiles to:
const element = React.createElement('h1', null, 'Hello, World!');
```

### JSX Rules

```jsx
// 1. Single Root Element
// Wrong
return (
 <h1>Title</h1>
 <p>Content</p>
)

// Correct
return (
 <div>
 <h1>Title</h1>
 <p>Content</p>
 </div>
)

// Or use Fragment
return (
 <>
 <h1>Title</h1>
 <p>Content</p>
 </>
)
```

```jsx
// 2. Close All Tags
<br /> // Self-closing
<img /> // Self-closing
<div></div> // Paired
```

```jsx
// 3. className instead of class
<div className="container"> // 
<div class="container"> // 
```

```jsx
// 4. camelCase for attributes
<button onClick={handleClick}> // 
<button onclick={handleClick}> // 

<label htmlFor="email"> // 
<label for="email"> // 
```

### JavaScript in JSX

Use curly braces `{}` for JavaScript:

```jsx
const name = "Sokha";
const items = ["Apple", "Banana", "Orange"];

function App() {
 return (
 <div>
 {/* Variables */}
 <h1>Hello, {name}!</h1>
 
 {/* Expressions */}
 <p>2 + 2 = {2 + 2}</p>
 
 {/* Function calls */}
 <p>Uppercase: {name.toUpperCase()}</p>
 
 {/* Ternary */}
 <p>{name ? `Welcome, ${name}` : 'Please log in'}</p>
 
 {/* Lists */}
 <ul>
 {items.map(item => <li key={item}>{item}</li>)}
 </ul>
 </div>
 );
}
```

---

## Lesson 4: Creating Components

### Function Components

```jsx
// Simple component
function Welcome() {
 return <h1>Welcome to React!</h1>;
}

// With arrow function
const Welcome = () => {
 return <h1>Welcome to React!</h1>;
};

// Shorthand (implicit return)
const Welcome = () => <h1>Welcome to React!</h1>;
```

### Using Components

```jsx
function App() {
 return (
 <div>
 <Welcome />
 <Welcome />
 <Welcome />
 </div>
 );
}
```

### Component with Logic

```jsx
function Greeting() {
 const hour = new Date().getHours();
 
 let greeting;
 if (hour < 12) {
 greeting = "Good morning";
 } else if (hour < 18) {
 greeting = "Good afternoon";
 } else {
 greeting = "Good evening";
 }
 
 return <h1>{greeting}!</h1>;
}
```

---

## Lesson 5: Component Organization

### One Component Per File

```jsx
// components/Header.jsx
function Header() {
 return (
 <header>
 <h1>My App</h1>
 <nav>
 <a href="/">Home</a>
 <a href="/about">About</a>
 </nav>
 </header>
 );
}

export default Header;
```

```jsx
// components/Footer.jsx
function Footer() {
 return (
 <footer>
 <p>&copy; 2024 KOOMPI</p>
 </footer>
 );
}

export default Footer;
```

```jsx
// App.jsx
import Header from './components/Header';
import Footer from './components/Footer';

function App() {
 return (
 <div>
 <Header />
 <main>
 <p>Main content here</p>
 </main>
 <Footer />
 </div>
 );
}

export default App;
```

### Project Structure

```
src/
├── components/
│ ├── Header.jsx
│ ├── Footer.jsx
│ ├── Button.jsx
│ └── Card.jsx
├── pages/
│ ├── Home.jsx
│ └── About.jsx
├── App.jsx
└── main.jsx
```

---

## Lesson 6: Styling Components

### CSS Files

```jsx
// Button.jsx
import './Button.css';

function Button({ children }) {
 return <button className="btn">{children}</button>;
}
```

```css
/* Button.css */
.btn {
 padding: 10px 20px;
 background: #3498db;
 color: white;
 border: none;
 border-radius: 5px;
 cursor: pointer;
}

.btn:hover {
 background: #2980b9;
}
```

### Inline Styles

```jsx
function Card() {
 const cardStyle = {
 backgroundColor: 'white',
 padding: '20px',
 borderRadius: '10px',
 boxShadow: '0 2px 10px rgba(0,0,0,0.1)'
 };
 
 return (
 <div style={cardStyle}>
 <h2>Card Title</h2>
 </div>
 );
}
```

### CSS Modules

```jsx
// Button.module.css
.button {
 padding: 10px 20px;
}

// Button.jsx
import styles from './Button.module.css';

function Button() {
 return <button className={styles.button}>Click</button>;
}
```

---

## Lesson 7: Your First React App

### Create a Simple Greeting App

```jsx
// App.jsx
import './App.css';

function Header() {
 return (
 <header className="header">
 <h1> Welcome to Cambodia</h1>
 </header>
 );
}

function Greeting() {
 const name = "KOOMPI Apprentice";
 const hour = new Date().getHours();
 
 let timeGreeting;
 if (hour < 12) timeGreeting = "Good morning";
 else if (hour < 18) timeGreeting = "Good afternoon";
 else timeGreeting = "Good evening";
 
 return (
 <div className="greeting">
 <h2>{timeGreeting}, {name}!</h2>
 <p>Welcome to your React journey.</p>
 </div>
 );
}

function Features() {
 const features = [
 "Component-based architecture",
 "Virtual DOM for fast updates",
 "Rich ecosystem",
 "Great developer experience"
 ];
 
 return (
 <div className="features">
 <h3>Why React?</h3>
 <ul>
 {features.map((feature, index) => (
 <li key={index}>{feature}</li>
 ))}
 </ul>
 </div>
 );
}

function Footer() {
 return (
 <footer className="footer">
 <p>Built with React </p>
 </footer>
 );
}

function App() {
 return (
 <div className="app">
 <Header />
 <main>
 <Greeting />
 <Features />
 </main>
 <Footer />
 </div>
 );
}

export default App;
```

---

## Self-Check Exercises

### Exercise 1: Setup

Create a new React project with Vite and run it.

### Exercise 2: JSX Practice

Create a component that displays:

- Your name
- A list of 3 hobbies
- The current date

### Exercise 3: Multiple Components

Create these components in separate files:

- `Header.jsx`
- `Main.jsx`
- `Footer.jsx`

Import and use them in `App.jsx`.

### Exercise 4: Styling

Add CSS to make your components look nice.

### Exercise 5: Dynamic Content

Create a component that shows different content based on the time of day.

---

## Module Summary

| Concept | Description |
|---------|-------------|
| React | Library for building UIs |
| Component | Reusable piece of UI |
| JSX | HTML-like syntax in JavaScript |
| Vite | Fast build tool |
| {} | JavaScript expressions in JSX |

---

## Next Steps

**Coming Next**: Module 02 - Components & Props

*You will learn to pass data between components!*

---

<div align="center">

**You're now a React developer!** 

*Components are the building blocks.*

</div>
