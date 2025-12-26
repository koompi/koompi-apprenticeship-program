# Module 03: Operators & Conditions

## Level 2.3: JavaScript Basics

---

## 🎯 Module Objectives

By the end of this module, you will be able to:

- Use comparison and logical operators
- Write conditional statements (if/else)
- Use switch statements
- Combine conditions with AND/OR logic

---

## Lesson 1: Comparison Operators

### Comparing Values

```javascript
let a = 10;
let b = 5;

// Greater than / Less than
console.log(a > b);   // true
console.log(a < b);   // false
console.log(a >= 10); // true
console.log(b <= 5);  // true

// Equal / Not equal
console.log(a == 10);  // true
console.log(a != b);   // true
```

### == vs === (Important!)

```javascript
// == compares VALUE (with conversion)
console.log(5 == "5");    // true (string converted to number)
console.log(1 == true);   // true (true converted to 1)

// === compares VALUE AND TYPE (strict)
console.log(5 === "5");   // false (different types)
console.log(1 === true);  // false (different types)
console.log(5 === 5);     // true (same value and type)
```

**Always use === and !== for safety!**

### Comparison Reference

| Operator | Meaning | Example |
|----------|---------|---------|
| `==` | Equal (loose) | `5 == "5"` → true |
| `===` | Equal (strict) | `5 === 5` → true |
| `!=` | Not equal (loose) | `5 != "6"` → true |
| `!==` | Not equal (strict) | `5 !== "5"` → true |
| `>` | Greater than | `10 > 5` → true |
| `<` | Less than | `5 < 10` → true |
| `>=` | Greater or equal | `5 >= 5` → true |
| `<=` | Less or equal | `5 <= 10` → true |

---

## Lesson 2: Logical Operators

### AND (&&)

**Both** conditions must be true:

```javascript
let age = 25;
let hasLicense = true;

// Can drive only if 18+ AND has license
let canDrive = age >= 18 && hasLicense;
console.log(canDrive);  // true

// Example
console.log(true && true);   // true
console.log(true && false);  // false
console.log(false && true);  // false
console.log(false && false); // false
```

### OR (||)

**At least one** condition must be true:

```javascript
let isWeekend = true;
let isHoliday = false;

// Day off if weekend OR holiday
let isDayOff = isWeekend || isHoliday;
console.log(isDayOff);  // true

// Example
console.log(true || true);   // true
console.log(true || false);  // true
console.log(false || true);  // true
console.log(false || false); // false
```

### NOT (!)

**Inverts** the value:

```javascript
let isLoggedIn = false;

console.log(!isLoggedIn);  // true
console.log(!true);        // false
console.log(!false);       // true
```

---

## Lesson 3: If Statements

### Basic If

```javascript
let age = 20;

if (age >= 18) {
    console.log("You are an adult.");
}
```

### If...Else

```javascript
let age = 15;

if (age >= 18) {
    console.log("You are an adult.");
} else {
    console.log("You are a minor.");
}
```

### If...Else If...Else

```javascript
let score = 85;

if (score >= 90) {
    console.log("Grade: A");
} else if (score >= 80) {
    console.log("Grade: B");
} else if (score >= 70) {
    console.log("Grade: C");
} else if (score >= 60) {
    console.log("Grade: D");
} else {
    console.log("Grade: F");
}
```

### Nested If

```javascript
let age = 25;
let hasLicense = true;

if (age >= 18) {
    if (hasLicense) {
        console.log("You can drive.");
    } else {
        console.log("You need a license.");
    }
} else {
    console.log("You are too young to drive.");
}
```

---

## Lesson 4: Combining Conditions

### Multiple Conditions with AND

```javascript
let age = 25;
let hasLicense = true;
let hasInsurance = true;

if (age >= 18 && hasLicense && hasInsurance) {
    console.log("You can legally drive.");
}
```

### Multiple Conditions with OR

```javascript
let day = "Saturday";

if (day === "Saturday" || day === "Sunday") {
    console.log("It's the weekend!");
} else {
    console.log("It's a weekday.");
}
```

### Complex Conditions

```javascript
let age = 22;
let isStudent = true;
let isEmployee = false;

// Student discount for students OR employees under 25
if (isStudent || (isEmployee && age < 25)) {
    console.log("You get a discount!");
}
```

---

## Lesson 5: Switch Statements

### When to Use Switch

Use switch when comparing one value against many options:

```javascript
let day = 3;

switch (day) {
    case 1:
        console.log("Monday");
        break;
    case 2:
        console.log("Tuesday");
        break;
    case 3:
        console.log("Wednesday");
        break;
    case 4:
        console.log("Thursday");
        break;
    case 5:
        console.log("Friday");
        break;
    case 6:
        console.log("Saturday");
        break;
    case 7:
        console.log("Sunday");
        break;
    default:
        console.log("Invalid day");
}
```

### Break is Important

Without break, code "falls through" to the next case:

```javascript
let fruit = "apple";

switch (fruit) {
    case "apple":
    case "apricot":
        console.log("Starts with A");
        break;
    case "banana":
        console.log("Starts with B");
        break;
    default:
        console.log("Other fruit");
}
```

---

## Lesson 6: Ternary Operator

### Short If/Else

The ternary operator is a shorthand for simple if/else:

```javascript
// condition ? valueIfTrue : valueIfFalse

let age = 20;
let status = age >= 18 ? "adult" : "minor";
console.log(status);  // "adult"

// Same as:
let status2;
if (age >= 18) {
    status2 = "adult";
} else {
    status2 = "minor";
}
```

### Practical Examples

```javascript
// Greeting based on time
let hour = 14;
let greeting = hour < 12 ? "Good morning" : "Good afternoon";

// Show/hide text
let isVisible = true;
let display = isVisible ? "block" : "none";

// Singular/plural
let count = 5;
let message = `You have ${count} item${count === 1 ? "" : "s"}`;
console.log(message);  // "You have 5 items"
```

---

## Lesson 7: Practical Examples

### Login Check

```javascript
let username = prompt("Enter username:");
let password = prompt("Enter password:");

const correctUser = "admin";
const correctPass = "password123";

if (username === correctUser && password === correctPass) {
    console.log("Login successful!");
} else if (username !== correctUser) {
    console.log("Username not found.");
} else {
    console.log("Incorrect password.");
}
```

### Age Verification

```javascript
let age = parseInt(prompt("Enter your age:"));

if (isNaN(age)) {
    console.log("Please enter a valid number.");
} else if (age < 0) {
    console.log("Age cannot be negative.");
} else if (age < 13) {
    console.log("You are a child.");
} else if (age < 20) {
    console.log("You are a teenager.");
} else if (age < 60) {
    console.log("You are an adult.");
} else {
    console.log("You are a senior.");
}
```

### Grade Calculator

```javascript
function getGrade(score) {
    if (score < 0 || score > 100) {
        return "Invalid score";
    }
    
    if (score >= 90) return "A";
    if (score >= 80) return "B";
    if (score >= 70) return "C";
    if (score >= 60) return "D";
    return "F";
}

console.log(getGrade(85));  // "B"
```

---

## 🧪 Self-Check Exercises

### Exercise 1: Comparison Practice

What do these evaluate to?

```javascript
console.log(10 > 5);
console.log(5 === "5");
console.log(5 == "5");
console.log("hello" !== "Hello");
console.log(10 >= 10);
```

### Exercise 2: Odd or Even

Write code that:

1. Asks for a number
2. Tells if it's odd or even

### Exercise 3: Grade Calculator

Write a program that:

1. Asks for a score (0-100)
2. Outputs the grade (A, B, C, D, F)

### Exercise 4: Login System

Create a simple login that:

1. Asks for username and password
2. Checks against stored values
3. Shows success or appropriate error

### Exercise 5: Day Name

Use a switch statement to:

1. Take a number 1-7
2. Output the day name (Monday-Sunday)

---

## 📝 Module Summary

**Comparison Operators**

| Operator | Meaning |
|----------|---------|
| `===` | Strict equal |
| `!==` | Strict not equal |
| `>` `<` | Greater/less than |
| `>=` `<=` | Greater/less than or equal |

**Logical Operators**

| Operator | Meaning |
|----------|---------|
| `&&` | AND |
| `\|\|` | OR |
| `!` | NOT |

**Conditionals**

| Type | Use When |
|------|----------|
| `if/else` | Simple conditions |
| `else if` | Multiple conditions |
| `switch` | Comparing one value to many |
| `? :` | Simple value assignment |

---

## 🎯 Next Steps

**Before moving to Module 04:**

- [ ] Master comparison operators
- [ ] Write complex conditions
- [ ] Completed all exercises
- [ ] Get mentor verification

**Coming Next**: Module 04 - Functions

*You will learn to organize your code into reusable pieces!*

---

<div align="center">

**Decisions drive your code!** 🚦

*If/else statements let your code think.*

</div>
