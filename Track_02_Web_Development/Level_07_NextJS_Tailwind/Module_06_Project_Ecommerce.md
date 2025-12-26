# Module 06: Project - E-commerce Store

## Level 2.7: Next.js & Tailwind

---

## Project Overview

Build a complete **E-commerce Store** with Next.js and Tailwind CSS!

This is your capstone project for the Web Development track.

---

## Project Requirements

### Must Have (Required)

| Feature | Skills Demonstrated |
|---------|---------------------|
| Product listing page | Data fetching, SSG/ISR |
| Product detail pages | Dynamic routes |
| Shopping cart | State management |
| Category filtering | Server/client components |
| Responsive design | Tailwind CSS |
| API routes | Backend development |
| Deployed on Vercel | Deployment |

### Nice to Have (Bonus)

| Feature | Skills Shown |
|---------|--------------|
| Search functionality | Query handling |
| User authentication | Auth flow |
| Checkout process | Forms, validation |
| Order history | Database |
| Admin dashboard | Protected routes |

---

## Project Structure

```
ecommerce-store/
├── src/
│ ├── app/
│ │ ├── layout.js
│ │ ├── page.js (Home)
│ │ ├── globals.css
│ │ ├── products/
│ │ │ ├── page.js (Product list)
│ │ │ └── [id]/
│ │ │ └── page.js (Product detail)
│ │ ├── cart/
│ │ │ └── page.js (Cart page)
│ │ └── api/
│ │ ├── products/
│ │ │ └── route.js
│ │ └── cart/
│ │ └── route.js
│ ├── components/
│ │ ├── Header.jsx
│ │ ├── Footer.jsx
│ │ ├── ProductCard.jsx
│ │ ├── CartItem.jsx
│ │ └── CartProvider.jsx
│ └── lib/
│ └── products.js
├── public/
│ └── images/
├── data/
│ └── products.json
└── package.json
```

---

## Step 1: Setup

```bash
npx create-next-app@latest ecommerce-store
# Select: Tailwind CSS, App Router, src/ directory

cd ecommerce-store
npm run dev
```

---

## Step 2: Product Data

```json
// data/products.json
{
 "products": [
 {
 "id": "1",
 "name": "KOOMPI E13",
 "description": "Lightweight laptop with 13-inch display, perfect for students and developers.",
 "price": 299,
 "category": "laptops",
 "image": "/images/koompi-e13.jpg",
 "rating": 4.5,
 "inStock": true
 },
 {
 "id": "2",
 "name": "Wireless Mouse",
 "description": "Ergonomic wireless mouse with long battery life.",
 "price": 25,
 "category": "accessories",
 "image": "/images/mouse.jpg",
 "rating": 4.2,
 "inStock": true
 },
 {
 "id": "3",
 "name": "Mechanical Keyboard",
 "description": "RGB mechanical keyboard with blue switches.",
 "price": 65,
 "category": "accessories",
 "image": "/images/keyboard.jpg",
 "rating": 4.7,
 "inStock": true
 },
 {
 "id": "4",
 "name": "USB-C Hub",
 "description": "7-in-1 USB-C hub with HDMI, USB 3.0, and SD card reader.",
 "price": 45,
 "category": "accessories",
 "image": "/images/usb-hub.jpg",
 "rating": 4.4,
 "inStock": false
 }
 ]
}
```

---

## Step 3: Cart Context

```jsx
// src/components/CartProvider.jsx
'use client';

import { createContext, useContext, useState, useEffect } from 'react';

const CartContext = createContext();

export function CartProvider({ children }) {
 const [cart, setCart] = useState([]);
 
 // Load cart from localStorage
 useEffect(() => {
 const saved = localStorage.getItem('cart');
 if (saved) setCart(JSON.parse(saved));
 }, []);
 
 // Save cart to localStorage
 useEffect(() => {
 localStorage.setItem('cart', JSON.stringify(cart));
 }, [cart]);
 
 const addToCart = (product) => {
 setCart(prev => {
 const existing = prev.find(item => item.id === product.id);
 if (existing) {
 return prev.map(item =>
 item.id === product.id
 ? { ...item, quantity: item.quantity + 1 }
 : item
 );
 }
 return [...prev, { ...product, quantity: 1 }];
 });
 };
 
 const removeFromCart = (productId) => {
 setCart(prev => prev.filter(item => item.id !== productId));
 };
 
 const updateQuantity = (productId, quantity) => {
 if (quantity <= 0) {
 removeFromCart(productId);
 return;
 }
 setCart(prev =>
 prev.map(item =>
 item.id === productId ? { ...item, quantity } : item
 )
 );
 };
 
 const clearCart = () => setCart([]);
 
 const total = cart.reduce(
 (sum, item) => sum + item.price * item.quantity, 0
 );
 
 const itemCount = cart.reduce((sum, item) => sum + item.quantity, 0);
 
 return (
 <CartContext.Provider value={{
 cart,
 addToCart,
 removeFromCart,
 updateQuantity,
 clearCart,
 total,
 itemCount
 }}>
 {children}
 </CartContext.Provider>
 );
}

export const useCart = () => useContext(CartContext);
```

