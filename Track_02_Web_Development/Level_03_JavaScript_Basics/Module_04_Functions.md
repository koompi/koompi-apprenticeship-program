# Module 04: Functions

## Level 2.3: JavaScript Basics

---

## Module Objectives

By the end of this module, you will be able to:

- Create and call functions
- Use parameters and return values
- Understand function scope
- Use arrow functions

---

## Lesson 1: What Are Functions?

### Functions Are Reusable Code

```
┌─────────────────────────────────────────────────────────────────────────────┐
│ WHY FUNCTIONS? │
├─────────────────────────────────────────────────────────────────────────────┤
│ │
│ WITHOUT FUNCTIONS: WITH FUNCTIONS: │
│ │
│ console.log("Hello, Sokha"); function greet(name) { │
│ console.log("Hello, Dara"); console.log("Hello, " + name); │
│ console.log("Hello, Bopha"); } │
│ console.log("Hello, Vanna"); │
│ // ... repeat for every person greet("Sokha"); │
│ greet("Dara"); │
│ greet("Bopha"); │
│ greet("Vanna"); │
│ // Reuse for anyone! │
│ │
│ Functions let you write once and use many times. │
│ │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## Lesson 2: Creating Functions

### Function Declaration

```javascript
function sayHello() {
 console.log("Hello!");
}

// Call the function
sayHello(); // Output: Hello!
sayHello(); // Output: Hello!
```

### Function with Parameters

```javascript
function greet(name) {
 console.log("Hello, " + name + "!");
}

greet("Sokha"); // Hello, Sokha!
greet("Dara"); // Hello, Dara!
```

### Multiple Parameters

```javascript
function introduce(name, age, job) {
 console.log(`My name is ${name}, I'm ${age}, and I work as a ${job}.`);
}

introduce("Sokha", 22, "developer");
// My name is Sokha, I'm 22, and I work as a developer.
```

### Default Parameters

```javascript
function greet(name = "Friend") {
 console.log(`Hello, ${name}!`);
}

greet("Sokha"); // Hello, Sokha!
greet(); // Hello, Friend!
```

---

## Lesson 3: Return Values

### The Return Statement

Functions can send a value back:

```javascript
function add(a, b) {
 return a + b;
}

let result = add(5, 3);
console.log(result); // 8

// Use directly
console.log(add(10, 20)); // 30
```

### Return Stops Execution

```javascript
function checkAge(age) {
 if (age < 18) {
 return "Too young";
 }
 return "Welcome!";
 console.log("This never runs"); // Unreachable
}

console.log(checkAge(15)); // Too young
console.log(checkAge(25)); // Welcome!
```

### Returning Different Types

```javascript
// Return a number
function calculateArea(width, height) {
 return width * height;
}

// Return a string
function getFullName(first, last) {
 return first + " " + last;
}

// Return a boolean
function isAdult(age) {
 return age >= 18;
}

// Return an object
function createUser(name, age) {
 return {
 name: name,
 age: age,
 isAdult: age >= 18
 };
}
```

---

## Lesson 4: Scope

### What is Scope?

Scope determines where variables are accessible.

```javascript
let globalVar = "I'm global";

function myFunction() {
 let localVar = "I'm local";
 
 console.log(globalVar); // Can access global
 console.log(localVar); // Can access local
}

myFunction();
console.log(globalVar); // Can access global
console.log(localVar); // Error! localVar not defined
```

### Block Scope

Variables declared with `let` and `const` are block-scoped:

```javascript
if (true) {
 let blockVar = "I'm in a block";
 console.log(blockVar); // Works here
}
console.log(blockVar); // Error! Not accessible outside

// var leaks out of blocks (avoid!)
if (true) {
 var leakyVar = "I leak!";
}
console.log(leakyVar); // "I leak!" - This actually works
```

---

## Lesson 5: Arrow Functions

### Arrow Function Syntax

A shorter way to write functions:

```javascript
// Traditional function
function add(a, b) {
 return a + b;
}

// Arrow function
const add = (a, b) => {
 return a + b;
};

// Even shorter (implicit return)
const add = (a, b) => a + b;
```

### Arrow Function Examples

```javascript
// No parameters
const sayHello = () => console.log("Hello!");

// One parameter (parentheses optional)
const double = x => x * 2;
const double = (x) => x * 2; // Also valid

// Multiple parameters
const add = (a, b) => a + b;

