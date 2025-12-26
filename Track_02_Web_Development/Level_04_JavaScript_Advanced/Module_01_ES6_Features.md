# Module 01: ES6+ Modern Features

## Level 2.4: JavaScript Advanced

---

## 🎯 Module Objectives

By the end of this module, you will be able to:

- Use destructuring for objects and arrays
- Apply spread and rest operators
- Work with template literals effectively
- Understand JavaScript modules (import/export)

---

## Lesson 1: Destructuring

### Object Destructuring

Extract values from objects into variables:

```javascript
// Without destructuring
const user = { name: "Sokha", age: 22, city: "Phnom Penh" };
const name = user.name;
const age = user.age;

// With destructuring
const { name, age, city } = user;
console.log(name);  // "Sokha"
console.log(age);   // 22
```

### Renaming Variables

```javascript
const user = { name: "Sokha", age: 22 };

// Rename while destructuring
const { name: userName, age: userAge } = user;
console.log(userName);  // "Sokha"
console.log(userAge);   // 22
```

### Default Values

```javascript
const user = { name: "Sokha" };

const { name, age = 18 } = user;
console.log(age);  // 18 (default value used)
```

### Nested Destructuring

```javascript
const user = {
    name: "Sokha",
    address: {
        city: "Phnom Penh",
        country: "Cambodia"
    }
};

const { name, address: { city, country } } = user;
console.log(city);  // "Phnom Penh"
```

### Array Destructuring

```javascript
const colors = ["red", "green", "blue"];

const [first, second, third] = colors;
console.log(first);   // "red"
console.log(second);  // "green"

// Skip elements
const [primary, , tertiary] = colors;
console.log(tertiary);  // "blue"

// Swap variables
let a = 1, b = 2;
[a, b] = [b, a];
console.log(a, b);  // 2, 1
```

---

## Lesson 2: Spread Operator (...)

### Spread Arrays

```javascript
const arr1 = [1, 2, 3];
const arr2 = [4, 5, 6];

// Combine arrays
const combined = [...arr1, ...arr2];
console.log(combined);  // [1, 2, 3, 4, 5, 6]

// Copy array
const copy = [...arr1];
copy.push(4);
console.log(arr1);  // [1, 2, 3] - original unchanged
console.log(copy);  // [1, 2, 3, 4]

// Add elements
const withNew = [0, ...arr1, 4];
console.log(withNew);  // [0, 1, 2, 3, 4]
```

### Spread Objects

```javascript
const user = { name: "Sokha", age: 22 };

// Copy object
const userCopy = { ...user };

// Merge objects
const details = { city: "Phnom Penh", job: "Developer" };
const fullUser = { ...user, ...details };
console.log(fullUser);
// { name: "Sokha", age: 22, city: "Phnom Penh", job: "Developer" }

// Override properties
const updated = { ...user, age: 23 };
console.log(updated);  // { name: "Sokha", age: 23 }
```

### Spread in Function Calls

```javascript
const numbers = [5, 2, 8, 1, 9];

// Instead of Math.max(5, 2, 8, 1, 9)
const max = Math.max(...numbers);
console.log(max);  // 9
```

---

## Lesson 3: Rest Operator (...)

### Rest in Functions

Collect remaining arguments:

```javascript
function sum(...numbers) {
    return numbers.reduce((total, n) => total + n, 0);
}

console.log(sum(1, 2, 3));       // 6
console.log(sum(1, 2, 3, 4, 5)); // 15
```

### Rest with Destructuring

```javascript
const [first, second, ...rest] = [1, 2, 3, 4, 5];
console.log(first);  // 1
console.log(second); // 2
console.log(rest);   // [3, 4, 5]

const { name, ...otherProps } = { name: "Sokha", age: 22, city: "PP" };
console.log(name);        // "Sokha"
console.log(otherProps);  // { age: 22, city: "PP" }
```

---

## Lesson 4: Enhanced Object Literals

### Shorthand Properties

```javascript
const name = "Sokha";
const age = 22;

// Old way
const user1 = { name: name, age: age };

// Shorthand
const user2 = { name, age };
console.log(user2);  // { name: "Sokha", age: 22 }
```

### Shorthand Methods

```javascript
// Old way
const obj1 = {
    sayHello: function() {
        console.log("Hello!");
    }
};

// Shorthand
const obj2 = {
    sayHello() {
        console.log("Hello!");
    }
};
```

### Computed Property Names

```javascript
const key = "dynamicKey";

const obj = {
    [key]: "value",
    ["item" + 1]: "first",
    ["item" + 2]: "second"
};

console.log(obj.dynamicKey);  // "value"
console.log(obj.item1);       // "first"
```

