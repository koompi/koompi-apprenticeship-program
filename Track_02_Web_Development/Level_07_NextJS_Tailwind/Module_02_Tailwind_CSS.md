# Module 02: Tailwind CSS Fundamentals

## Level 2.7: Next.js & Tailwind

---

## Module Objectives

By the end of this module, you will be able to:

- Understand utility-first CSS
- Use Tailwind classes effectively
- Build responsive designs
- Customize Tailwind configuration

---

## Lesson 1: What is Tailwind CSS?

### Utility-First CSS

```
┌─────────────────────────────────────────────────────────────────────────────┐
│ TRADITIONAL CSS vs TAILWIND │
├─────────────────────────────────────────────────────────────────────────────┤
│ │
│ TRADITIONAL CSS: TAILWIND CSS: │
│ ════════════════ ═══════════════ │
│ │
│ .card { <div class="bg-white │
│ background: white; rounded-lg │
│ border-radius: 8px; shadow-md │
│ box-shadow: 0 2px 4px rgba(); p-6"> │
│ padding: 24px; Content │
│ } </div> │
│ │
│ <div class="card"> No CSS file needed! │
│ Content Styles right in HTML │
│ </div> │
│ │
│ + Separate files + Rapid development │
│ + Reusable classes + No naming struggles │
│ - Naming is hard + Consistent design │
│ - Growing CSS files - Long class lists │
│ │
└─────────────────────────────────────────────────────────────────────────────┘
```

### Why Tailwind?

| Benefit | Description |
|---------|-------------|
| **Speed** | Style without leaving HTML |
| **Consistency** | Pre-defined design system |
| **No Dead CSS** | Only used classes in bundle |
| **Responsive** | Built-in breakpoints |
| **Customizable** | Extend or modify anything |

---

## Lesson 2: Core Concepts

### Spacing

```html
<!-- Padding -->
<div class="p-4">All sides padding</div>
<div class="px-4">Horizontal padding</div>
<div class="py-4">Vertical padding</div>
<div class="pt-4">Top padding</div>
<div class="pb-4">Bottom padding</div>
<div class="pl-4">Left padding</div>
<div class="pr-4">Right padding</div>

<!-- Margin (same pattern) -->
<div class="m-4">All sides margin</div>
<div class="mx-auto">Center horizontally</div>
<div class="mt-8">Top margin</div>
```

**Spacing Scale:**

| Class | Size |
|-------|------|
| `0` | 0 |
| `1` | 0.25rem (4px) |
| `2` | 0.5rem (8px) |
| `4` | 1rem (16px) |
| `6` | 1.5rem (24px) |
| `8` | 2rem (32px) |
| `12` | 3rem (48px) |
| `16` | 4rem (64px) |

### Sizing

```html
<!-- Width -->
<div class="w-full">100% width</div>
<div class="w-1/2">50% width</div>
<div class="w-64">256px width</div>
<div class="w-screen">100vw</div>

<!-- Height -->
<div class="h-screen">100vh</div>
<div class="h-full">100% height</div>
<div class="min-h-screen">Min 100vh</div>

<!-- Max width -->
<div class="max-w-md">Max 28rem</div>
<div class="max-w-4xl">Max 56rem</div>
```

---

## Lesson 3: Colors

### Text Colors

```html
<p class="text-black">Black text</p>
<p class="text-white">White text</p>
<p class="text-gray-500">Gray text</p>
<p class="text-red-500">Red text</p>
<p class="text-blue-600">Blue text</p>
<p class="text-green-500">Green text</p>
```

### Background Colors

```html
<div class="bg-white">White background</div>
<div class="bg-gray-100">Light gray</div>
<div class="bg-blue-500">Blue background</div>
<div class="bg-gradient-to-r from-blue-500 to-purple-500">Gradient</div>
```

### Color Scale

Each color has shades from 50-950:

```html
<div class="bg-blue-50">Lightest</div>
<div class="bg-blue-100">...</div>
<div class="bg-blue-500">Medium</div>
<div class="bg-blue-900">Dark</div>
<div class="bg-blue-950">Darkest</div>
```

### Opacity

```html
<div class="bg-black/50">50% opacity black</div>
<div class="text-white/75">75% opacity white text</div>
```

---

## Lesson 4: Typography

### Font Size

```html
<p class="text-xs">Extra small</p>
<p class="text-sm">Small</p>
<p class="text-base">Base (16px)</p>
<p class="text-lg">Large</p>
<p class="text-xl">Extra large</p>
<p class="text-2xl">2x large</p>
<p class="text-4xl">4x large</p>
```

### Font Weight

```html
<p class="font-thin">Thin</p>
<p class="font-normal">Normal</p>
<p class="font-medium">Medium</p>
<p class="font-semibold">Semibold</p>
<p class="font-bold">Bold</p>
```

### Text Alignment & Decoration

```html
<p class="text-left">Left aligned</p>
<p class="text-center">Center aligned</p>
<p class="text-right">Right aligned</p>

<p class="underline">Underlined</p>
<p class="line-through">Strikethrough</p>
<p class="uppercase">UPPERCASE</p>
<p class="capitalize">Capitalize Each Word</p>
```

---

## Lesson 5: Layout with Flexbox & Grid

### Flexbox

