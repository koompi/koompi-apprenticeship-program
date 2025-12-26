# Module 03: Data Fetching in Next.js

## Level 2.7: Next.js & Tailwind

---

## 🎯 Module Objectives

By the end of this module, you will be able to:

- Fetch data in Server Components
- Understand SSR, SSG, and ISR
- Handle loading and error states
- Cache and revalidate data

---

## Lesson 1: Data Fetching Basics

### Server Components Can Fetch Directly

```jsx
// app/products/page.js
// This is a Server Component - can use async/await directly!

async function getProducts() {
  const res = await fetch('https://api.example.com/products');
  
  if (!res.ok) {
    throw new Error('Failed to fetch products');
  }
  
  return res.json();
}

export default async function ProductsPage() {
  const products = await getProducts();
  
  return (
    <div>
      <h1>Products</h1>
      <ul>
        {products.map(product => (
          <li key={product.id}>{product.name}</li>
        ))}
      </ul>
    </div>
  );
}
```

### Benefits of Server Fetching

| Benefit | Description |
|---------|-------------|
| No client JS | Data fetched before HTML sent |
| Secure | API keys stay on server |
| Fast | Closer to data source |
| SEO | Content in initial HTML |

---

## Lesson 2: Rendering Strategies

### Static Generation (SSG)

Default behavior - generated at build time:

```jsx
// Fetched at build time, cached indefinitely
async function getData() {
  const res = await fetch('https://api.example.com/data');
  return res.json();
}
```

### Server-Side Rendering (SSR)

Fetch fresh data on every request:

```jsx
// Fetched on every request
async function getData() {
  const res = await fetch('https://api.example.com/data', {
    cache: 'no-store'  // Don't cache
  });
  return res.json();
}
```

### Incremental Static Regeneration (ISR)

Revalidate after a time period:

```jsx
// Revalidate every 60 seconds
async function getData() {
  const res = await fetch('https://api.example.com/data', {
    next: { revalidate: 60 }  // Revalidate every 60 seconds
  });
  return res.json();
}
```

### Comparison

| Strategy | When to Use | Cache |
|----------|-------------|-------|
| **SSG** | Data rarely changes | Forever (until rebuild) |
| **ISR** | Data changes periodically | Revalidate after time |
| **SSR** | Data changes frequently | No cache |

---

## Lesson 3: Dynamic Routes with Data

### Fetching by Parameter

```jsx
// app/products/[id]/page.js
async function getProduct(id) {
  const res = await fetch(`https://api.example.com/products/${id}`);
  
  if (!res.ok) {
    throw new Error('Product not found');
  }
  
  return res.json();
}

export default async function ProductPage({ params }) {
  const product = await getProduct(params.id);
  
  return (
    <div>
      <h1>{product.name}</h1>
      <p>{product.description}</p>
      <p className="text-2xl font-bold">${product.price}</p>
    </div>
  );
}
```

### Generate Static Params

Pre-generate pages for known IDs:

```jsx
// app/products/[id]/page.js
export async function generateStaticParams() {
  const products = await fetch('https://api.example.com/products')
    .then(res => res.json());
  
  return products.map(product => ({
    id: product.id.toString()
  }));
}
```

---

## Lesson 4: Loading States

### loading.js File

```jsx
// app/products/loading.js
export default function Loading() {
  return (
    <div className="flex justify-center items-center min-h-screen">
      <div className="animate-spin rounded-full h-12 w-12 border-4 border-blue-600 border-t-transparent"></div>
    </div>
  );
}
```

### Skeleton Loading

```jsx
// app/products/loading.js
export default function Loading() {
  return (
    <div className="grid grid-cols-1 md:grid-cols-3 gap-6">
      {[1, 2, 3, 4, 5, 6].map(i => (
        <div key={i} className="bg-white rounded-lg p-4 animate-pulse">
          <div className="bg-gray-300 h-48 rounded mb-4"></div>
          <div className="bg-gray-300 h-6 rounded mb-2"></div>
          <div className="bg-gray-300 h-4 rounded w-2/3"></div>
        </div>
      ))}
    </div>
  );
}
```

### Suspense for Specific Components

```jsx
import { Suspense } from 'react';

export default function Page() {
  return (
    <div>
      <h1>Dashboard</h1>
      
      <Suspense fallback={<StatsLoading />}>
        <Stats />
      </Suspense>
      
      <Suspense fallback={<ChartLoading />}>
        <Chart />
      </Suspense>
    </div>
  );
}
```

---

## Lesson 5: Error Handling

### error.js File

```jsx
'use client';  // Error components must be Client Components

// app/products/error.js
export default function Error({ error, reset }) {
  return (
    <div className="text-center py-10">
      <h2 className="text-2xl font-bold text-red-600 mb-4">
        Something went wrong!
      </h2>
      <p className="text-gray-600 mb-4">{error.message}</p>
      <button
        onClick={() => reset()}
        className="bg-blue-600 text-white px-6 py-2 rounded-lg"
      >
        Try again
      </button>
    </div>
  );
}
```

### Not Found

```jsx
// app/products/[id]/not-found.js
import Link from 'next/link';