---

## Lesson 5: Template Literals Advanced

### Multi-line Strings

```javascript
const html = `
    <div class="card">
        <h2>Title</h2>
        <p>Content goes here</p>
    </div>
`;
```

### Expression Interpolation

```javascript
const price = 100;
const tax = 0.1;

const message = `
    Price: $${price}
    Tax: $${price * tax}
    Total: $${price * (1 + tax)}
`;
```

### Tagged Templates

```javascript
function highlight(strings, ...values) {
    return strings.reduce((result, str, i) => {
        return result + str + (values[i] ? `<mark>${values[i]}</mark>` : '');
    }, '');
}

const name = "Sokha";
const role = "Developer";

const result = highlight`Welcome ${name}, you are a ${role}!`;
// "Welcome <mark>Sokha</mark>, you are a <mark>Developer</mark>!"
```

---

## Lesson 6: Optional Chaining & Nullish Coalescing

### Optional Chaining (?.)

Safely access nested properties:

```javascript
const user = {
    name: "Sokha",
    address: {
        city: "Phnom Penh"
    }
};

// Without optional chaining
const country1 = user.address && user.address.country;

// With optional chaining
const country2 = user.address?.country;
console.log(country2);  // undefined (no error!)

// Works with methods too
const user2 = {};
user2.getName?.();  // undefined, no error

// Array access
const arr = null;
arr?.[0];  // undefined, no error
```

### Nullish Coalescing (??)

Default value only for null/undefined (not for 0 or ""):

```javascript
const count = 0;

// || treats 0 as falsy
console.log(count || 10);  // 10 (wrong!)

// ?? only checks null/undefined
console.log(count ?? 10);  // 0 (correct!)

const name = "";
console.log(name || "Anonymous");  // "Anonymous"
console.log(name ?? "Anonymous");  // "" (empty string is valid)
```

---

## Lesson 7: Modules (Import/Export)

### Named Exports

```javascript
// utils.js
export const PI = 3.14159;

export function add(a, b) {
    return a + b;
}

export function subtract(a, b) {
    return a - b;
}
```

```javascript
// main.js
import { PI, add, subtract } from './utils.js';

console.log(PI);        // 3.14159
console.log(add(2, 3)); // 5
```

### Default Export

```javascript
// Calculator.js
export default class Calculator {
    add(a, b) { return a + b; }
    subtract(a, b) { return a - b; }
}
```

```javascript
// main.js
import Calculator from './Calculator.js';

const calc = new Calculator();
console.log(calc.add(5, 3));  // 8
```

### Mixed Exports

```javascript
// api.js
export const API_URL = "https://api.example.com";

export function fetchData() { /* ... */ }

export default class ApiClient { /* ... */ }
```

```javascript
// main.js
import ApiClient, { API_URL, fetchData } from './api.js';
```

### Renaming Imports

```javascript
import { add as addNumbers, subtract as subtractNumbers } from './utils.js';
```

---

## 🧪 Self-Check Exercises

### Exercise 1: Destructuring Practice

```javascript
const product = {
    id: 1,
    name: "KOOMPI E13",
    price: 299,
    specs: {
        ram: "8GB",
        storage: "256GB"
    }
};

// Destructure: name, price, and ram from specs
```

### Exercise 2: Spread Operations

```javascript
const arr1 = [1, 2, 3];
const arr2 = [4, 5, 6];

// Create new array: [0, 1, 2, 3, 4, 5, 6, 7]
```

### Exercise 3: Rest Parameters

Create a function `average(...numbers)` that calculates the average of any number of arguments.

### Exercise 4: Optional Chaining

Safely access deeply nested data without errors.

### Exercise 5: Modules

Create two files:

- `math.js` with exported functions
- `app.js` that imports and uses them

---

## 📝 Module Summary

| Feature | Syntax | Use Case |
|---------|--------|----------|
| Destructuring | `const { a, b } = obj` | Extract values |
| Spread | `[...arr]` | Copy/combine |
| Rest | `(...args)` | Collect arguments |
| Optional Chaining | `obj?.prop` | Safe access |
| Nullish Coalescing | `a ?? b` | Default for null |
| Modules | `import/export` | Code organization |

---

## 🎯 Next Steps

**Coming Next**: Module 02 - Asynchronous JavaScript

*You will learn Promises, async/await, and handling asynchronous operations!*

---

<div align="center">

**Modern JavaScript is powerful!** ⚡

*These features make your code cleaner and safer.*

</div>
