# Module 02: Asynchronous JavaScript

## Level 2.4: JavaScript Advanced

---

## Module Objectives

By the end of this module, you will be able to:

- Understand synchronous vs asynchronous code
- Use callbacks and understand callback hell
- Work with Promises
- Master async/await syntax

---

## Lesson 1: Sync vs Async

### Synchronous Code

Runs line by line, each waits for the previous:

```javascript
console.log("First");
console.log("Second");
console.log("Third");

// Output:
// First
// Second
// Third
```

### Asynchronous Code

Some operations don't wait:

```javascript
console.log("First");

setTimeout(() => {
 console.log("Second");
}, 2000);

console.log("Third");

// Output:
// First
// Third
// Second (after 2 seconds)
```

### Why Async Matters

- ASYNC IS ESSENTIAL FOR:
- • Fetching data from servers
- • Reading/writing files
- • User interactions
- • Timers and animations
- • Database operations
- Without async, your app would FREEZE during these operations!

---

## Lesson 2: Callbacks

### What is a Callback?

A function passed to another function to be called later:

```javascript
function greet(name, callback) {
 console.log(`Hello, ${name}!`);
 callback();
}

function sayGoodbye() {
 console.log("Goodbye!");
}

greet("Sokha", sayGoodbye);
// Hello, Sokha!
// Goodbye!
```

### Async Callbacks

```javascript
function fetchUser(userId, callback) {
 setTimeout(() => {
 const user = { id: userId, name: "Sokha" };
 callback(user);
 }, 1000);
}

fetchUser(1, (user) => {
 console.log(user); // { id: 1, name: "Sokha" }
});
```

### Callback Hell 

Nested callbacks become unreadable:

```javascript
getUser(userId, (user) => {
 getPosts(user.id, (posts) => {
 getComments(posts[0].id, (comments) => {
 getLikes(comments[0].id, (likes) => {
 // This is callback hell!
 console.log(likes);
 });
 });
 });
});
```

This is why we have Promises!

---

## Lesson 3: Promises

### What is a Promise?

A Promise represents a value that may be available now, later, or never.

```javascript
const promise = new Promise((resolve, reject) => {
 // Async operation
 setTimeout(() => {
 const success = true;
 
 if (success) {
 resolve("Data loaded!");
 } else {
 reject("Error loading data");
 }
 }, 1000);
});
```

### Promise States

- PROMISE STATES
- PENDING ► FULFILLED (resolved with value)
- (waiting)
- ► REJECTED (rejected with error)
- Once settled (fulfilled or rejected), cannot change

### Using Promises

```javascript
const promise = fetchData();

promise
 .then(data => {
 console.log("Success:", data);
 })
 .catch(error => {
 console.log("Error:", error);
 })
 .finally(() => {
 console.log("Done (success or fail)");
 });
```

### Chaining Promises

```javascript
fetchUser(1)
 .then(user => {
 console.log(user);
 return fetchPosts(user.id);
 })
 .then(posts => {
 console.log(posts);
 return fetchComments(posts[0].id);
 })
 .then(comments => {
 console.log(comments);
 })
 .catch(error => {
 console.log("Error:", error);
 });
```

Much cleaner than callback hell!

---

## Lesson 4: Creating Promises

### Basic Promise

```javascript
function delay(ms) {
 return new Promise(resolve => {
 setTimeout(resolve, ms);
 });
}

delay(2000).then(() => {
 console.log("2 seconds passed!");
});
```

### Promise with Data

```javascript
function fetchUser(id) {
 return new Promise((resolve, reject) => {
 setTimeout(() => {
 if (id > 0) {
 resolve({ id, name: "Sokha" });
 } else {
 reject("Invalid ID");
 }
 }, 1000);
 });
}

fetchUser(1)
 .then(user => console.log(user))
 .catch(err => console.log(err));
```

### Promise.all

Wait for multiple promises:

```javascript
const promise1 = fetchUser(1);
const promise2 = fetchUser(2);
const promise3 = fetchUser(3);

Promise.all([promise1, promise2, promise3])
 .then(users => {
 console.log(users); // Array of all users
 })
 .catch(error => {
 console.log("One failed:", error);
 });
```

### Promise.race

First to complete wins:

```javascript
Promise.race([
 fetchFromServer1(),
 fetchFromServer2()
])
.then(result => {
 console.log("First result:", result);
});
```

---

## Lesson 5: Async/Await

### The Modern Way

Async/await makes async code look synchronous:

