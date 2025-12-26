# Module 04: React Hooks

## Level 2.6: React Fundamentals

---

## Module Objectives

By the end of this module, you will be able to:

- Use useEffect for side effects
- Understand the useEffect lifecycle
- Create custom hooks
- Use other common hooks

---

## Lesson 1: What are Side Effects?

### Side Effects Explained

```
┌─────────────────────────────────────────────────────────────────────────────┐
│ SIDE EFFECTS │
├─────────────────────────────────────────────────────────────────────────────┤
│ │
│ Anything that affects something outside the component: │
│ │
│ • Fetching data from an API │
│ • Updating the document title │
│ • Setting up subscriptions │
│ • Manually changing the DOM │
│ • Setting timers │
│ • Logging │
│ • Saving to localStorage │
│ │
│ These are NOT pure rendering → they need useEffect │
│ │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## Lesson 2: useEffect Basics

### Basic Syntax

```jsx
import { useEffect } from 'react';

function Component() {
 useEffect(() => {
 // Side effect code here
 console.log("Effect ran!");
 });
 
 return <div>Hello</div>;
}
```

### The Dependency Array

```jsx
// Runs after EVERY render
useEffect(() => {
 console.log("Every render");
});

// Runs only ONCE (on mount)
useEffect(() => {
 console.log("Only once");
}, []); // Empty array

// Runs when 'count' changes
useEffect(() => {
 console.log("Count changed:", count);
}, [count]);

// Runs when 'name' OR 'age' changes
useEffect(() => {
 console.log("Name or age changed");
}, [name, age]);
```

---

## Lesson 3: Common useEffect Patterns

### Document Title

```jsx
function PageTitle({ title }) {
 useEffect(() => {
 document.title = title;
 }, [title]);
 
 return <h1>{title}</h1>;
}
```

### Fetching Data

```jsx
function UserProfile({ userId }) {
 const [user, setUser] = useState(null);
 const [loading, setLoading] = useState(true);
 const [error, setError] = useState(null);
 
 useEffect(() => {
 const fetchUser = async () => {
 try {
 setLoading(true);
 const response = await fetch(`/api/users/${userId}`);
 const data = await response.json();
 setUser(data);
 } catch (err) {
 setError(err.message);
 } finally {
 setLoading(false);
 }
 };
 
 fetchUser();
 }, [userId]); // Re-fetch when userId changes
 
 if (loading) return <p>Loading...</p>;
 if (error) return <p>Error: {error}</p>;
 if (!user) return null;
 
 return (
 <div>
 <h2>{user.name}</h2>
 <p>{user.email}</p>
 </div>
 );
}
```

### localStorage Sync

```jsx
function ThemeToggle() {
 const [isDark, setIsDark] = useState(() => {
 // Initialize from localStorage
 const saved = localStorage.getItem('darkMode');
 return saved ? JSON.parse(saved) : false;
 });
 
 useEffect(() => {
 // Save to localStorage when changed
 localStorage.setItem('darkMode', JSON.stringify(isDark));
 
 // Apply to document
 document.body.classList.toggle('dark-mode', isDark);
 }, [isDark]);
 
 return (
 <button onClick={() => setIsDark(!isDark)}>
 {isDark ? ' Light' : ' Dark'}
 </button>
 );
}
```

---

## Lesson 4: Cleanup Function

### Why Cleanup?

Prevent memory leaks and stale operations:

```jsx
useEffect(() => {
 // Setup
 const subscription = subscribeToData();
 
 // Cleanup function (runs before next effect or unmount)
 return () => {
 subscription.unsubscribe();
 };
}, []);
```

### Timer Cleanup

```jsx
function Timer() {
 const [seconds, setSeconds] = useState(0);
 
 useEffect(() => {
 const interval = setInterval(() => {
 setSeconds(prev => prev + 1);
 }, 1000);
 
 // Cleanup: clear interval when component unmounts
 return () => clearInterval(interval);
 }, []);
 
 return <p>Time: {seconds}s</p>;
}
```

### Event Listener Cleanup

```jsx
function WindowSize() {
 const [size, setSize] = useState({
 width: window.innerWidth,
 height: window.innerHeight
 });
 
 useEffect(() => {
 const handleResize = () => {
 setSize({
 width: window.innerWidth,
 height: window.innerHeight
 });
 };
 
 window.addEventListener('resize', handleResize);
 
 // Cleanup
 return () => window.removeEventListener('resize', handleResize);
 }, []);
 
 return <p>Window: {size.width} x {size.height}</p>;
}
```

---

## Lesson 5: Other Hooks

### useRef

Reference to DOM elements or mutable values:

```jsx
import { useRef } from 'react';

function TextInput() {
 const inputRef = useRef(null);
 
 const focusInput = () => {
 inputRef.current.focus();
 };
 
 return (
 <div>
 <input ref={inputRef} type="text" />
 <button onClick={focusInput}>Focus Input</button>
 </div>
 );
}
```

### useRef for Persistent Values

```jsx
function Counter() {
 const [count, setCount] = useState(0);
 const renderCount = useRef(0);
 
 useEffect(() => {
 renderCount.current += 1;
 });
 
 return (
 <div>
 <p>Count: {count}</p>
 <p>Renders: {renderCount.current}</p>
 <button onClick={() => setCount(count + 1)}>+</button>
 </div>
 );
}
```

### useMemo

Memoize expensive calculations:

```jsx
import { useMemo } from 'react';

