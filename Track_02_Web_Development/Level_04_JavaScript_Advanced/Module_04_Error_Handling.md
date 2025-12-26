# Module 04: Error Handling & Debugging

## Level 2.4: JavaScript Advanced

---

## Module Objectives

By the end of this module, you will be able to:

- Handle errors gracefully with try/catch
- Create custom error types
- Debug code effectively
- Use browser developer tools

---

## Lesson 1: Types of Errors

### JavaScript Error Types

```javascript
// SyntaxError - Invalid code structure
const x = ; // Unexpected token

// ReferenceError - Using undefined variable
console.log(undefinedVar);

// TypeError - Wrong type operation
null.toString();
const notFunc = 5;
notFunc();

// RangeError - Number out of range
const arr = new Array(-1);

// URIError - Invalid URI
decodeURI('%');
```

### Runtime vs Syntax Errors

| Type | When | Can Catch? |
|------|------|------------|
| Syntax Error | Before running | No (fix code) |
| Runtime Error | While running | Yes (try/catch) |
| Logic Error | While running | No (wrong results) |

---

## Lesson 2: Try/Catch/Finally

### Basic Try/Catch

```javascript
try {
 // Code that might fail
 const result = riskyOperation();
 console.log(result);
} catch (error) {
 // Handle the error
 console.error('Something went wrong:', error.message);
}
```

### The Finally Block

Runs whether success or failure:

```javascript
try {
 const data = await fetchData();
 displayData(data);
} catch (error) {
 showErrorMessage(error);
} finally {
 // Always runs
 hideLoadingSpinner();
}
```

### Error Object Properties

```javascript
try {
 throw new Error('Something failed');
} catch (error) {
 console.log(error.name); // "Error"
 console.log(error.message); // "Something failed"
 console.log(error.stack); // Stack trace
}
```

---

## Lesson 3: Throwing Errors

### Throw Statement

```javascript
function divide(a, b) {
 if (b === 0) {
 throw new Error('Cannot divide by zero');
 }
 return a / b;
}

try {
 const result = divide(10, 0);
} catch (error) {
 console.log(error.message); // "Cannot divide by zero"
}
```

### Throwing Different Types

```javascript
// Throw error object
throw new Error('Generic error');

// Throw specific error type
throw new TypeError('Expected a number');
throw new RangeError('Value out of range');

// Throw custom object
throw {
 code: 'VALIDATION_ERROR',
 message: 'Invalid email format',
 field: 'email'
};
```

### Re-throwing Errors

```javascript
try {
 processData();
} catch (error) {
 if (error.code === 'NETWORK_ERROR') {
 // Handle network error
 showOfflineMessage();
 } else {
 // Re-throw others
 throw error;
 }
}
```

---

## Lesson 4: Custom Error Classes

### Creating Custom Errors

```javascript
class ValidationError extends Error {
 constructor(message, field) {
 super(message);
 this.name = 'ValidationError';
 this.field = field;
 }
}

class NetworkError extends Error {
 constructor(message, statusCode) {
 super(message);
 this.name = 'NetworkError';
 this.statusCode = statusCode;
 }
}

// Usage
function validateEmail(email) {
 if (!email.includes('@')) {
 throw new ValidationError('Invalid email format', 'email');
 }
}

try {
 validateEmail('invalid-email');
} catch (error) {
 if (error instanceof ValidationError) {
 console.log(`Field ${error.field}: ${error.message}`);
 }
}
```

---

## Lesson 5: Async Error Handling

### With Promises

```javascript
fetchData()
 .then(data => process(data))
 .then(result => display(result))
 .catch(error => {
 // Catches error from any .then()
 console.error('Pipeline failed:', error);
 });
```

### With Async/Await

```javascript
async function loadData() {
 try {
 const response = await fetch(url);
 
 if (!response.ok) {
 throw new NetworkError('Request failed', response.status);
 }
 
 const data = await response.json();
 return data;
 } catch (error) {
 if (error instanceof NetworkError) {
 showNetworkError(error);
 } else {
 showGenericError(error);
 }
 throw error; // Re-throw if caller needs to know
 }
}
```

### Error Boundaries Pattern