// With function body
const greet = (name) => {
 let message = `Hello, ${name}!`;
 console.log(message);
 return message;
};
```

### When to Use Arrow Functions

| Use Arrow Functions | Use Regular Functions |
|---------------------|----------------------|
| Short operations | Methods in objects |
| Array methods | Constructors |
| Callbacks | When you need `this` context |

---

## Lesson 6: Function Expressions

### Storing Functions in Variables

```javascript
// Function declaration
function greet1(name) {
 return `Hello, ${name}!`;
}

// Function expression
const greet2 = function(name) {
 return `Hello, ${name}!`;
};

// Arrow function expression
const greet3 = (name) => `Hello, ${name}!`;

// All work the same way
console.log(greet1("Sokha"));
console.log(greet2("Sokha"));
console.log(greet3("Sokha"));
```

### Passing Functions as Arguments

```javascript
function doOperation(a, b, operation) {
 return operation(a, b);
}

const add = (x, y) => x + y;
const subtract = (x, y) => x - y;
const multiply = (x, y) => x * y;

console.log(doOperation(10, 5, add)); // 15
console.log(doOperation(10, 5, subtract)); // 5
console.log(doOperation(10, 5, multiply)); // 50
```

---

## Lesson 7: Practical Function Examples

### Calculator Functions

```javascript
const add = (a, b) => a + b;
const subtract = (a, b) => a - b;
const multiply = (a, b) => a * b;
const divide = (a, b) => b !== 0 ? a / b : "Cannot divide by zero";

function calculate(num1, num2, operation) {
 switch(operation) {
 case '+': return add(num1, num2);
 case '-': return subtract(num1, num2);
 case '*': return multiply(num1, num2);
 case '/': return divide(num1, num2);
 default: return "Invalid operation";
 }
}

console.log(calculate(10, 5, '+')); // 15
console.log(calculate(10, 5, '/')); // 2
```

### Validation Functions

```javascript
function isValidEmail(email) {
 return email.includes('@') && email.includes('.');
}

function isValidPassword(password) {
 return password.length >= 8;
}

function validateUser(email, password) {
 if (!isValidEmail(email)) {
 return "Invalid email format";
 }
 if (!isValidPassword(password)) {
 return "Password must be at least 8 characters";
 }
 return "Valid!";
}

console.log(validateUser("test@email.com", "12345678")); // Valid!
console.log(validateUser("testemail", "12345678")); // Invalid email
```

### Greeting Function

```javascript
function getGreeting() {
 const hour = new Date().getHours();
 
 if (hour < 12) {
 return "Good morning";
 } else if (hour < 18) {
 return "Good afternoon";
 } else {
 return "Good evening";
 }
}

function personalizeGreeting(name) {
 return `${getGreeting()}, ${name}!`;
}

console.log(personalizeGreeting("Sokha"));
// Output depends on time of day
```

---

## Self-Check Exercises

### Exercise 1: Basic Function

Create a function that:

- Takes a person's name
- Returns "Hello, [name]!"
- Call it with 3 different names

### Exercise 2: Calculator

Create functions for add, subtract, multiply, divide. Each takes two numbers and returns the result.

### Exercise 3: Temperature Converter

Create two functions:

- `celsiusToFahrenheit(celsius)` — returns fahrenheit
- `fahrenheitToCelsius(fahrenheit)` — returns celsius

Formula: F = (C × 9/5) + 32

### Exercise 4: Grade Function

Create a function that:

- Takes a score (0-100)
- Returns the grade (A, B, C, D, F)

### Exercise 5: Password Generator

Create a function that generates a random password:

- Takes a length parameter (default 8)
- Returns a random string of that length
- Use letters and numbers

---

## Module Summary

**Function Types**

| Type | Syntax |
|------|--------|
| Declaration | `function name() {}` |
| Expression | `const name = function() {}` |
| Arrow | `const name = () => {}` |

**Key Concepts**

| Concept | Description |
|---------|-------------|
| Parameters | Inputs to the function |
| Return | Output from the function |
| Scope | Where variables are accessible |
| Default values | Fallback for missing parameters |

---

## Next Steps

**Before moving to Module 05:**

- [ ] Create functions with parameters
- [ ] Use return statements
- [ ] Understand scope
- [ ] Practice arrow functions
- [ ] Get mentor verification

**Coming Next**: Module 05 - Arrays & Loops

*You will learn to work with collections of data!*

---

<div align="center">

**Functions are your building blocks!** 

*Good functions make good code.*

</div>
