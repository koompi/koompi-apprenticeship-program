# Module 04: API Routes

## Level 2.7: Next.js & Tailwind

---

## Module Objectives

By the end of this module, you will be able to:

- Create API endpoints in Next.js
- Handle different HTTP methods
- Connect to databases
- Build a complete CRUD API

---

## Lesson 1: What are API Routes?

### Full-Stack in One Project

```
┌─────────────────────────────────────────────────────────────────────────────┐
│ NEXT.JS = FRONTEND + BACKEND │
├─────────────────────────────────────────────────────────────────────────────┤
│ │
│ TRADITIONAL: NEXT.JS: │
│ ════════════ ════════ │
│ │
│ Frontend (React) ←──→ Backend (Express) │
│ Separate project Separate project │
│ Different deploy Different deploy │
│ │
│ Frontend (React) │
│ + │
│ Backend (API Routes) │
│ ───────────────────── │
│ ONE project, ONE deploy │
│ │
└─────────────────────────────────────────────────────────────────────────────┘
```

### API Route Location

```
app/
├── api/
│ ├── hello/
│ │ └── route.js → GET /api/hello
│ ├── users/
│ │ ├── route.js → /api/users
│ │ └── [id]/
│ │ └── route.js → /api/users/123
│ └── products/
│ └── route.js → /api/products
```

---

## Lesson 2: Basic API Route

### Simple GET Endpoint

```jsx
// app/api/hello/route.js
import { NextResponse } from 'next/server';

export async function GET() {
 return NextResponse.json({ message: 'Hello, World!' });
}
```

Test it: `http://localhost:3000/api/hello`

### With Dynamic Data

```jsx
// app/api/time/route.js
import { NextResponse } from 'next/server';

export async function GET() {
 return NextResponse.json({
 time: new Date().toISOString(),
 timezone: 'Asia/Phnom_Penh'
 });
}
```

---

## Lesson 3: HTTP Methods

### All Methods in One File

```jsx
// app/api/products/route.js
import { NextResponse } from 'next/server';

// Simulated database
let products = [
 { id: 1, name: 'Laptop', price: 299 },
 { id: 2, name: 'Mouse', price: 25 },
];

// GET - List all products
export async function GET() {
 return NextResponse.json(products);
}

// POST - Create new product
export async function POST(request) {
 const body = await request.json();
 
 const newProduct = {
 id: products.length + 1,
 name: body.name,
 price: body.price
 };
 
 products.push(newProduct);
 
 return NextResponse.json(newProduct, { status: 201 });
}
```

### Dynamic Route Methods

```jsx
// app/api/products/[id]/route.js
import { NextResponse } from 'next/server';

// GET single product
export async function GET(request, { params }) {
 const id = parseInt(params.id);
 const product = products.find(p => p.id === id);
 
 if (!product) {
 return NextResponse.json(
 { error: 'Product not found' },
 { status: 404 }
 );
 }
 
 return NextResponse.json(product);
}

// PUT - Update product
export async function PUT(request, { params }) {
 const id = parseInt(params.id);
 const body = await request.json();
 
 const index = products.findIndex(p => p.id === id);
 
 if (index === -1) {
 return NextResponse.json(
 { error: 'Product not found' },
 { status: 404 }
 );
 }
 
 products[index] = { ...products[index], ...body };
 
 return NextResponse.json(products[index]);
}

// DELETE - Remove product
export async function DELETE(request, { params }) {
 const id = parseInt(params.id);
 
 const index = products.findIndex(p => p.id === id);
 
 if (index === -1) {
 return NextResponse.json(
 { error: 'Product not found' },
 { status: 404 }
 );
 }
 
 products.splice(index, 1);
 
 return NextResponse.json({ success: true });
}
```

---

## Lesson 4: Request & Response

### Reading Request Data

```jsx
export async function POST(request) {
 // JSON body
 const body = await request.json();
 
 // URL search params
 const { searchParams } = new URL(request.url);
 const query = searchParams.get('q');
 
 // Headers
 const authHeader = request.headers.get('authorization');
 
 // Cookies
 const cookies = request.cookies;
 const token = cookies.get('token');
 
 return NextResponse.json({ body, query, authHeader });
}
```

### Response Options

```jsx
// JSON response
return NextResponse.json(data);

// With status code
return NextResponse.json(data, { status: 201 });

// With headers
return NextResponse.json(data, {
 headers: {
 'Cache-Control': 'max-age=3600'
 }
});

// Redirect
return NextResponse.redirect(new URL('/login', request.url));

// Error response
return NextResponse.json(
 { error: 'Not Found' },
 { status: 404 }
);
```

---

## Lesson 5: Database Connection

### Using a JSON File (Simple)

```jsx
// lib/db.js
import fs from 'fs/promises';
import path from 'path';

const dbPath = path.join(process.cwd(), 'data', 'db.json');

export async function readDB() {
 const data = await fs.readFile(dbPath, 'utf8');
 return JSON.parse(data);
}

export async function writeDB(data) {
 await fs.writeFile(dbPath, JSON.stringify(data, null, 2));
}
```

### Using with API Route

```jsx
// app/api/todos/route.js
import { NextResponse } from 'next/server';
import { readDB, writeDB } from '@/lib/db';

export async function GET() {
 const db = await readDB();
 return NextResponse.json(db.todos);
}

export async function POST(request) {
 const body = await request.json();
 const db = await readDB();
 
 const newTodo = {
 id: Date.now(),
 text: body.text,
 completed: false
 };
 
 db.todos.push(newTodo);
 await writeDB(db);
 
 return NextResponse.json(newTodo, { status: 201 });
}
```

