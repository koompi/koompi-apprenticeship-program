# Module 02: Variables & Data Types

## Level 2.3: JavaScript Basics

---

## 🎯 Module Objectives

By the end of this module, you will be able to:

- Declare variables using let, const, and var
- Work with different data types
- Perform string operations
- Understand type conversion

---

## Lesson 1: What Are Variables?

### Variables Store Data

Think of variables as labeled boxes that hold information:

```javascript
let name = "Sokha";       // Box labeled "name" contains "Sokha"
let age = 22;             // Box labeled "age" contains 22
let isStudent = true;     // Box labeled "isStudent" contains true
```

### Declaring Variables

```javascript
// Declaration with value
let score = 100;

// Declaration without value (undefined)
let playerName;

// Assign value later
playerName = "Dara";

// Change value
score = 150;
```

---

## Lesson 2: let, const, and var

### Three Ways to Declare

```javascript
let   message = "Hello";   // Can be changed
const PI = 3.14159;        // Cannot be changed
var   oldWay = "Legacy";   // Old way (avoid)
```

### let — Use Most of the Time

```javascript
let count = 0;
count = 1;  // ✅ OK - can change
count = 2;  // ✅ OK - can change again

let count = 3;  // ❌ Error - can't redeclare
```

### const — For Values That Don't Change

```javascript
const maxUsers = 100;
maxUsers = 200;  // ❌ Error! Cannot change const

const siteName = "KOOMPI";
siteName = "Other";  // ❌ Error!
```

**When to use const:**

- Configuration values
- Constants (like PI, MAX_VALUE)
- DOM element references
- When value shouldn't change

### var — The Old Way (Avoid)

```javascript
var oldVariable = "Legacy code";
// Works but can cause problems
// Only use when maintaining old code
```

### Comparison

| Feature | let | const | var |
|---------|-----|-------|-----|
| Can reassign | ✅ Yes | ❌ No | ✅ Yes |
| Can redeclare | ❌ No | ❌ No | ✅ Yes |
| Block scope | ✅ Yes | ✅ Yes | ❌ No |
| Recommended | ✅ | ✅ | ❌ |

---

## Lesson 3: Naming Variables

### Rules

```javascript
// Valid names
let userName;
let user_name;
let userName1;
let $price;
let _private;

// Invalid names
let 1user;      // ❌ Can't start with number
let user-name;  // ❌ Can't use hyphen
let let;        // ❌ Can't use reserved words
let my name;    // ❌ Can't have spaces
```

### Common Conventions

```javascript
// camelCase (most common in JavaScript)
let firstName;
let userEmailAddress;
let isLoggedIn;

// Use descriptive names
let x;         // ❌ What does x mean?
let userAge;   // ✅ Clear meaning

// Boolean names often start with is, has, can
let isActive;
let hasPermission;
let canEdit;
```

### Reserved Words (Can't Use)

```
break, case, catch, class, const, continue, 
do, else, export, extends, false, finally, 
for, function, if, import, in, instanceof, 
let, new, null, return, static, switch, 
this, throw, true, try, typeof, undefined, 
var, void, while, with, yield
```

---

## Lesson 4: Data Types

### Primitive Data Types

```javascript
// 1. STRING - text
let name = "Sokha";
let greeting = 'Hello!';
let message = `Welcome, ${name}`;

// 2. NUMBER - integers and decimals
let age = 22;
let price = 9.99;
let negative = -10;

// 3. BOOLEAN - true or false
let isStudent = true;
let hasLicense = false;

// 4. UNDEFINED - no value assigned
let unknown;
console.log(unknown);  // undefined

// 5. NULL - intentionally empty
let selectedUser = null;

// 6. SYMBOL - unique identifier (advanced)
let id = Symbol('id');
```

### Checking Type

```javascript
let name = "Sokha";
let age = 22;
let isStudent = true;

console.log(typeof name);      // "string"
console.log(typeof age);       // "number"
console.log(typeof isStudent); // "boolean"
console.log(typeof undefined); // "undefined"
console.log(typeof null);      // "object" (JavaScript quirk!)
```

---

## Lesson 5: Working with Strings

### Creating Strings

```javascript
// Single quotes
let str1 = 'Hello';

// Double quotes
let str2 = "World";

// Template literals (backticks) - allows expressions
let str3 = `Hello, World!`;
```

### String Concatenation

```javascript
let firstName = "Sokha";
let lastName = "Meas";

// Using +
let fullName = firstName + " " + lastName;
console.log(fullName);  // "Sokha Meas"

// Using template literals (better!)
let greeting = `Hello, ${firstName} ${lastName}!`;
console.log(greeting);  // "Hello, Sokha Meas!"
```

### Template Literals

```javascript
let name = "Dara";
let age = 25;

// Can embed expressions
let intro = `My name is ${name} and I am ${age} years old.`;

// Can do calculations
let message = `Next year I will be ${age + 1}.`;

// Multi-line strings
let poem = `
    Roses are red,
    Violets are blue,
    JavaScript is fun,
    And so are you!
