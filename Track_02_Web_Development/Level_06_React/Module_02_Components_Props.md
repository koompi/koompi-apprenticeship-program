# Module 02: Components & Props

## Level 2.6: React Fundamentals

---

## Module Objectives

By the end of this module, you will be able to:

- Understand the component hierarchy
- Pass data with props
- Use destructuring for props
- Create reusable components

---

## Lesson 1: Understanding Props

### What Are Props?

Props = Properties. Data passed from parent to child component.

```jsx
// Parent passes data
<Greeting name="Sokha" age={22} />

// Child receives data
function Greeting(props) {
 return <h1>Hello, {props.name}! You are {props.age}.</h1>;
}
```

### Props Flow

```
┌─────────────────────────────────────────────────────────────────────────────┐
│ DATA FLOW IN REACT │
├─────────────────────────────────────────────────────────────────────────────┤
│ │
│ App (Parent) │
│ name="Sokha" age={22} │
│ │ │
│ │ props │
│ ▼ │
│ Greeting (Child) │
│ props.name, props.age │
│ │
│ Data flows DOWN (parent → child) │
│ Never UP (child cannot modify parent props) │
│ │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## Lesson 2: Using Props

### Passing Different Types

```jsx
function App() {
 return (
 <UserCard
 name="Sokha" // String
 age={22} // Number
 isStudent={true} // Boolean
 skills={["React", "CSS"]} // Array
 address={{ city: "PP" }} // Object
 onClick={handleClick} // Function
 />
 );
}
```

### Receiving Props

```jsx
// Method 1: props object
function UserCard(props) {
 return (
 <div>
 <h2>{props.name}</h2>
 <p>Age: {props.age}</p>
 <p>Student: {props.isStudent ? "Yes" : "No"}</p>
 </div>
 );
}

// Method 2: Destructuring (preferred)
function UserCard({ name, age, isStudent }) {
 return (
 <div>
 <h2>{name}</h2>
 <p>Age: {age}</p>
 <p>Student: {isStudent ? "Yes" : "No"}</p>
 </div>
 );
}
```

---

## Lesson 3: Default Props

### Setting Defaults

```jsx
// Method 1: Default parameters
function Button({ text = "Click me", color = "blue" }) {
 return (
 <button style={{ backgroundColor: color }}>
 {text}
 </button>
 );
}

// Usage
<Button /> // Uses defaults
<Button text="Submit" /> // Custom text, default color
<Button text="Delete" color="red" /> // Custom both
```

### With Object Destructuring

```jsx
function Card({ 
 title = "Untitled",
 description = "No description",
 imageUrl = "/placeholder.jpg"
}) {
 return (
 <div className="card">
 <img src={imageUrl} alt={title} />
 <h3>{title}</h3>
 <p>{description}</p>
 </div>
 );
}
```

---

## Lesson 4: The Children Prop

### What is children?

Content between component tags:

```jsx
// Parent
<Card>
 <h2>Title</h2>
 <p>This content is passed as children</p>
</Card>

// Card component
function Card({ children }) {
 return (
 <div className="card">
 {children}
 </div>
 );
}
```

### Flexible Layouts

```jsx
function Container({ children, className }) {
 return (
 <div className={`container ${className}`}>
 {children}
 </div>
 );
}

// Usage
<Container className="main-content">
 <Header />
 <ArticleList />
 <Footer />
</Container>
```

### Button Example

```jsx
function Button({ children, onClick, variant = "primary" }) {
 return (
 <button className={`btn btn-${variant}`} onClick={onClick}>
 {children}
 </button>
 );
}

// Usage
<Button onClick={handleSave}>
 Save
</Button>

<Button variant="danger" onClick={handleDelete}>
 Delete
</Button>
```

---

## Lesson 5: Component Composition

### Building from Small Parts

```jsx
// Small, focused components
function Avatar({ src, alt }) {
 return <img className="avatar" src={src} alt={alt} />;
}

function UserInfo({ name, role }) {
 return (
 <div className="user-info">
 <h4>{name}</h4>
 <p>{role}</p>
 </div>
 );
}

// Composed component
function UserCard({ user }) {
 return (
 <div className="user-card">
 <Avatar src={user.avatar} alt={user.name} />
 <UserInfo name={user.name} role={user.role} />
 </div>
 );
}

