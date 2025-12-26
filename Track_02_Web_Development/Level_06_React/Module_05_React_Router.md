# Module 05: React Router

## Level 2.6: React Fundamentals

---

## Module Objectives

By the end of this module, you will be able to:

- Add routing to a React application
- Create navigation between pages
- Handle dynamic routes
- Implement protected routes

---

## Lesson 1: What is Routing?

### Single Page Applications (SPA)

```
┌─────────────────────────────────────────────────────────────────────────────┐
│ SPA ROUTING │
├─────────────────────────────────────────────────────────────────────────────┤
│ │
│ TRADITIONAL SPA (React) │
│ ═══════════ ════════════ │
│ │
│ /home → Load page.html /home → Show <Home /> │
│ /about → Load about.html /about → Show <About /> │
│ /contact → Load contact.html /contact → Show <Contact /> │
│ │
│ Full page reload each time Same page, different component │
│ Slow, jarring Fast, smooth │
│ │
│ React Router handles URL changes without page reloads │
│ │
└─────────────────────────────────────────────────────────────────────────────┘
```

### Installation

```bash
npm install react-router-dom
```

---

## Lesson 2: Basic Setup

### BrowserRouter

Wrap your app:

```jsx
// main.jsx
import { BrowserRouter } from 'react-router-dom';

ReactDOM.createRoot(document.getElementById('root')).render(
 <BrowserRouter>
 <App />
 </BrowserRouter>
);
```

### Routes and Route

```jsx
// App.jsx
import { Routes, Route } from 'react-router-dom';
import Home from './pages/Home';
import About from './pages/About';
import Contact from './pages/Contact';

function App() {
 return (
 <Routes>
 <Route path="/" element={<Home />} />
 <Route path="/about" element={<About />} />
 <Route path="/contact" element={<Contact />} />
 </Routes>
 );
}
```

---

## Lesson 3: Navigation

### Link Component

```jsx
import { Link } from 'react-router-dom';

function Navigation() {
 return (
 <nav>
 <Link to="/">Home</Link>
 <Link to="/about">About</Link>
 <Link to="/contact">Contact</Link>
 </nav>
 );
}
```

### NavLink for Active Styling

```jsx
import { NavLink } from 'react-router-dom';

function Navigation() {
 return (
 <nav>
 <NavLink 
 to="/"
 className={({ isActive }) => isActive ? 'active' : ''}
 >
 Home
 </NavLink>
 <NavLink 
 to="/about"
 className={({ isActive }) => isActive ? 'active' : ''}
 >
 About
 </NavLink>
 </nav>
 );
}
```

### Programmatic Navigation

```jsx
import { useNavigate } from 'react-router-dom';

function LoginForm() {
 const navigate = useNavigate();
 
 const handleSubmit = async (e) => {
 e.preventDefault();
 // ... login logic
 navigate('/dashboard'); // Redirect after login
 };
 
 return (
 <form onSubmit={handleSubmit}>
 {/* form fields */}
 </form>
 );
}
```

---

## Lesson 4: Dynamic Routes

### URL Parameters

```jsx
// App.jsx
<Routes>
 <Route path="/users/:userId" element={<UserProfile />} />
 <Route path="/products/:productId" element={<ProductDetail />} />
</Routes>
```

### useParams Hook

```jsx
import { useParams } from 'react-router-dom';

function UserProfile() {
 const { userId } = useParams();
 const [user, setUser] = useState(null);
 
 useEffect(() => {
 fetch(`/api/users/${userId}`)
 .then(res => res.json())
 .then(data => setUser(data));
 }, [userId]);
 
 if (!user) return <p>Loading...</p>;
 
 return (
 <div>
 <h1>{user.name}</h1>
 <p>{user.email}</p>
 </div>
 );
}
```

### Linking to Dynamic Routes

```jsx
function UserList({ users }) {
 return (
 <ul>
 {users.map(user => (
 <li key={user.id}>
 <Link to={`/users/${user.id}`}>{user.name}</Link>
 </li>
 ))}
 </ul>
 );
}
```

---

## Lesson 5: Nested Routes

### Layout with Outlet

