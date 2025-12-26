# Module 05: Arrays & Loops

## Level 2.3: JavaScript Basics

---

## Module Objectives

By the end of this module, you will be able to:

- Create and manipulate arrays
- Use for, while, and forEach loops
- Apply array methods (push, pop, map, filter)
- Iterate through collections

---

## Lesson 1: Introduction to Arrays

### What Are Arrays?

Arrays store multiple values in a single variable:

```javascript
// Without arrays
let student1 = "Sokha";
let student2 = "Dara";
let student3 = "Bopha";

// With arrays
let students = ["Sokha", "Dara", "Bopha"];
```

### Creating Arrays

```javascript
// Array literal (preferred)
let fruits = ["apple", "banana", "orange"];

// Empty array
let emptyArray = [];

// Mixed types (possible but not recommended)
let mixed = [1, "hello", true, null];

// Array of numbers
let scores = [85, 92, 78, 95, 88];
```

### Accessing Elements

Arrays are **zero-indexed** (start at 0):

```javascript
let colors = ["red", "green", "blue"];

console.log(colors[0]); // "red"
console.log(colors[1]); // "green"
console.log(colors[2]); // "blue"
console.log(colors[3]); // undefined (doesn't exist)

// Last element
console.log(colors[colors.length - 1]); // "blue"
```

### Array Length

```javascript
let fruits = ["apple", "banana", "orange"];
console.log(fruits.length); // 3
```

---

## Lesson 2: Modifying Arrays

### Changing Elements

```javascript
let colors = ["red", "green", "blue"];

colors[1] = "yellow";
console.log(colors); // ["red", "yellow", "blue"]
```

### Adding Elements

```javascript
let fruits = ["apple", "banana"];

// Add to end
fruits.push("orange");
console.log(fruits); // ["apple", "banana", "orange"]

// Add to beginning
fruits.unshift("mango");
console.log(fruits); // ["mango", "apple", "banana", "orange"]
```

### Removing Elements

```javascript
let fruits = ["apple", "banana", "orange"];

// Remove from end
let last = fruits.pop();
console.log(last); // "orange"
console.log(fruits); // ["apple", "banana"]

// Remove from beginning
let first = fruits.shift();
console.log(first); // "apple"
console.log(fruits); // ["banana"]
```

### Splice (Add/Remove at Position)

```javascript
let colors = ["red", "green", "blue", "yellow"];

// Remove 1 element at index 2
colors.splice(2, 1);
console.log(colors); // ["red", "green", "yellow"]

// Insert "purple" at index 1
colors.splice(1, 0, "purple");
console.log(colors); // ["red", "purple", "green", "yellow"]

// Replace 1 element at index 0 with "orange"
colors.splice(0, 1, "orange");
console.log(colors); // ["orange", "purple", "green", "yellow"]
```

---

## Lesson 3: For Loops

### Basic For Loop

```javascript
for (let i = 0; i < 5; i++) {
 console.log(i);
}
// Output: 0, 1, 2, 3, 4
```

### Loop Structure

```javascript
for (initialization; condition; update) {
 // code to repeat
}

// initialization: let i = 0 → runs once at start
// condition: i < 5 → checked before each iteration
// update: i++ → runs after each iteration
```

### Looping Through Arrays

```javascript
let fruits = ["apple", "banana", "orange"];

for (let i = 0; i < fruits.length; i++) {
 console.log(fruits[i]);
}
// apple
// banana
// orange
```

### For...of Loop (Simpler!)

```javascript
let fruits = ["apple", "banana", "orange"];

for (let fruit of fruits) {
 console.log(fruit);
}
// apple
// banana
// orange
```

---

## Lesson 4: While Loops

### While Loop

Repeats while condition is true:

```javascript
let count = 0;

while (count < 5) {
 console.log(count);
 count++;
}
// 0, 1, 2, 3, 4
```

### Do...While Loop

Runs at least once:

```javascript
let count = 0;

do {
 console.log(count);
 count++;
} while (count < 5);
// 0, 1, 2, 3, 4
```

### When to Use Each

| Loop Type | Best For |
|-----------|----------|
| `for` | Known number of iterations |
| `for...of` | Arrays and iterables |
| `while` | Unknown iterations, complex conditions |
| `do...while` | Must run at least once |

---

## Lesson 5: Array Methods

### forEach — Do Something with Each Element

```javascript
let numbers = [1, 2, 3, 4, 5];

numbers.forEach(function(num) {
 console.log(num * 2);
});
// 2, 4, 6, 8, 10

// With arrow function
numbers.forEach(num => console.log(num * 2));
```

### map — Transform Each Element

```javascript
let numbers = [1, 2, 3, 4, 5];

let doubled = numbers.map(num => num * 2);
console.log(doubled); // [2, 4, 6, 8, 10]

// Original unchanged
console.log(numbers); // [1, 2, 3, 4, 5]
```

### filter — Keep Matching Elements