// Usage
<UserCard user={{
 name: "Sokha",
 role: "Developer",
 avatar: "/sokha.jpg"
}} />
```

### Card System

```jsx
function Card({ children }) {
 return <div className="card">{children}</div>;
}

function CardHeader({ children }) {
 return <div className="card-header">{children}</div>;
}

function CardBody({ children }) {
 return <div className="card-body">{children}</div>;
}

function CardFooter({ children }) {
 return <div className="card-footer">{children}</div>;
}

// Usage
<Card>
 <CardHeader>
 <h3>Product Title</h3>
 </CardHeader>
 <CardBody>
 <p>Product description goes here.</p>
 </CardBody>
 <CardFooter>
 <Button>Buy Now</Button>
 </CardFooter>
</Card>
```

---

## Lesson 6: Props Best Practices

### Keep Props Simple

```jsx
// Too many props
<UserCard
 firstName="Sokha"
 lastName="Meas"
 email="sokha@email.com"
 phone="012345678"
 street="123 Main St"
 city="Phnom Penh"
 country="Cambodia"
/>

// Pass an object
<UserCard user={userData} />

function UserCard({ user }) {
 return (
 <div>
 <h2>{user.firstName} {user.lastName}</h2>
 <p>{user.email}</p>
 <p>{user.city}, {user.country}</p>
 </div>
 );
}
```

### Destructure Early

```jsx
// Clean and clear
function ProductCard({ product }) {
 const { name, price, description, imageUrl } = product;
 
 return (
 <div className="product-card">
 <img src={imageUrl} alt={name} />
 <h3>{name}</h3>
 <p>{description}</p>
 <span className="price">${price}</span>
 </div>
 );
}
```

### Spread Props When Needed

```jsx
// Pass all props to child
function Button({ children, ...rest }) {
 return (
 <button className="btn" {...rest}>
 {children}
 </button>
 );
}

// All these work:
<Button onClick={fn}>Click</Button>
<Button disabled>Can't Click</Button>
<Button type="submit">Submit</Button>
```

---

## Lesson 7: Practical Examples

### Product List

```jsx
// Data
const products = [
 { id: 1, name: "Laptop", price: 299, image: "/laptop.jpg" },
 { id: 2, name: "Mouse", price: 25, image: "/mouse.jpg" },
 { id: 3, name: "Keyboard", price: 45, image: "/keyboard.jpg" },
];

// ProductCard component
function ProductCard({ product }) {
 const { name, price, image } = product;
 
 return (
 <div className="product-card">
 <img src={image} alt={name} />
 <h3>{name}</h3>
 <p className="price">${price}</p>
 <button>Add to Cart</button>
 </div>
 );
}

// ProductList component
function ProductList({ products }) {
 return (
 <div className="product-grid">
 {products.map(product => (
 <ProductCard key={product.id} product={product} />
 ))}
 </div>
 );
}

// App
function App() {
 return (
 <div>
 <h1>Our Products</h1>
 <ProductList products={products} />
 </div>
 );
}
```

### Navigation

```jsx
function NavLink({ to, children, isActive = false }) {
 return (
 <a 
 href={to} 
 className={`nav-link ${isActive ? 'active' : ''}`}
 >
 {children}
 </a>
 );
}

function Navigation({ links, currentPath }) {
 return (
 <nav>
 {links.map(link => (
 <NavLink 
 key={link.to}
 to={link.to}
 isActive={currentPath === link.to}
 >
 {link.label}
 </NavLink>
 ))}
 </nav>
 );
}
```

---

## Self-Check Exercises

### Exercise 1: Greeting Component

Create a `Greeting` component that takes `name` and `timeOfDay` props.

### Exercise 2: Card Component

Create a reusable `Card` component with `title`, `description`, and `children` props.

### Exercise 3: Button Variants

Create a `Button` component with `variant` prop (primary, secondary, danger).

### Exercise 4: User List

Create components to display a list of users with their info.

### Exercise 5: Product Grid

Build a product grid with reusable `ProductCard` components.

---

## Module Summary

| Concept | Description |
|---------|-------------|
| Props | Data passed parent → child |
| Destructuring | Extract props cleanly |
| Default props | Fallback values |
| children | Content between tags |
| Composition | Build from small parts |

---

## Next Steps

**Coming Next**: Module 03 - State & Events

*You will learn to make components interactive!*

---

<div align="center">

**Props power your components!** 

*Data flows down, components stay pure.*

</div>