```html
<!-- Basic flex container -->
<div class="flex">
 <div>Item 1</div>
 <div>Item 2</div>
</div>

<!-- Direction -->
<div class="flex flex-col">Vertical</div>
<div class="flex flex-row">Horizontal (default)</div>

<!-- Justify (main axis) -->
<div class="flex justify-start">Start</div>
<div class="flex justify-center">Center</div>
<div class="flex justify-end">End</div>
<div class="flex justify-between">Space between</div>
<div class="flex justify-around">Space around</div>

<!-- Align (cross axis) -->
<div class="flex items-start">Top</div>
<div class="flex items-center">Center</div>
<div class="flex items-end">Bottom</div>

<!-- Gap -->
<div class="flex gap-4">Gap between items</div>

<!-- Wrap -->
<div class="flex flex-wrap">Wrap items</div>
```

### Grid

```html
<!-- Basic grid -->
<div class="grid grid-cols-3 gap-4">
 <div>1</div>
 <div>2</div>
 <div>3</div>
</div>

<!-- Responsive columns -->
<div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-4">
 <!-- 1 col on mobile, 2 on tablet, 4 on desktop -->
</div>

<!-- Column span -->
<div class="grid grid-cols-4">
 <div class="col-span-2">Spans 2 columns</div>
 <div>Normal</div>
 <div>Normal</div>
</div>
```

---

## Lesson 6: Responsive Design

### Breakpoints

| Prefix | Min-width | CSS |
|--------|-----------|-----|
| `sm:` | 640px | @media (min-width: 640px) |
| `md:` | 768px | @media (min-width: 768px) |
| `lg:` | 1024px | @media (min-width: 1024px) |
| `xl:` | 1280px | @media (min-width: 1280px) |
| `2xl:` | 1536px | @media (min-width: 1536px) |

### Mobile-First Approach

```html
<!-- Mobile first, then add larger screen styles -->
<div class="
 text-sm /* Mobile: small text */
 md:text-base /* Tablet: base text */
 lg:text-lg /* Desktop: large text */
">
 Responsive text
</div>

<div class="
 flex flex-col /* Mobile: stack vertically */
 md:flex-row /* Tablet+: side by side */
">
 <div>Sidebar</div>
 <div>Content</div>
</div>

<div class="
 p-4 /* Mobile: small padding */
 md:p-8 /* Tablet: medium padding */
 lg:p-12 /* Desktop: large padding */
">
 Responsive padding
</div>
```

### Hide/Show at Breakpoints

```html
<div class="hidden md:block">
 Only visible on tablet and up
</div>

<div class="block md:hidden">
 Only visible on mobile
</div>
```

---

## Lesson 7: Common Components

### Card Component

```html
<div class="bg-white rounded-lg shadow-md overflow-hidden">
 <img src="/image.jpg" alt="Product" class="w-full h-48 object-cover" />
 <div class="p-6">
 <h3 class="text-xl font-semibold mb-2">Product Name</h3>
 <p class="text-gray-600 mb-4">Product description goes here.</p>
 <div class="flex justify-between items-center">
 <span class="text-2xl font-bold text-blue-600">$99</span>
 <button class="bg-blue-600 text-white px-4 py-2 rounded-lg hover:bg-blue-700">
 Add to Cart
 </button>
 </div>
 </div>
</div>
```

### Button Variants

```html
<!-- Primary -->
<button class="bg-blue-600 text-white px-6 py-2 rounded-lg hover:bg-blue-700 transition">
 Primary
</button>

<!-- Secondary -->
<button class="bg-gray-200 text-gray-800 px-6 py-2 rounded-lg hover:bg-gray-300 transition">
 Secondary
</button>

<!-- Outline -->
<button class="border-2 border-blue-600 text-blue-600 px-6 py-2 rounded-lg hover:bg-blue-600 hover:text-white transition">
 Outline
</button>

<!-- Danger -->
<button class="bg-red-600 text-white px-6 py-2 rounded-lg hover:bg-red-700 transition">
 Danger
</button>
```

### Navigation Bar

```html
<nav class="bg-white shadow-md">
 <div class="max-w-6xl mx-auto px-4">
 <div class="flex justify-between items-center h-16">
 <!-- Logo -->
 <a href="/" class="text-xl font-bold text-blue-600">
 KOOMPI
 </a>
 
 <!-- Desktop Nav -->
 <div class="hidden md:flex space-x-8">
 <a href="/" class="text-gray-600 hover:text-blue-600">Home</a>
 <a href="/products" class="text-gray-600 hover:text-blue-600">Products</a>
 <a href="/about" class="text-gray-600 hover:text-blue-600">About</a>
 <a href="/contact" class="text-gray-600 hover:text-blue-600">Contact</a>
 </div>
 
 <!-- Mobile menu button -->
 <button class="md:hidden">
 <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
 <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16" />
 </svg>
 </button>
 </div>
 </div>
</nav>
```

---

## Self-Check Exercises

### Exercise 1: Button Styles

Create 4 different button styles using Tailwind.

### Exercise 2: Responsive Grid

Create a grid that's 1 column on mobile, 2 on tablet, 4 on desktop.

### Exercise 3: Card Component

Build a product card with image, title, description, price, and button.

### Exercise 4: Navigation

Create a responsive navigation bar.

### Exercise 5: Hero Section

Build a full-width hero section with centered text and call-to-action.

---

## Module Summary

| Category | Common Classes |
|----------|----------------|
| Spacing | `p-4`, `m-4`, `px-6`, `my-8` |
| Colors | `text-blue-600`, `bg-gray-100` |
| Typography | `text-xl`, `font-bold` |
| Layout | `flex`, `grid`, `justify-center` |
| Responsive | `md:flex`, `lg:grid-cols-4` |
| Effects | `shadow-md`, `rounded-lg`, `hover:` |

---

## Next Steps

**Coming Next**: Module 03 - Data Fetching

*You will learn to fetch and display data in Next.js!*

---

<div align="center">

**Style at the speed of thought!** 

*Utility classes = rapid development*

</div>