function ExpensiveList({ items, filter }) {
 const filteredItems = useMemo(() => {
 console.log("Filtering...");
 return items.filter(item => item.includes(filter));
 }, [items, filter]);
 
 return (
 <ul>
 {filteredItems.map(item => <li key={item}>{item}</li>)}
 </ul>
 );
}
```

### useCallback

Memoize functions:

```jsx
import { useCallback } from 'react';

function Parent() {
 const [count, setCount] = useState(0);
 
 const handleClick = useCallback(() => {
 console.log("Clicked!");
 }, []); // Function identity stays stable
 
 return (
 <div>
 <Child onClick={handleClick} />
 <button onClick={() => setCount(count + 1)}>
 Count: {count}
 </button>
 </div>
 );
}
```

---

## Lesson 6: Custom Hooks

### Creating Custom Hooks

Extract reusable logic:

```jsx
// useLocalStorage.js
function useLocalStorage(key, initialValue) {
 const [value, setValue] = useState(() => {
 const saved = localStorage.getItem(key);
 return saved ? JSON.parse(saved) : initialValue;
 });
 
 useEffect(() => {
 localStorage.setItem(key, JSON.stringify(value));
 }, [key, value]);
 
 return [value, setValue];
}

// Usage
function App() {
 const [name, setName] = useLocalStorage('name', '');
 
 return (
 <input
 value={name}
 onChange={e => setName(e.target.value)}
 />
 );
}
```

### useFetch Hook

```jsx
function useFetch(url) {
 const [data, setData] = useState(null);
 const [loading, setLoading] = useState(true);
 const [error, setError] = useState(null);
 
 useEffect(() => {
 const fetchData = async () => {
 try {
 setLoading(true);
 const response = await fetch(url);
 if (!response.ok) throw new Error('Failed');
 const json = await response.json();
 setData(json);
 } catch (err) {
 setError(err.message);
 } finally {
 setLoading(false);
 }
 };
 
 fetchData();
 }, [url]);
 
 return { data, loading, error };
}

// Usage
function UserList() {
 const { data: users, loading, error } = useFetch('/api/users');
 
 if (loading) return <p>Loading...</p>;
 if (error) return <p>Error: {error}</p>;
 
 return (
 <ul>
 {users.map(user => <li key={user.id}>{user.name}</li>)}
 </ul>
 );
}
```

### useToggle Hook

```jsx
function useToggle(initialValue = false) {
 const [value, setValue] = useState(initialValue);
 
 const toggle = useCallback(() => {
 setValue(v => !v);
 }, []);
 
 return [value, toggle];
}

// Usage
function Modal() {
 const [isOpen, toggleOpen] = useToggle();
 
 return (
 <div>
 <button onClick={toggleOpen}>Open Modal</button>
 {isOpen && (
 <div className="modal">
 <p>Modal content</p>
 <button onClick={toggleOpen}>Close</button>
 </div>
 )}
 </div>
 );
}
```

---

## Lesson 7: Rules of Hooks

### The Rules

```jsx
// Rule 1: Only call hooks at the top level
function Component() {
 const [count, setCount] = useState(0); // Top level
 
 // Wrong: Inside condition
 if (count > 0) {
 const [name, setName] = useState(""); // 
 }
 
 // Wrong: Inside loop
 for (let i = 0; i < 3; i++) {
 useEffect(() => {}); // 
 }
}

// Rule 2: Only call hooks in React functions
function MyComponent() {
 useState(); // React component
}

function useMyHook() {
 useState(); // Custom hook (starts with "use")
}

function regularFunction() {
 useState(); // Regular function
}
```

---

## Self-Check Exercises

### Exercise 1: Document Title

Create a component that updates the page title based on a prop.

### Exercise 2: Fetch Data

Create a component that fetches and displays user data.

### Exercise 3: Timer

Create a stopwatch with start, stop, and reset.

### Exercise 4: Custom Hook

Create a `useWindowSize` hook that returns window dimensions.

### Exercise 5: Debounce

Create a search input that debounces API calls.

---

## Module Summary

| Hook | Purpose |
|------|---------|
| `useEffect` | Handle side effects |
| `useRef` | DOM refs & mutable values |
| `useMemo` | Memoize values |
| `useCallback` | Memoize functions |
| Custom hooks | Reusable logic |

**useEffect Patterns:**

```jsx
useEffect(() => {}, []); // Run once
useEffect(() => {}, [dep]); // Run on dep change
useEffect(() => { return cleanup; }, []); // With cleanup
```

---

## Next Steps

**Coming Next**: Module 05 - React Router

*You will learn to add navigation to your app!*

---

<div align="center">

**Hooks power modern React!** 

*Side effects under control.*

</div>
