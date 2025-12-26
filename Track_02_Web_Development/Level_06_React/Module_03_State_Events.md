# Module 03: State & Events

## Level 2.6: React Fundamentals

---

## Module Objectives

By the end of this module, you will be able to:

- Understand state vs props
- Use the useState hook
- Handle user events
- Build interactive components

---

## Lesson 1: Understanding State

### Props vs State

```
┌─────────────────────────────────────────────────────────────────────────────┐
│ PROPS vs STATE │
├─────────────────────────────────────────────────────────────────────────────┤
│ │
│ PROPS STATE │
│ ═════ ═════ │
│ │
│ • Passed from parent • Managed internally │
│ • Read-only • Can be changed │
│ • Component doesn't own • Component owns │
│ • Used for configuration • Used for interactivity │
│ │
│ Example: Example: │
│ <Button color="blue"> Button tracks if clicked │
│ (parent decides color) (manages own state) │
│ │
└─────────────────────────────────────────────────────────────────────────────┘
```

### When to Use State

- Form input values
- Toggle switches (on/off)
- Modal open/closed
- Counter values
- Selected items
- Loading states
- Error messages

---

## Lesson 2: useState Hook

### Basic Syntax

```jsx
import { useState } from 'react';

function Counter() {
 // Declare state: [currentValue, setterFunction]
 const [count, setCount] = useState(0);
 // ↑ initial value
 
 return (
 <div>
 <p>Count: {count}</p>
 <button onClick={() => setCount(count + 1)}>
 Increment
 </button>
 </div>
 );
}
```

### How useState Works

```jsx
const [value, setValue] = useState(initialValue);
// ↑ ↑ ↑
// | | └── Starting value
// | └── Function to update value
// └── Current value
```

### Multiple State Variables

```jsx
function UserForm() {
 const [name, setName] = useState("");
 const [email, setEmail] = useState("");
 const [age, setAge] = useState(0);
 const [isSubscribed, setIsSubscribed] = useState(false);
 
 return (
 <form>
 <input 
 value={name}
 onChange={e => setName(e.target.value)}
 placeholder="Name"
 />
 <input 
 value={email}
 onChange={e => setEmail(e.target.value)}
 placeholder="Email"
 />
 {/* ... */}
 </form>
 );
}
```

---

## Lesson 3: Handling Events

### Event Syntax

```jsx
// HTML
<button onclick="handleClick()">

// React (camelCase, function reference)
<button onClick={handleClick}>
```

### Common Events

| Event | When Triggered |
|-------|----------------|
| `onClick` | Element clicked |
| `onChange` | Input value changes |
| `onSubmit` | Form submitted |
| `onFocus` | Element focused |
| `onBlur` | Element loses focus |
| `onMouseEnter` | Mouse enters element |
| `onMouseLeave` | Mouse leaves element |
| `onKeyDown` | Key pressed |

### Event Handler Functions

```jsx
function Button() {
 // Define handler function
 const handleClick = () => {
 console.log("Button clicked!");
 };
 
 return <button onClick={handleClick}>Click Me</button>;
}

// Or inline
function Button() {
 return (
 <button onClick={() => console.log("Clicked!")}>
 Click Me
 </button>
 );
}
```

### Event Object

```jsx
function Input() {
 const handleChange = (event) => {
 console.log(event.target.value);
 };
 
 return <input onChange={handleChange} />;
}
```

---

## Lesson 4: State with Events

### Counter Example

```jsx
import { useState } from 'react';

function Counter() {
 const [count, setCount] = useState(0);
 
 const increment = () => setCount(count + 1);
 const decrement = () => setCount(count - 1);
 const reset = () => setCount(0);
 
 return (
 <div className="counter">
 <h2>Count: {count}</h2>
 <button onClick={decrement}>-</button>
 <button onClick={reset}>Reset</button>
 <button onClick={increment}>+</button>
 </div>
 );
}
```

### Toggle Example

```jsx
function Toggle() {
 const [isOn, setIsOn] = useState(false);
 
 const toggle = () => setIsOn(!isOn);
 
 return (
 <div>
 <p>Status: {isOn ? "ON" : "OFF"}</p>
 <button onClick={toggle}>
 Turn {isOn ? "OFF" : "ON"}
 </button>
 </div>
 );
}
```

### Input Example

```jsx
function NameInput() {
 const [name, setName] = useState("");
 
 return (
 <div>
 <input
 type="text"
 value={name}
 onChange={(e) => setName(e.target.value)}
 placeholder="Enter your name"
 />
 <p>Hello, {name || "stranger"}!</p>
 </div>
 );
}
```

---

## Lesson 5: Forms in React

### Controlled Components

React controls the input value:

```jsx
function LoginForm() {
 const [email, setEmail] = useState("");
 const [password, setPassword] = useState("");
 
 const handleSubmit = (e) => {
 e.preventDefault();
 console.log("Login:", { email, password });
 // Submit to API
 };
 
 return (
 <form onSubmit={handleSubmit}>
 <input
 type="email"
 value={email}
 onChange={(e) => setEmail(e.target.value)}
 placeholder="Email"
 />
 <input
 type="password"
 value={password}
 onChange={(e) => setPassword(e.target.value)}
 placeholder="Password"
 />
 <button type="submit">Login</button>
 </form>
 );
}
```

