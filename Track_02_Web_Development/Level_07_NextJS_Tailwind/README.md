# Level 2.7: Next.js & Tailwind CSS

## Track 02: Web Development

---

## Level Overview

Learn production-ready technologies! **Next.js** is a React framework for building full-stack applications, and **Tailwind CSS** is a utility-first CSS framework.

**Duration**: 4-6 weeks

**Modules in this Level:**

1. Introduction to Next.js
2. Tailwind CSS Fundamentals
3. Routing & Navigation
4. Data Fetching
5. API Routes
6. Project: Full-Stack Application

---

## Prerequisites

- Completed React Fundamentals
- Git & GitHub proficiency
- Understanding of APIs

---

## Why Next.js + Tailwind?

```
┌─────────────────────────────────────────────────────────────────────────────┐
│ NEXT.JS + TAILWIND CSS │
├─────────────────────────────────────────────────────────────────────────────┤
│ │
│ NEXT.JS BENEFITS TAILWIND BENEFITS │
│ ════════════════ ═════════════════ │
│ │
│ File-based routing Rapid styling │
│ Server-side rendering No CSS files to manage │
│ API routes built-in Consistent design system │
│ Automatic optimization Responsive made easy │
│ Easy deployment Highly customizable │
│ │
│ USED BY │
│ ═══════ │
│ Netflix, TikTok, Nike, Hulu, Twitch, The Washington Post │
│ │
│ PERFECT FOR │
│ ═══════════ │
│ Production apps, E-commerce, Dashboards, SaaS products │
│ │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## What You'll Build

A **Full-Stack E-commerce Product Catalog**:

- KOOMPI SHOP [Products] [About] [Cart (3)]
- HERO: Discover Amazing Tech Products
- [Shop Now]
- Featured Products
- [Image] [Image] [Image] [Image]
- KOOMPI E13 USB-C Hub Webcam Keyboard
- $299 $45 $65 $55
- [Add Cart] [Add Cart] [Add Cart] [Add Cart]

---

## Module Index

| Module | Topic | Key Concepts |
|--------|-------|--------------|
| 01 | Next.js Setup | Installation, file structure |
| 02 | Tailwind CSS | Utility classes, responsive design |
| 03 | Routing | Pages, dynamic routes, layouts |
| 04 | Data Fetching | getServerSideProps, getStaticProps |
| 05 | API Routes | Backend endpoints, database |
| 06 | Project | Full-Stack E-commerce |

---

## Code Preview

### Next.js Page

```jsx
// app/products/page.jsx
import ProductCard from '@/components/ProductCard';

async function getProducts() {
 const res = await fetch('https://api.example.com/products');
 return res.json();
}

export default async function ProductsPage() {
 const products = await getProducts();
 
 return (
 <div className="container mx-auto px-4 py-8">
 <h1 className="text-3xl font-bold mb-8">Our Products</h1>
 <div className="grid grid-cols-1 md:grid-cols-3 gap-6">
 {products.map(product => (
 <ProductCard key={product.id} product={product} />
 ))}
 </div>
 </div>
 );
}
```

### Tailwind Component

```jsx
function ProductCard({ product }) {
 return (
 <div className="bg-white rounded-lg shadow-md overflow-hidden 
 hover:shadow-xl transition-shadow duration-300">
 <img 
 src={product.image} 
 alt={product.name}
 className="w-full h-48 object-cover"
 />
 <div className="p-4">
 <h3 className="text-lg font-semibold mb-2">
 {product.name}
 </h3>
 <p className="text-gray-600 mb-4">
 ${product.price}
 </p>
 <button className="w-full bg-blue-600 text-white py-2 
 rounded-lg hover:bg-blue-700 
 transition-colors">
 Add to Cart
 </button>
 </div>
 </div>
 );
}
```

---

## Setup

```bash
# Create Next.js app with Tailwind
npx create-next-app@latest my-shop
# Select: Yes to Tailwind CSS
# Select: Yes to App Router

cd my-shop
npm run dev
```

---

## Level Completion

**To complete Level 2.7:**

- [ ] All 6 modules studied
- [ ] Next.js routing mastered
- [ ] Tailwind CSS proficiency
- [ ] API routes working
- [ ] Full-stack project deployed
- [ ] **Next.js & Tailwind Badge** earned

---

## Track Complete

After completing Level 2.7, you have finished **Track 02: Web Development**!

You are now a **Full-Stack Apprentice** with skills in:

- HTML, CSS, JavaScript
- React & Next.js
- Git & GitHub
- API Development
- Deployment

**Ready for your Capstone Project!**

---

<div align="center">

**Production-ready skills!** 

*You can now build real-world applications.*

</div>