```javascript
let numbers = [1, 2, 3, 4, 5, 6];

let evenNumbers = numbers.filter(num => num % 2 === 0);
console.log(evenNumbers); // [2, 4, 6]

// Find students with passing grades
let scores = [45, 72, 88, 55, 91, 67];
let passing = scores.filter(score => score >= 60);
console.log(passing); // [72, 88, 91, 67]
```

### find — Get First Match

```javascript
let users = [
 { name: "Sokha", age: 22 },
 { name: "Dara", age: 25 },
 { name: "Bopha", age: 22 }
];

let user = users.find(u => u.name === "Dara");
console.log(user); // { name: "Dara", age: 25 }
```

### includes — Check if Element Exists

```javascript
let fruits = ["apple", "banana", "orange"];

console.log(fruits.includes("banana")); // true
console.log(fruits.includes("grape")); // false
```

### reduce — Combine to Single Value

```javascript
let numbers = [1, 2, 3, 4, 5];

let sum = numbers.reduce((total, num) => total + num, 0);
console.log(sum); // 15

// Initial value is 0, then:
// 0 + 1 = 1
// 1 + 2 = 3
// 3 + 3 = 6
// 6 + 4 = 10
// 10 + 5 = 15
```

---

## Lesson 6: Practical Examples

### Shopping Cart

```javascript
let cart = [
 { name: "Laptop", price: 299 },
 { name: "Mouse", price: 25 },
 { name: "Keyboard", price: 49 }
];

// Calculate total
let total = cart.reduce((sum, item) => sum + item.price, 0);
console.log(`Total: $${total}`); // Total: $373

// Get item names
let items = cart.map(item => item.name);
console.log(items); // ["Laptop", "Mouse", "Keyboard"]

// Find expensive items
let expensive = cart.filter(item => item.price > 30);
console.log(expensive); // Laptop and Keyboard
```

### Student Grades

```javascript
let students = [
 { name: "Sokha", score: 85 },
 { name: "Dara", score: 72 },
 { name: "Bopha", score: 91 },
 { name: "Vanna", score: 58 }
];

// Get passing students
let passing = students.filter(s => s.score >= 60);
console.log(passing);

// Get names only
let names = students.map(s => s.name);
console.log(names);

// Calculate average
let total = students.reduce((sum, s) => sum + s.score, 0);
let average = total / students.length;
console.log(`Average: ${average}`); // 76.5
```

---

## Lesson 7: Nested Loops

### Looping Through 2D Arrays

```javascript
let matrix = [
 [1, 2, 3],
 [4, 5, 6],
 [7, 8, 9]
];

for (let row of matrix) {
 for (let num of row) {
 console.log(num);
 }
}
// 1, 2, 3, 4, 5, 6, 7, 8, 9
```

### Multiplication Table

```javascript
for (let i = 1; i <= 5; i++) {
 let row = "";
 for (let j = 1; j <= 5; j++) {
 row += `${i * j}\t`;
 }
 console.log(row);
}
// 1 2 3 4 5
// 2 4 6 8 10
// ...
```

---

## Self-Check Exercises

### Exercise 1: Array Basics

Create an array of 5 Cambodian provinces. Then:

1. Print each province
2. Add 2 more provinces
3. Remove the first one
4. Check if "Siem Reap" is in the array

### Exercise 2: Sum Array

Write a function that takes an array of numbers and returns their sum.

### Exercise 3: Find Maximum

Write a function that finds the largest number in an array (without using Math.max).

### Exercise 4: Filter Practice

Given an array of ages, filter to find:

1. All adults (18+)
2. All teenagers (13-19)

### Exercise 5: Todo List Data

Create an array of todo objects with task and done properties. Write functions to:

1. List all tasks
2. List only incomplete tasks
3. Mark a task as done
4. Count completed tasks

---

## Module Summary

**Array Methods**

| Method | Purpose | Returns |
|--------|---------|---------|
| `push()` | Add to end | New length |
| `pop()` | Remove from end | Removed element |
| `map()` | Transform all | New array |
| `filter()` | Keep matches | New array |
| `find()` | Get first match | Element or undefined |
| `forEach()` | Loop through | undefined |
| `reduce()` | Combine to one | Single value |
| `includes()` | Check existence | Boolean |

**Loop Types**

| Type | Syntax | Best For |
|------|--------|----------|
| for | `for (let i=0; i<n; i++)` | Index needed |
| for...of | `for (let x of arr)` | Simple iteration |
| forEach | `arr.forEach(fn)` | Array operations |
| while | `while (cond)` | Unknown iterations |

---

## Next Steps

**Before moving to Module 06:**

- [ ] Create and manipulate arrays
- [ ] Use all loop types
- [ ] Apply map, filter, reduce
- [ ] Complete all exercises
- [ ] Get mentor verification

**Coming Next**: Module 06 - DOM Manipulation

*You will learn to change web pages with JavaScript!*

---

<div align="center">

**Collections power your apps!** 

*Arrays hold all your data.*

</div>