---

## Step 4: Layout

```jsx
// src/app/layout.js
import { Inter } from 'next/font/google';
import './globals.css';
import Header from '@/components/Header';
import Footer from '@/components/Footer';
import { CartProvider } from '@/components/CartProvider';

const inter = Inter({ subsets: ['latin'] });

export const metadata = {
 title: 'KOOMPI Store',
 description: 'Your one-stop shop for tech products',
};

export default function RootLayout({ children }) {
 return (
 <html lang="en">
 <body className={inter.className}>
 <CartProvider>
 <div className="min-h-screen flex flex-col">
 <Header />
 <main className="flex-1">
 {children}
 </main>
 <Footer />
 </div>
 </CartProvider>
 </body>
 </html>
 );
}
```

---

## Step 5: Header Component

```jsx
// src/components/Header.jsx
'use client';

import Link from 'next/link';
import { useCart } from './CartProvider';

export default function Header() {
 const { itemCount } = useCart();
 
 return (
 <header className="bg-white shadow-sm sticky top-0 z-50">
 <div className="max-w-6xl mx-auto px-4">
 <div className="flex justify-between items-center h-16">
 <Link href="/" className="text-2xl font-bold text-blue-600">
 KOOMPI Store
 </Link>
 
 <nav className="hidden md:flex space-x-8">
 <Link href="/products" className="text-gray-600 hover:text-blue-600">
 Products
 </Link>
 <Link href="/products?category=laptops" className="text-gray-600 hover:text-blue-600">
 Laptops
 </Link>
 <Link href="/products?category=accessories" className="text-gray-600 hover:text-blue-600">
 Accessories
 </Link>
 </nav>
 
 <Link 
 href="/cart" 
 className="relative bg-blue-600 text-white px-4 py-2 rounded-lg hover:bg-blue-700"
 >
 Cart
 {itemCount > 0 && (
 <span className="absolute -top-2 -right-2 bg-red-500 text-white text-xs w-5 h-5 rounded-full flex items-center justify-center">
 {itemCount}
 </span>
 )}
 </Link>
 </div>
 </div>
 </header>
 );
}
```

---

## Step 6: Product Card

```jsx
// src/components/ProductCard.jsx
'use client';

import Image from 'next/image';
import Link from 'next/link';
import { useCart } from './CartProvider';

export default function ProductCard({ product }) {
 const { addToCart } = useCart();
 
 return (
 <div className="bg-white rounded-xl shadow-md overflow-hidden hover:shadow-xl transition group">
 <Link href={`/products/${product.id}`}>
 <div className="relative h-48 bg-gray-100">
 <Image
 src={product.image}
 alt={product.name}
 fill
 className="object-contain p-4 group-hover:scale-105 transition"
 />
 </div>
 </Link>
 
 <div className="p-4">
 <div className="flex justify-between items-start mb-2">
 <Link href={`/products/${product.id}`}>
 <h3 className="font-semibold text-lg hover:text-blue-600">
 {product.name}
 </h3>
 </Link>
 <span className="text-yellow-500"> {product.rating}</span>
 </div>
 
 <p className="text-gray-600 text-sm mb-4 line-clamp-2">
 {product.description}
 </p>
 
 <div className="flex justify-between items-center">
 <span className="text-2xl font-bold text-blue-600">
 ${product.price}
 </span>
 
 <button
 onClick={() => addToCart(product)}
 disabled={!product.inStock}
 className={`px-4 py-2 rounded-lg transition ${
 product.inStock
 ? 'bg-blue-600 text-white hover:bg-blue-700'
 : 'bg-gray-300 text-gray-500 cursor-not-allowed'
 }`}
 >
 {product.inStock ? 'Add to Cart' : 'Out of Stock'}
 </button>
 </div>
 </div>
 </div>
 );
}
```

---

## Step 7: Products Page