---

## Lesson 6: Authentication Example

### Login Endpoint

```jsx
// app/api/auth/login/route.js
import { NextResponse } from 'next/server';
import { cookies } from 'next/headers';

// In real app, use proper auth library and database
const users = [
 { id: 1, email: 'sokha@example.com', password: 'password123' }
];

export async function POST(request) {
 const { email, password } = await request.json();
 
 // Find user
 const user = users.find(u => u.email === email && u.password === password);
 
 if (!user) {
 return NextResponse.json(
 { error: 'Invalid credentials' },
 { status: 401 }
 );
 }
 
 // Set cookie (in real app, use proper JWT)
 cookies().set('session', user.id.toString(), {
 httpOnly: true,
 secure: process.env.NODE_ENV === 'production',
 maxAge: 60 * 60 * 24 * 7 // 1 week
 });
 
 return NextResponse.json({
 user: { id: user.id, email: user.email }
 });
}
```

### Protected Route

```jsx
// app/api/profile/route.js
import { NextResponse } from 'next/server';
import { cookies } from 'next/headers';

export async function GET() {
 const session = cookies().get('session');
 
 if (!session) {
 return NextResponse.json(
 { error: 'Unauthorized' },
 { status: 401 }
 );
 }
 
 // Fetch user by session
 // ... 
 
 return NextResponse.json({ user: { /* user data */ } });
}
```

---

## Lesson 7: Complete CRUD Example

### Task Manager API

```jsx
// data/db.json
{
 "tasks": []
}
```

```jsx
// app/api/tasks/route.js
import { NextResponse } from 'next/server';
import { readDB, writeDB } from '@/lib/db';

// GET all tasks
export async function GET() {
 try {
 const db = await readDB();
 return NextResponse.json(db.tasks);
 } catch (error) {
 return NextResponse.json(
 { error: 'Failed to fetch tasks' },
 { status: 500 }
 );
 }
}

// POST new task
export async function POST(request) {
 try {
 const body = await request.json();
 
 if (!body.title) {
 return NextResponse.json(
 { error: 'Title is required' },
 { status: 400 }
 );
 }
 
 const db = await readDB();
 
 const newTask = {
 id: Date.now().toString(),
 title: body.title,
 description: body.description || '',
 completed: false,
 createdAt: new Date().toISOString()
 };
 
 db.tasks.push(newTask);
 await writeDB(db);
 
 return NextResponse.json(newTask, { status: 201 });
 } catch (error) {
 return NextResponse.json(
 { error: 'Failed to create task' },
 { status: 500 }
 );
 }
}
```

```jsx
// app/api/tasks/[id]/route.js
import { NextResponse } from 'next/server';
import { readDB, writeDB } from '@/lib/db';

// GET single task
export async function GET(request, { params }) {
 try {
 const db = await readDB();
 const task = db.tasks.find(t => t.id === params.id);
 
 if (!task) {
 return NextResponse.json(
 { error: 'Task not found' },
 { status: 404 }
 );
 }
 
 return NextResponse.json(task);
 } catch (error) {
 return NextResponse.json(
 { error: 'Failed to fetch task' },
 { status: 500 }
 );
 }
}

// PUT update task
export async function PUT(request, { params }) {
 try {
 const body = await request.json();
 const db = await readDB();
 
 const index = db.tasks.findIndex(t => t.id === params.id);
 
 if (index === -1) {
 return NextResponse.json(
 { error: 'Task not found' },
 { status: 404 }
 );
 }
 
 db.tasks[index] = {
 ...db.tasks[index],
 ...body,
 updatedAt: new Date().toISOString()
 };
 
 await writeDB(db);
 
 return NextResponse.json(db.tasks[index]);
 } catch (error) {
 return NextResponse.json(
 { error: 'Failed to update task' },
 { status: 500 }
 );
 }
}

// DELETE task
export async function DELETE(request, { params }) {
 try {
 const db = await readDB();
 
 const index = db.tasks.findIndex(t => t.id === params.id);
 
 if (index === -1) {
 return NextResponse.json(
 { error: 'Task not found' },
 { status: 404 }
 );
 }
 
 db.tasks.splice(index, 1);
 await writeDB(db);
 
 return NextResponse.json({ success: true });
 } catch (error) {
 return NextResponse.json(
 { error: 'Failed to delete task' },
 { status: 500 }
 );
 }
}
```

---

## Self-Check Exercises

### Exercise 1: Hello API

Create a simple `/api/hello` endpoint.

### Exercise 2: CRUD API

Create a complete CRUD API for a notes app.

### Exercise 3: Query Parameters

Create an endpoint that filters data based on query params.

### Exercise 4: Error Handling

Add proper error handling to your API routes.

### Exercise 5: Protected Endpoint

Create an endpoint that requires authentication.

---

## Module Summary

| Concept | Description |
|---------|-------------|
| `route.js` | API endpoint file |
| `GET`, `POST`, etc. | Export functions for methods |
| `NextResponse.json()` | Return JSON response |
| `request.json()` | Read request body |
| `params` | URL parameters |
| `cookies()` | Access cookies |

---

## Next Steps

**Coming Next**: Module 05 - Deployment

*You will learn to deploy your Next.js app!*

---

<div align="center">

**Full-stack development!** 

*Backend and frontend in harmony.*

</div>
