# Module 01: Introduction to Next.js

## Level 2.7: Next.js & Tailwind

---

## Module Objectives

By the end of this module, you will be able to:

- Understand what Next.js is and its benefits
- Set up a Next.js project
- Understand the App Router structure
- Create your first pages

---

## Lesson 1: What is Next.js?

### Next.js Defined

```
┌─────────────────────────────────────────────────────────────────────────────┐
│ NEXT.JS = REACT + SUPERPOWERS │
├─────────────────────────────────────────────────────────────────────────────┤
│ │
│ React alone: Next.js adds: │
│ ════════════ ════════════ │
│ │
│ • Client-side only • Server-side rendering (SSR) │
│ • Manual routing setup • File-based routing │
│ • No built-in API • API routes built-in │
│ • Complex deployment • Easy deployment (Vercel) │
│ • Manual optimization • Automatic optimization │
│ │
│ Next.js is a FRAMEWORK built on top of React. │
│ It provides structure and features out of the box. │
│ │
│ USED BY: Netflix, TikTok, Nike, Hulu, Notion, Twitch │
│ │
└─────────────────────────────────────────────────────────────────────────────┘
```

### Key Features

| Feature | Description |
|---------|-------------|
| **File-based Routing** | Folder structure = URL structure |
| **Server Components** | React components that run on server |
| **Server-side Rendering** | HTML generated on server |
| **Static Generation** | Pre-built pages at build time |
| **API Routes** | Backend endpoints in same project |
| **Automatic Optimization** | Images, fonts, scripts |
| **Built-in CSS Support** | CSS Modules, Tailwind ready |

---

## Lesson 2: Setting Up

### Create Next.js App

```bash
npx create-next-app@latest my-nextjs-app
```

**Prompts (recommended answers):**

```
Would you like to use TypeScript? › No
Would you like to use ESLint? › Yes 
Would you like to use Tailwind CSS? › Yes
Would you like to use `src/` directory? › Yes
Would you like to use App Router? › Yes
Would you like to customize the default import alias? › No
```

### Start Development

```bash
cd my-nextjs-app
npm run dev
```