### Form with Object State

```jsx
function SignupForm() {
 const [formData, setFormData] = useState({
 name: "",
 email: "",
 password: ""
 });
 
 const handleChange = (e) => {
 const { name, value } = e.target;
 setFormData(prev => ({
 ...prev,
 [name]: value
 }));
 };
 
 const handleSubmit = (e) => {
 e.preventDefault();
 console.log(formData);
 };
 
 return (
 <form onSubmit={handleSubmit}>
 <input
 name="name"
 value={formData.name}
 onChange={handleChange}
 placeholder="Name"
 />
 <input
 name="email"
 value={formData.email}
 onChange={handleChange}
 placeholder="Email"
 />
 <input
 name="password"
 type="password"
 value={formData.password}
 onChange={handleChange}
 placeholder="Password"
 />
 <button type="submit">Sign Up</button>
 </form>
 );
}
```

---

## Lesson 6: Updating State Correctly

### State Updates are Asynchronous

```jsx
// Wrong: Reading state immediately after setting
const handleClick = () => {
 setCount(count + 1);
 console.log(count); // Still old value!
};

// Use functional update for derived state
const handleClick = () => {
 setCount(prevCount => prevCount + 1);
};
```

### Functional Updates

Use when new state depends on previous:

```jsx
// Multiple increments
const incrementThree = () => {
 // Wrong: Only increments by 1
 setCount(count + 1);
 setCount(count + 1);
 setCount(count + 1);
 
 // Correct: Increments by 3
 setCount(prev => prev + 1);
 setCount(prev => prev + 1);
 setCount(prev => prev + 1);
};
```

### Updating Objects in State

```jsx
const [user, setUser] = useState({ name: "Sokha", age: 22 });

// Wrong: Mutating state directly
user.age = 23;

// Correct: Create new object
setUser({ ...user, age: 23 });

// Or with functional update
setUser(prev => ({ ...prev, age: prev.age + 1 }));
```

### Updating Arrays in State

```jsx
const [items, setItems] = useState(["Apple", "Banana"]);

// Add item
setItems([...items, "Orange"]);

// Remove item
setItems(items.filter(item => item !== "Banana"));

// Update item
setItems(items.map(item => 
 item === "Apple" ? "Red Apple" : item
));
```

---

## Lesson 7: Practical Examples

### Todo Item

```jsx
function TodoItem({ todo, onToggle, onDelete }) {
 return (
 <div className={`todo ${todo.completed ? 'completed' : ''}`}>
 <input
 type="checkbox"
 checked={todo.completed}
 onChange={() => onToggle(todo.id)}
 />
 <span>{todo.text}</span>
 <button onClick={() => onDelete(todo.id)}>Delete</button>
 </div>
 );
}

function TodoList() {
 const [todos, setTodos] = useState([
 { id: 1, text: "Learn React", completed: false },
 { id: 2, text: "Build project", completed: false }
 ]);
 const [newTodo, setNewTodo] = useState("");
 
 const addTodo = (e) => {
 e.preventDefault();
 if (!newTodo.trim()) return;
 
 setTodos([
 ...todos,
 { id: Date.now(), text: newTodo, completed: false }
 ]);
 setNewTodo("");
 };
 
 const toggleTodo = (id) => {
 setTodos(todos.map(todo =>
 todo.id === id ? { ...todo, completed: !todo.completed } : todo
 ));
 };
 
 const deleteTodo = (id) => {
 setTodos(todos.filter(todo => todo.id !== id));
 };
 
 return (
 <div>
 <form onSubmit={addTodo}>
 <input
 value={newTodo}
 onChange={(e) => setNewTodo(e.target.value)}
 placeholder="New todo..."
 />
 <button type="submit">Add</button>
 </form>
 
 {todos.map(todo => (
 <TodoItem
 key={todo.id}
 todo={todo}
 onToggle={toggleTodo}
 onDelete={deleteTodo}
 />
 ))}
 </div>
 );
}
```

---

## Self-Check Exercises

### Exercise 1: Counter

Create a counter with increment, decrement, and reset buttons.

### Exercise 2: Toggle Theme

Create a dark/light mode toggle.

### Exercise 3: Character Counter

Create an input that shows remaining characters (max 100).

### Exercise 4: Login Form

Create a login form with email and password validation.

### Exercise 5: Shopping Cart

Create a simple list where you can add/remove items.

---

## Module Summary

| Concept | Description |
|---------|-------------|
| State | Component's internal data |
| useState | Hook to add state |
| Events | Handle user interactions |
| Controlled inputs | React controls form values |
| Functional updates | Update based on previous state |

---

## Next Steps

**Coming Next**: Module 04 - Hooks (useEffect)

*You will learn to handle side effects!*

---

<div align="center">

**State makes React interactive!** 

*User actions → State changes → UI updates*

</div>