```javascript
// With Promises
function getData() {
 return fetchUser(1)
 .then(user => fetchPosts(user.id))
 .then(posts => console.log(posts));
}

// With async/await
async function getData() {
 const user = await fetchUser(1);
 const posts = await fetchPosts(user.id);
 console.log(posts);
}
```

### async Keyword

Makes a function return a Promise:

```javascript
async function greet() {
 return "Hello!";
}

greet().then(message => console.log(message)); // "Hello!"
```

### await Keyword

Pauses execution until Promise resolves:

```javascript
async function loadData() {
 console.log("Loading...");
 
 const data = await fetchData(); // Waits here
 
 console.log("Data:", data);
 return data;
}
```

### Error Handling with try/catch

```javascript
async function loadUser(id) {
 try {
 const user = await fetchUser(id);
 const posts = await fetchPosts(user.id);
 return { user, posts };
 } catch (error) {
 console.error("Failed:", error);
 throw error; // Re-throw if needed
 }
}
```

---

## Lesson 6: Practical Examples

### Sequential vs Parallel

```javascript
// Sequential - one after another (slower)
async function sequential() {
 const user1 = await fetchUser(1); // Wait 1s
 const user2 = await fetchUser(2); // Wait 1s
 const user3 = await fetchUser(3); // Wait 1s
 // Total: 3 seconds
}

// Parallel - all at once (faster)
async function parallel() {
 const [user1, user2, user3] = await Promise.all([
 fetchUser(1),
 fetchUser(2),
 fetchUser(3)
 ]);
 // Total: 1 second (all run together)
}
```

### Loading Indicator

```javascript
async function loadDataWithUI() {
 const loadingDiv = document.getElementById("loading");
 const contentDiv = document.getElementById("content");
 
 try {
 loadingDiv.style.display = "block";
 contentDiv.style.display = "none";
 
 const data = await fetchData();
 
 contentDiv.innerHTML = renderData(data);
 contentDiv.style.display = "block";
 } catch (error) {
 contentDiv.innerHTML = `<p class="error">${error.message}</p>`;
 contentDiv.style.display = "block";
 } finally {
 loadingDiv.style.display = "none";
 }
}
```

### Retry Logic

```javascript
async function fetchWithRetry(url, maxRetries = 3) {
 for (let i = 0; i < maxRetries; i++) {
 try {
 const response = await fetch(url);
 return await response.json();
 } catch (error) {
 console.log(`Attempt ${i + 1} failed`);
 if (i === maxRetries - 1) throw error;
 await delay(1000); // Wait before retry
 }
 }
}
```

---

## Lesson 7: Common Patterns

### Async in Array Methods

```javascript
// WRONG - forEach doesn't wait
urls.forEach(async url => {
 await fetch(url); // These run in parallel, not sequential
});

// RIGHT - for...of for sequential
for (const url of urls) {
 await fetch(url);
}

// RIGHT - Promise.all for parallel
await Promise.all(urls.map(url => fetch(url)));
```

### Immediately Invoked Async Function

```javascript
(async () => {
 const data = await fetchData();
 console.log(data);
})();
```

### Top-Level Await (ES2022+)

In modules, you can use await at the top level:

```javascript
// In a module file
const data = await fetchData();
export { data };
```

---

## Self-Check Exercises

### Exercise 1: Convert Callback to Promise

Convert this callback-based function to return a Promise:

```javascript
function loadData(callback) {
 setTimeout(() => {
 callback({ name: "Data" });
 }, 1000);
}
```

### Exercise 2: Promise Chain

Create a promise chain that:

1. Fetches a user
2. Fetches their posts
3. Fetches comments on first post
4. Logs the comments

### Exercise 3: Async/Await Conversion

Convert the promise chain from Exercise 2 to async/await.

### Exercise 4: Parallel Loading

Load 3 different data sources in parallel using Promise.all.

### Exercise 5: Error Handling

Add proper error handling to the async function with user feedback.

---

## Module Summary

| Concept | Syntax | Use Case |
|---------|--------|----------|
| Callback | `fn(callback)` | Legacy, simple cases |
| Promise | `.then().catch()` | Chained async |
| async/await | `async/await` | Modern, readable |
| Promise.all | `Promise.all([])` | Parallel execution |

---

## Next Steps

**Coming Next**: Module 03 - Working with APIs

*You will learn to fetch real data from web APIs!*

---

<div align="center">

**Async unlocks the web!** 

*Almost everything interesting is asynchronous.*

</div>