```jsx
// Layout.jsx
import { Outlet, Link } from 'react-router-dom';

function Layout() {
 return (
 <div>
 <header>
 <nav>
 <Link to="/">Home</Link>
 <Link to="/about">About</Link>
 </nav>
 </header>
 
 <main>
 <Outlet /> {/* Child routes render here */}
 </main>
 
 <footer>
 <p>&copy; 2024 My App</p>
 </footer>
 </div>
 );
}
```

### Nested Route Configuration

```jsx
// App.jsx
function App() {
 return (
 <Routes>
 <Route path="/" element={<Layout />}>
 <Route index element={<Home />} />
 <Route path="about" element={<About />} />
 <Route path="contact" element={<Contact />} />
 <Route path="users" element={<Users />}>
 <Route index element={<UserList />} />
 <Route path=":userId" element={<UserProfile />} />
 </Route>
 </Route>
 </Routes>
 );
}
```

---

## Lesson 6: Error and Loading States

### 404 Not Found

```jsx
function App() {
 return (
 <Routes>
 <Route path="/" element={<Layout />}>
 <Route index element={<Home />} />
 <Route path="about" element={<About />} />
 <Route path="*" element={<NotFound />} />
 </Route>
 </Routes>
 );
}

function NotFound() {
 return (
 <div className="not-found">
 <h1>404</h1>
 <p>Page not found</p>
 <Link to="/">Go Home</Link>
 </div>
 );
}
```

### Loading States

```jsx
import { Suspense, lazy } from 'react';

// Lazy load pages
const Home = lazy(() => import('./pages/Home'));
const About = lazy(() => import('./pages/About'));

function App() {
 return (
 <Suspense fallback={<Loading />}>
 <Routes>
 <Route path="/" element={<Home />} />
 <Route path="/about" element={<About />} />
 </Routes>
 </Suspense>
 );
}

function Loading() {
 return <div className="loading">Loading...</div>;
}
```

---

## Lesson 7: Protected Routes

### Auth Check

```jsx
import { Navigate } from 'react-router-dom';

function ProtectedRoute({ children }) {
 const isAuthenticated = checkAuth(); // Your auth logic
 
 if (!isAuthenticated) {
 return <Navigate to="/login" replace />;
 }
 
 return children;
}

// Usage in routes
function App() {
 return (
 <Routes>
 <Route path="/" element={<Home />} />
 <Route path="/login" element={<Login />} />
 <Route 
 path="/dashboard" 
 element={
 <ProtectedRoute>
 <Dashboard />
 </ProtectedRoute>
 } 
 />
 </Routes>
 );
}
```

### Complete Auth Example

```jsx
// AuthContext.jsx
import { createContext, useContext, useState } from 'react';

const AuthContext = createContext();

export function AuthProvider({ children }) {
 const [user, setUser] = useState(null);
 
 const login = (userData) => setUser(userData);
 const logout = () => setUser(null);
 
 return (
 <AuthContext.Provider value={{ user, login, logout }}>
 {children}
 </AuthContext.Provider>
 );
}

export const useAuth = () => useContext(AuthContext);

// ProtectedRoute.jsx
function ProtectedRoute({ children }) {
 const { user } = useAuth();
 
 if (!user) {
 return <Navigate to="/login" replace />;
 }
 
 return children;
}
```

---

## Self-Check Exercises

### Exercise 1: Basic Routes

Create an app with Home, About, and Contact pages with navigation.

### Exercise 2: Dynamic Route

Create a product list with links to individual product detail pages.

### Exercise 3: Nested Layout

Create a dashboard layout with nested routes for different sections.

### Exercise 4: 404 Page

Add a custom 404 page for undefined routes.

### Exercise 5: Protected Route

Create login functionality with a protected dashboard page.

---

## Module Summary

| Component/Hook | Purpose |
|----------------|---------|
| `BrowserRouter` | Enable routing |
| `Routes` | Container for routes |
| `Route` | Define a route |
| `Link` | Navigate between pages |
| `NavLink` | Link with active styling |
| `useNavigate` | Programmatic navigation |
| `useParams` | Access URL parameters |
| `Outlet` | Render nested routes |

---

## Next Steps

**Coming Next**: Module 06 - Project: Task Manager

*You will build a complete React application!*

---

<div align="center">

**Navigation makes apps complete!** 

*Routes connect your pages.*

</div>
