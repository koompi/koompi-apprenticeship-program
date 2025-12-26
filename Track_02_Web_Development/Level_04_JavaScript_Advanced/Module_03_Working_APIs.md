# Module 03: Working with APIs

## Level 2.4: JavaScript Advanced

---

## Module Objectives

By the end of this module, you will be able to:

- Understand what APIs are and how they work
- Use the Fetch API to make HTTP requests
- Handle JSON data
- Work with REST APIs

---

## Lesson 1: What is an API?

### API Defined

- WHAT IS AN API?
- API = Application Programming Interface
- Think of it as a waiter in a restaurant:
- YOU (Client) WAITER (API) KITCHEN (Server)
- "I want pizza" ► Takes order ► Makes pizza
- Eats pizza ◄ Delivers food ◄ Prepares dish
- You don't need to know HOW the kitchen works.
- The waiter handles the communication.

### Web APIs

- **Weather API** → Get weather data
- **Maps API** → Get location data
- **Social Media APIs** → Get posts, profiles
- **Payment APIs** → Process payments
- **Your own API** → Your app's data

---

## Lesson 2: HTTP Basics

### HTTP Methods

| Method | Purpose | Example |
|--------|---------|---------|
| `GET` | Read data | Get list of users |
| `POST` | Create data | Create new user |
| `PUT` | Update data (replace) | Update entire user |
| `PATCH` | Update data (partial) | Update user's email |
| `DELETE` | Remove data | Delete user |

### HTTP Status Codes

| Code | Meaning | When |
|------|---------|------|
| 200 | OK | Request succeeded |
| 201 | Created | New resource created |
| 400 | Bad Request | Invalid request data |
| 401 | Unauthorized | Need to log in |
| 403 | Forbidden | Don't have permission |
| 404 | Not Found | Resource doesn't exist |
| 500 | Server Error | Server problem |

---

## Lesson 3: The Fetch API

### Basic GET Request

```javascript
fetch('https://api.example.com/users')
 .then(response => response.json())
 .then(data => console.log(data))
 .catch(error => console.error('Error:', error));
```

### With Async/Await

```javascript
async function getUsers() {
 try {
 const response = await fetch('https://api.example.com/users');
 const data = await response.json();
 console.log(data);
 return data;
 } catch (error) {
 console.error('Error:', error);
 }
}
```

### Checking Response

```javascript
async function fetchData(url) {
 const response = await fetch(url);
 
 if (!response.ok) {
 throw new Error(`HTTP error! Status: ${response.status}`);
 }
 
 return response.json();
}
```

---

## Lesson 4: Request Options

### POST Request

```javascript
async function createUser(userData) {
 const response = await fetch('https://api.example.com/users', {
 method: 'POST',
 headers: {
 'Content-Type': 'application/json'
 },
 body: JSON.stringify(userData)
 });
 
 return response.json();
}

// Usage
createUser({ name: 'Sokha', email: 'sokha@email.com' });
```

### PUT Request

```javascript
async function updateUser(id, userData) {
 const response = await fetch(`https://api.example.com/users/${id}`, {
 method: 'PUT',
 headers: {
 'Content-Type': 'application/json'
 },
 body: JSON.stringify(userData)
 });
 
 return response.json();
}
```

### DELETE Request

```javascript
async function deleteUser(id) {
 const response = await fetch(`https://api.example.com/users/${id}`, {
 method: 'DELETE'
 });
 
 return response.ok;
}
```

### With Authentication

```javascript
async function fetchProtectedData() {
 const token = 'your-auth-token';
 
 const response = await fetch('https://api.example.com/protected', {
 headers: {
 'Authorization': `Bearer ${token}`,
 'Content-Type': 'application/json'
 }
 });
 
 return response.json();
}
```

---

## Lesson 5: Working with JSON

### What is JSON?

```javascript
// JSON = JavaScript Object Notation
// A text format for storing and transmitting data

{
 "name": "Sokha",
 "age": 22,
 "isStudent": true,
 "skills": ["HTML", "CSS", "JavaScript"],
 "address": {
 "city": "Phnom Penh",
 "country": "Cambodia"
 }
}
```

### Parsing JSON

```javascript
// String to Object
const jsonString = '{"name": "Sokha", "age": 22}';
const obj = JSON.parse(jsonString);
console.log(obj.name); // "Sokha"