Open [http://localhost:3000](http://localhost:3000)

---

## Lesson 3: Project Structure

### App Router Structure

```
my-nextjs-app/
├── src/
│ └── app/
│ ├── layout.js ← Root layout (wraps all pages)
│ ├── page.js ← Home page (/)
│ ├── globals.css ← Global styles
│ ├── about/
│ │ └── page.js ← About page (/about)
│ ├── products/
│ │ ├── page.js ← Products list (/products)
│ │ └── [id]/
│ │ └── page.js ← Product detail (/products/123)
│ └── api/
│ └── hello/
│ └── route.js ← API endpoint (/api/hello)
├── public/ ← Static files
├── package.json
├── next.config.js
└── tailwind.config.js
```

### File Naming Convention

| File | Purpose |
|------|---------|
| `page.js` | UI for a route |
| `layout.js` | Shared UI for segment |
| `loading.js` | Loading UI |
| `error.js` | Error UI |
| `not-found.js` | 404 UI |
| `route.js` | API endpoint |

---

## Lesson 4: Pages and Routing

### Creating Pages

```jsx
// src/app/page.js (Home - /)
export default function HomePage() {
 return (
 <main>
 <h1>Welcome to My App</h1>
 <p>This is the home page.</p>
 </main>
 );
}
```

```jsx
// src/app/about/page.js (/about)
export default function AboutPage() {
 return (
 <main>
 <h1>About Us</h1>
 <p>Learn more about our company.</p>
 </main>
 );
}
```

```jsx
// src/app/contact/page.js (/contact)
export default function ContactPage() {
 return (
 <main>
 <h1>Contact Us</h1>
 <form>
 <input type="email" placeholder="Email" />
 <textarea placeholder="Message"></textarea>
 <button type="submit">Send</button>
 </form>
 </main>
 );
}
```

### URL Mapping

| File Path | URL |
|-----------|-----|
| `app/page.js` | `/` |
| `app/about/page.js` | `/about` |
| `app/blog/page.js` | `/blog` |
| `app/blog/[slug]/page.js` | `/blog/my-post` |

---

## Lesson 5: Layouts

### Root Layout

Every app needs a root layout:

```jsx
// src/app/layout.js
import './globals.css';

export const metadata = {
 title: 'My Next.js App',
 description: 'Built with Next.js',
};

export default function RootLayout({ children }) {
 return (
 <html lang="en">
 <body>
 <header>
 <nav>
 <a href="/">Home</a>
 <a href="/about">About</a>
 <a href="/contact">Contact</a>
 </nav>
 </header>
 
 <main>{children}</main>
 
 <footer>
 <p>&copy; 2024 My App</p>
 </footer>
 </body>
 </html>
 );
}
```

### Nested Layouts

```jsx
// src/app/dashboard/layout.js
export default function DashboardLayout({ children }) {
 return (
 <div className="dashboard">
 <aside className="sidebar">
 <nav>
 <a href="/dashboard">Overview</a>
 <a href="/dashboard/settings">Settings</a>
 </nav>
 </aside>
 <div className="content">
 {children}
 </div>
 </div>
 );
}
```

---

## Lesson 6: Navigation

### Link Component

```jsx
import Link from 'next/link';

export default function Navigation() {
 return (
 <nav>
 <Link href="/">Home</Link>
 <Link href="/about">About</Link>
 <Link href="/products">Products</Link>
 <Link href="/contact">Contact</Link>
 </nav>
 );
}
```

### Dynamic Links

```jsx
function ProductList({ products }) {
 return (
 <ul>
 {products.map(product => (
 <li key={product.id}>
 <Link href={`/products/${product.id}`}>
 {product.name}
 </Link>
 </li>
 ))}
 </ul>
 );
}
```

### Programmatic Navigation

```jsx
'use client';

import { useRouter } from 'next/navigation';

export default function SearchForm() {
 const router = useRouter();
 
 const handleSearch = (e) => {
 e.preventDefault();
 const query = e.target.search.value;
 router.push(`/search?q=${query}`);
 };
 
 return (
 <form onSubmit={handleSearch}>
 <input name="search" placeholder="Search..." />
 <button type="submit">Search</button>
 </form>
 );
}
```

---

## Lesson 7: Server vs Client Components

### Server Components (Default)

```jsx
// This is a Server Component (default)
// Runs on the server, can fetch data directly

async function ProductList() {
 const products = await fetch('https://api.example.com/products')
 .then(res => res.json());
 
 return (
 <ul>
 {products.map(p => <li key={p.id}>{p.name}</li>)}
 </ul>
 );
}
```

### Client Components

```jsx
'use client'; // This directive makes it a Client Component

import { useState } from 'react';

export default function Counter() {
 const [count, setCount] = useState(0);
 
 return (
 <div>
 <p>Count: {count}</p>
 <button onClick={() => setCount(count + 1)}>+</button>
 </div>
 );
}
```

### When to Use Each

| Server Component | Client Component |
|------------------|------------------|
| Fetch data | useState, useEffect |
| Access backend resources | Event listeners (onClick) |
| Keep secrets secure | Browser APIs |
| Reduce client JS | Interactivity |

---

## Self-Check Exercises

### Exercise 1: Setup

Create a new Next.js app with Tailwind CSS.

### Exercise 2: Three Pages

Create Home, About, and Contact pages.

### Exercise 3: Navigation

Add a navigation bar to the layout.

### Exercise 4: Nested Layout

Create a dashboard section with its own layout.

### Exercise 5: Dynamic Route

Create a `/blog/[slug]` route that displays the slug.

---

## Module Summary

| Concept | Description |
|---------|-------------|
| Next.js | React framework with SSR |
| App Router | File-based routing system |
| `page.js` | Defines a route's UI |
| `layout.js` | Shared wrapper component |
| Server Component | Default, runs on server |
| Client Component | `'use client'`, interactive |

---

## Next Steps

**Coming Next**: Module 02 - Tailwind CSS Fundamentals

*You will learn rapid styling with utility classes!*

---

<div align="center">

**Next.js powers production apps!** 

*React + Structure + Performance*

</div>