```javascript
async function safeOperation(operation, fallback) {
 try {
 return await operation();
 } catch (error) {
 console.error('Operation failed:', error);
 return fallback;
 }
}

// Usage
const users = await safeOperation(
 () => fetchUsers(),
 [] // Fallback to empty array
);
```

---

## Lesson 6: Debugging Techniques

### Console Methods

```javascript
console.log('Basic message');
console.error('Error message');
console.warn('Warning message');
console.info('Info message');

// Table for arrays/objects
console.table([
 { name: 'Sokha', age: 22 },
 { name: 'Dara', age: 25 }
]);

// Grouping
console.group('User Details');
console.log('Name: Sokha');
console.log('Age: 22');
console.groupEnd();

// Timing
console.time('operation');
// ... code to measure
console.timeEnd('operation'); // operation: 123.45ms

// Counting
console.count('clicked'); // clicked: 1
console.count('clicked'); // clicked: 2

// Assert
console.assert(1 === 2, 'This will show because condition is false');
```

### Debugger Statement

```javascript
function calculateTotal(items) {
 let total = 0;
 
 for (const item of items) {
 debugger; // Browser pauses here
 total += item.price * item.quantity;
 }
 
 return total;
}
```

### Browser DevTools

- DEVTOOLS FEATURES
- CONSOLE TAB
- • View logs and errors
- • Execute JavaScript
- • Test expressions
- SOURCES TAB
- • Set breakpoints
- • Step through code
- • Watch variables
- • View call stack
- NETWORK TAB
- • See all requests
- • Check response data
- • Debug API calls
- ELEMENTS TAB
- • Inspect DOM
- • See computed styles
- • Debug layout

---

## Lesson 7: Best Practices

### Error Handling Patterns

```javascript
// 1. Always handle async errors
async function fetchData() {
 try {
 const data = await api.get('/data');
 return { success: true, data };
 } catch (error) {
 return { success: false, error: error.message };
 }
}

// 2. Provide user-friendly messages
function getUserMessage(error) {
 const messages = {
 NETWORK_ERROR: 'Please check your internet connection',
 NOT_FOUND: 'The requested item was not found',
 UNAUTHORIZED: 'Please log in to continue',
 DEFAULT: 'Something went wrong. Please try again.'
 };
 
 return messages[error.code] || messages.DEFAULT;
}

// 3. Log errors for debugging
function handleError(error, context) {
 console.error(`Error in ${context}:`, error);
 
 // In production, send to error tracking service
 if (window.errorTracker) {
 window.errorTracker.capture(error, { context });
 }
}

// 4. Fail gracefully
function renderData(data) {
 if (!data || !Array.isArray(data)) {
 return '<p>No data available</p>';
 }
 
 return data.map(item => `<div>${item.name}</div>`).join('');
}
```

### Debugging Checklist

```
□ Read the error message carefully
□ Check the line number in the stack trace
□ Verify variable values with console.log
□ Check for typos
□ Verify data types
□ Check API response format
□ Test with simple inputs first
□ Use browser DevTools breakpoints
□ Check network tab for failed requests
□ Google the exact error message
```

---

## Self-Check Exercises

### Exercise 1: Try/Catch Practice

Wrap a fetch call in try/catch with proper error handling.

### Exercise 2: Custom Error

Create a `AuthenticationError` class with properties for code and message.

### Exercise 3: Debug a Bug

Find and fix the bug:

```javascript
function sumArray(numbers) {
 let total;
 for (let i = 0; i <= numbers.length; i++) {
 total += numbers[i];
 }
 return total;
}
```

### Exercise 4: Error Boundary

Create a function that safely parses JSON with a fallback value.

### Exercise 5: Full Error Handling

Create a user registration form with:

- Validation errors
- Network error handling
- User-friendly error messages

---

## Module Summary

| Concept | Purpose |
|---------|---------|
| try/catch | Catch runtime errors |
| finally | Always execute cleanup |
| throw | Create errors intentionally |
| Custom errors | Specific error types |
| console | Debug output |
| debugger | Pause execution |

---

## Next Steps

**Coming Next**: Module 05 - Project: Weather Dashboard

*You will build a complete application using everything learned!*

---

<div align="center">

**Errors are information!** 

*Good error handling makes great apps.*

</div>