// Object to String
const data = { name: "Dara", age: 25 };
const json = JSON.stringify(data);
console.log(json); // '{"name":"Dara","age":25}'

// Pretty print
const prettyJson = JSON.stringify(data, null, 2);
```

### Handling API Response

```javascript
async function displayUsers() {
 try {
 const response = await fetch('https://jsonplaceholder.typicode.com/users');
 const users = await response.json();
 
 users.forEach(user => {
 console.log(`${user.name} - ${user.email}`);
 });
 } catch (error) {
 console.error('Failed to load users:', error);
 }
}
```

---

## Lesson 6: Real API Examples

### JSONPlaceholder (Practice API)

```javascript
// Free fake API for testing
const API_URL = 'https://jsonplaceholder.typicode.com';

// Get posts
async function getPosts() {
 const response = await fetch(`${API_URL}/posts`);
 return response.json();
}

// Get single post
async function getPost(id) {
 const response = await fetch(`${API_URL}/posts/${id}`);
 return response.json();
}

// Get post's comments
async function getPostComments(postId) {
 const response = await fetch(`${API_URL}/posts/${postId}/comments`);
 return response.json();
}
```

### Weather API Example

```javascript
const API_KEY = 'your-api-key';

async function getWeather(city) {
 const url = `https://api.openweathermap.org/data/2.5/weather?q=${city}&appid=${API_KEY}&units=metric`;
 
 try {
 const response = await fetch(url);
 
 if (!response.ok) {
 throw new Error('City not found');
 }
 
 const data = await response.json();
 
 return {
 city: data.name,
 temp: data.main.temp,
 description: data.weather[0].description,
 humidity: data.main.humidity
 };
 } catch (error) {
 console.error('Weather fetch failed:', error);
 throw error;
 }
}

// Usage
const weather = await getWeather('Phnom Penh');
console.log(`${weather.city}: ${weather.temp}°C, ${weather.description}`);
```

---

## Lesson 7: Building an API Client

### Reusable API Class

```javascript
class ApiClient {
 constructor(baseURL) {
 this.baseURL = baseURL;
 }
 
 async request(endpoint, options = {}) {
 const url = `${this.baseURL}${endpoint}`;
 
 const config = {
 headers: {
 'Content-Type': 'application/json',
 ...options.headers
 },
 ...options
 };
 
 if (config.body) {
 config.body = JSON.stringify(config.body);
 }
 
 const response = await fetch(url, config);
 
 if (!response.ok) {
 const error = await response.json();
 throw new Error(error.message || 'Request failed');
 }
 
 return response.json();
 }
 
 get(endpoint) {
 return this.request(endpoint);
 }
 
 post(endpoint, data) {
 return this.request(endpoint, {
 method: 'POST',
 body: data
 });
 }
 
 put(endpoint, data) {
 return this.request(endpoint, {
 method: 'PUT',
 body: data
 });
 }
 
 delete(endpoint) {
 return this.request(endpoint, {
 method: 'DELETE'
 });
 }
}

// Usage
const api = new ApiClient('https://api.example.com');

const users = await api.get('/users');
const newUser = await api.post('/users', { name: 'Sokha' });
await api.delete('/users/1');
```

---

## Self-Check Exercises

### Exercise 1: Fetch Users

Fetch users from JSONPlaceholder and display their names.

### Exercise 2: Create Post

Create a new post using the POST method.

### Exercise 3: Search Users

Create a function that searches users by name.

### Exercise 4: Error Handling

Add proper error handling to display user-friendly messages.

### Exercise 5: Weather Widget

Create a simple weather widget that:

1. Has an input for city name
2. Fetches weather data
3. Displays temperature and conditions

---

## Module Summary

| Concept | Description |
|---------|-------------|
| API | Interface to get/send data |
| REST | Standard for web APIs |
| Fetch | Browser API for HTTP requests |
| JSON | Data format for APIs |
| Methods | GET, POST, PUT, DELETE |

**Common Fetch Pattern:**

```javascript
async function fetchData(url) {
 try {
 const response = await fetch(url);
 if (!response.ok) throw new Error('Failed');
 return await response.json();
 } catch (error) {
 console.error(error);
 throw error;
 }
}
```

---

## Next Steps

**Coming Next**: Module 04 - Error Handling & Debugging

*You will learn to handle errors gracefully and debug effectively!*

---

<div align="center">

**APIs connect you to the world!** 

*Every modern app uses APIs.*

</div>