export default function NotFound() {
  return (
    <div className="text-center py-20">
      <h1 className="text-4xl font-bold mb-4">404</h1>
      <p className="text-gray-600 mb-8">Product not found</p>
      <Link 
        href="/products"
        className="bg-blue-600 text-white px-6 py-2 rounded-lg"
      >
        Back to Products
      </Link>
    </div>
  );
}
```

### Using notFound()

```jsx
import { notFound } from 'next/navigation';

async function getProduct(id) {
  const res = await fetch(`https://api.example.com/products/${id}`);
  
  if (!res.ok) {
    notFound();  // Triggers not-found.js
  }
  
  return res.json();
}
```

---

## Lesson 6: Practical Example

### Product Listing Page

```jsx
// app/products/page.js
import Link from 'next/link';
import Image from 'next/image';

async function getProducts() {
  const res = await fetch('https://fakestoreapi.com/products', {
    next: { revalidate: 3600 }  // Revalidate every hour
  });
  return res.json();
}

export default async function ProductsPage() {
  const products = await getProducts();
  
  return (
    <div className="max-w-6xl mx-auto px-4 py-8">
      <h1 className="text-3xl font-bold mb-8">Our Products</h1>
      
      <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-6">
        {products.map(product => (
          <Link 
            key={product.id}
            href={`/products/${product.id}`}
            className="bg-white rounded-lg shadow-md overflow-hidden hover:shadow-lg transition"
          >
            <div className="relative h-48">
              <Image
                src={product.image}
                alt={product.title}
                fill
                className="object-contain p-4"
              />
            </div>
            <div className="p-4">
              <h2 className="font-semibold mb-2 line-clamp-1">
                {product.title}
              </h2>
              <p className="text-xl font-bold text-blue-600">
                ${product.price}
              </p>
            </div>
          </Link>
        ))}
      </div>
    </div>
  );
}
```

### Product Detail Page

```jsx
// app/products/[id]/page.js
import Image from 'next/image';
import { notFound } from 'next/navigation';

async function getProduct(id) {
  const res = await fetch(`https://fakestoreapi.com/products/${id}`);
  
  if (!res.ok) {
    notFound();
  }
  
  return res.json();
}

export default async function ProductPage({ params }) {
  const product = await getProduct(params.id);
  
  return (
    <div className="max-w-4xl mx-auto px-4 py-8">
      <div className="grid md:grid-cols-2 gap-8">
        <div className="relative h-96">
          <Image
            src={product.image}
            alt={product.title}
            fill
            className="object-contain"
          />
        </div>
        
        <div>
          <h1 className="text-2xl font-bold mb-4">{product.title}</h1>
          <p className="text-gray-600 mb-4">{product.description}</p>
          <p className="text-3xl font-bold text-blue-600 mb-6">
            ${product.price}
          </p>
          <button className="w-full bg-blue-600 text-white py-3 rounded-lg font-semibold hover:bg-blue-700">
            Add to Cart
          </button>
        </div>
      </div>
    </div>
  );
}

export async function generateStaticParams() {
  const products = await fetch('https://fakestoreapi.com/products')
    .then(res => res.json());
  
  return products.map(product => ({
    id: product.id.toString()
  }));
}
```

---

## Lesson 7: Metadata for SEO

### Static Metadata

```jsx
// app/products/page.js
export const metadata = {
  title: 'Products | My Store',
  description: 'Browse our collection of products',
};
```

### Dynamic Metadata

```jsx
// app/products/[id]/page.js
export async function generateMetadata({ params }) {
  const product = await getProduct(params.id);
  
  return {
    title: `${product.title} | My Store`,
    description: product.description,
    openGraph: {
      images: [product.image],
    },
  };
}
```

---

## 🧪 Self-Check Exercises

### Exercise 1: Basic Fetch

Create a page that fetches and displays a list of posts.

### Exercise 2: Dynamic Route

Create a post detail page with dynamic routing.

### Exercise 3: Loading State

Add a skeleton loading state for the posts page.

### Exercise 4: Error Handling

Add error handling with a custom error component.

### Exercise 5: Metadata

Add appropriate SEO metadata to your pages.

---

## 📝 Module Summary

| Concept | Description |
|---------|-------------|
| Server Components | Fetch data directly, no client JS |
| SSG | Static, built at compile time |
| SSR | Fresh data every request |
| ISR | Revalidate periodically |
| loading.js | Loading UI |
| error.js | Error boundary |
| notFound() | Trigger 404 page |

---

## 🎯 Next Steps

**Coming Next**: Module 04 - API Routes

*You will learn to build backend endpoints!*

---

<div align="center">

**Data powers your app!** 📊

*Fetch smart, render fast.*

</div>