`;
```

### String Properties and Methods

```javascript
let text = "Hello, Cambodia!";

// Length
console.log(text.length);  // 16

// Access character
console.log(text[0]);      // "H"
console.log(text[7]);      // "C"

// Common methods
console.log(text.toUpperCase());  // "HELLO, CAMBODIA!"
console.log(text.toLowerCase());  // "hello, cambodia!"
console.log(text.includes("Cambodia"));  // true
console.log(text.indexOf("Cambodia"));   // 7
console.log(text.slice(0, 5));    // "Hello"
console.log(text.replace("Cambodia", "World"));  // "Hello, World!"
```

---

## Lesson 6: Working with Numbers

### Basic Operations

```javascript
let a = 10;
let b = 3;

console.log(a + b);   // 13 (addition)
console.log(a - b);   // 7 (subtraction)
console.log(a * b);   // 30 (multiplication)
console.log(a / b);   // 3.333... (division)
console.log(a % b);   // 1 (remainder/modulo)
console.log(a ** b);  // 1000 (exponent)
```

### Increment and Decrement

```javascript
let count = 0;

count++;  // count is now 1
count++;  // count is now 2
count--;  // count is now 1

// Also:
count += 5;  // count = count + 5
count -= 2;  // count = count - 2
count *= 3;  // count = count * 3
```

### Math Object

```javascript
// Rounding
console.log(Math.round(4.5));   // 5
console.log(Math.floor(4.9));   // 4 (round down)
console.log(Math.ceil(4.1));    // 5 (round up)

// Other useful methods
console.log(Math.abs(-5));      // 5 (absolute value)
console.log(Math.max(1, 5, 3)); // 5
console.log(Math.min(1, 5, 3)); // 1
console.log(Math.random());     // Random 0-1

// Random whole number between 1 and 10
let random = Math.floor(Math.random() * 10) + 1;
```

---

## Lesson 7: Type Conversion

### Automatic Conversion (Coercion)

```javascript
// String + Number = String
console.log("5" + 3);      // "53" (string)

// Number operations try to convert
console.log("5" - 3);      // 2 (number)
console.log("5" * 3);      // 15 (number)

// Be careful!
console.log("5" + 3);      // "53"
console.log(5 + "3");      // "53"
```

### Explicit Conversion

```javascript
// To String
let num = 123;
let str = String(num);        // "123"
let str2 = num.toString();    // "123"

// To Number
let text = "456";
let number = Number(text);    // 456
let num2 = parseInt("456");   // 456
let num3 = parseFloat("3.14"); // 3.14

// To Boolean
let bool = Boolean(1);        // true
let bool2 = Boolean(0);       // false
let bool3 = Boolean("");      // false
let bool4 = Boolean("hello"); // true
```

### Truthy and Falsy

```javascript
// Falsy values (become false)
Boolean(0);          // false
Boolean("");         // false
Boolean(null);       // false
Boolean(undefined);  // false
Boolean(NaN);        // false
Boolean(false);      // false

// Everything else is truthy
Boolean(1);          // true
Boolean("hello");    // true
Boolean([]);         // true
Boolean({});         // true
```

---

## 🧪 Self-Check Exercises

### Exercise 1: Variable Practice

Create variables for:

- Your name
- Your age
- Whether you are a student (true/false)
- Your favorite color

Print all of them to the console.

### Exercise 2: String Concatenation

Create a variable with your first name and another with your last name. Combine them to create a full name using:

1. The + operator
2. Template literals

### Exercise 3: Math Calculator

Create variables for:

- price = 100
- quantity = 5
- taxRate = 0.10

Calculate and print:

- Subtotal (price × quantity)
- Tax amount (subtotal × taxRate)
- Total (subtotal + tax)

### Exercise 4: Type Checking

For each variable below, use typeof to check the type:

```javascript
let a = "Hello";
let b = 42;
let c = true;
let d;
let e = null;
```

### Exercise 5: User Info

Create a page that:

1. Prompts for user's name
2. Prompts for user's age
3. Displays: "Hello [name], you will be [age+1] next year!"

---

## 📝 Module Summary

**Variable Declarations**

| Keyword | Reassign | Best For |
|---------|----------|----------|
| `let` | ✅ Yes | Variables that change |
| `const` | ❌ No | Constants, config |
| `var` | ✅ Yes | Old code only |

**Data Types**

| Type | Example |
|------|---------|
| String | `"Hello"` |
| Number | `42`, `3.14` |
| Boolean | `true`, `false` |
| Undefined | `undefined` |
| Null | `null` |

---

## 🎯 Next Steps

**Before moving to Module 03:**

- [ ] Practiced variable declarations
- [ ] Worked with strings and numbers
- [ ] Understand data types
- [ ] Completed all exercises
- [ ] Get mentor verification

**Coming Next**: Module 03 - Operators & Conditions

*You will learn to make decisions in code!*

---

<div align="center">

**Data is the foundation!** 📊

*Everything in programming starts with data.*

</div>
