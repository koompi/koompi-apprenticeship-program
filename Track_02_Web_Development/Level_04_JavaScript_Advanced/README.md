# Level 2.4: JavaScript Advanced

## Track 02: Web Development

---

## Level Overview

Take your JavaScript skills further! Learn advanced concepts that power real-world applications.

**Duration**: 3-4 weeks

**Modules in this Level:**

1. ES6+ Modern Features
2. Asynchronous JavaScript
3. Working with APIs
4. Error Handling & Debugging
5. Project: Weather Dashboard

---

## Prerequisites

- Completed Level 2.3: JavaScript Basics
- Built Interactive Quiz project
- Comfortable with functions, arrays, DOM

---

## What You'll Build

A **Weather Dashboard** that fetches real weather data:

```
┌─────────────────────────────────────────────────────────────────────────────┐
│ │
│ WEATHER DASHBOARD │
│ │
│ ┌─────────────────────────────────────────────────────────────────────┐ │
│ │ Search: [Phnom Penh_____________] [ Search] │ │
│ └─────────────────────────────────────────────────────────────────────┘ │
│ │
│ ┌─────────────────────────────────────────────────────────────────────┐ │
│ │ │ │
│ │ Phnom Penh, Cambodia │ │
│ │ ━━━━━━━━━━━━━━━━━━━━━━━━ │ │
│ │ │ │
│ │ 32°C │ │
│ │ Sunny │ │
│ │ │ │
│ │ Humidity: 65% Wind: 12 km/h UV: High │ │
│ │ │ │
│ └─────────────────────────────────────────────────────────────────────┘ │
│ │
│ ┌────────┐ ┌────────┐ ┌────────┐ ┌────────┐ ┌────────┐ │
│ │ MON │ │ TUE │ │ WED │ │ THU │ │ FRI │ │
│ │ │ │ │ │ │ │ │ │ │ │
│ │ 31° │ │ 29° │ │ 27° │ │ 30° │ │ 32° │ │
│ └────────┘ └────────┘ └────────┘ └────────┘ └────────┘ │
│ │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## Module Index

| Module | Topic | Key Concepts |
|--------|-------|--------------|
| 01 | ES6+ Features | Destructuring, spread, modules |
| 02 | Async JavaScript | Promises, async/await, callbacks |
| 03 | Working with APIs | Fetch, JSON, REST APIs |
| 04 | Error Handling | Try/catch, debugging strategies |
| 05 | Project | Weather Dashboard |

---

## Key Concepts

### ES6+ Features

```javascript
// Destructuring
const { name, age } = user;

// Spread operator
const newArray = [...oldArray, newItem];

// Template literals
const message = `Hello, ${name}!`;

// Arrow functions
const add = (a, b) => a + b;
```

### Async/Await

```javascript
async function getWeather(city) {
 try {
 const response = await fetch(`api/weather?city=${city}`);
 const data = await response.json();
 return data;
 } catch (error) {
 console.error("Failed to fetch weather:", error);
 }
}
```

### Fetch API

```javascript
fetch('https://api.example.com/data')
 .then(response => response.json())
 .then(data => console.log(data))
 .catch(error => console.error(error));
```

---

## Level Completion

**To complete Level 2.4:**

- [ ] All 5 modules studied
- [ ] Understand async/await
- [ ] Can fetch data from APIs
- [ ] Weather Dashboard working
- [ ] Handle errors gracefully
- [ ] **JavaScript Advanced Badge** earned

---

<div align="center">

**Real apps need real data!** 

*Start with Module 01: ES6+ Features*

</div>