```jsx
// src/app/products/page.js
import ProductCard from '@/components/ProductCard';
import products from '@/../data/products.json';

export default function ProductsPage({ searchParams }) {
 const category = searchParams?.category;
 
 const filteredProducts = category
 ? products.products.filter(p => p.category === category)
 : products.products;
 
 return (
 <div className="max-w-6xl mx-auto px-4 py-8">
 <div className="flex justify-between items-center mb-8">
 <h1 className="text-3xl font-bold">
 {category ? category.charAt(0).toUpperCase() + category.slice(1) : 'All Products'}
 </h1>
 <p className="text-gray-600">{filteredProducts.length} products</p>
 </div>
 
 <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
 {filteredProducts.map(product => (
 <ProductCard key={product.id} product={product} />
 ))}
 </div>
 </div>
 );
}
```

---

## Step 8: Cart Page

```jsx
// src/app/cart/page.js
'use client';

import { useCart } from '@/components/CartProvider';
import Image from 'next/image';
import Link from 'next/link';

export default function CartPage() {
 const { cart, updateQuantity, removeFromCart, total, clearCart } = useCart();
 
 if (cart.length === 0) {
 return (
 <div className="max-w-4xl mx-auto px-4 py-16 text-center">
 <h1 className="text-3xl font-bold mb-4">Your Cart is Empty</h1>
 <p className="text-gray-600 mb-8">Add some products to get started!</p>
 <Link
 href="/products"
 className="bg-blue-600 text-white px-8 py-3 rounded-lg inline-block hover:bg-blue-700"
 >
 Browse Products
 </Link>
 </div>
 );
 }
 
 return (
 <div className="max-w-4xl mx-auto px-4 py-8">
 <h1 className="text-3xl font-bold mb-8">Shopping Cart</h1>
 
 <div className="space-y-4 mb-8">
 {cart.map(item => (
 <div key={item.id} className="bg-white rounded-lg shadow p-4 flex gap-4">
 <div className="relative w-24 h-24 bg-gray-100 rounded">
 <Image
 src={item.image}
 alt={item.name}
 fill
 className="object-contain p-2"
 />
 </div>
 
 <div className="flex-1">
 <h3 className="font-semibold">{item.name}</h3>
 <p className="text-blue-600 font-bold">${item.price}</p>
 </div>
 
 <div className="flex items-center gap-2">
 <button
 onClick={() => updateQuantity(item.id, item.quantity - 1)}
 className="w-8 h-8 rounded bg-gray-200 hover:bg-gray-300"
 >
 -
 </button>
 <span className="w-8 text-center">{item.quantity}</span>
 <button
 onClick={() => updateQuantity(item.id, item.quantity + 1)}
 className="w-8 h-8 rounded bg-gray-200 hover:bg-gray-300"
 >
 +
 </button>
 </div>
 
 <div className="text-right">
 <p className="font-bold">${item.price * item.quantity}</p>
 <button
 onClick={() => removeFromCart(item.id)}
 className="text-red-500 text-sm hover:underline"
 >
 Remove
 </button>
 </div>
 </div>
 ))}
 </div>
 
 <div className="bg-white rounded-lg shadow p-6">
 <div className="flex justify-between text-xl font-bold mb-6">
 <span>Total:</span>
 <span className="text-blue-600">${total.toFixed(2)}</span>
 </div>
 
 <div className="flex gap-4">
 <button
 onClick={clearCart}
 className="flex-1 py-3 border-2 border-gray-300 rounded-lg hover:bg-gray-50"
 >
 Clear Cart
 </button>
 <button className="flex-1 py-3 bg-blue-600 text-white rounded-lg hover:bg-blue-700">
 Checkout
 </button>
 </div>
 </div>
 </div>
 );
}
```

---

## Evaluation Criteria

| Criteria | Points |
|----------|--------|
| **Functionality** (40) | |
| Product display works | 10 |
| Cart add/remove works | 15 |
| Filtering works | 10 |
| Persistence works | 5 |
| **Code Quality** (25) | |
| Clean components | 10 |
| Next.js best practices | 10 |
| TypeScript (optional) | 5 |
| **Design** (20) | |
| Visual appeal | 10 |
| Responsive | 10 |
| **Deployment** (15) | |
| Deployed to Vercel | 10 |
| No errors | 5 |

---

## Track Complete

Upon completing this project:

 **Full-Stack Apprentice Badge** earned 
 **Next.js & Tailwind Badge** earned 
 **Track 02: Web Development COMPLETE!** 
 Ready for **KOOMPI Software Engineer Capstone** 

---

<div align="center">

**You built a complete e-commerce store!** 

*Full-stack development unlocked.*

*You are now a Full-Stack Apprentice!*



</div>
