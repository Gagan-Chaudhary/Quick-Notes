# JavaScript Comprehensive Guide

## 1. JavaScript Fundamentals

### What is JavaScript?

- High-level, interpreted programming language
- Supports multiple programming paradigms
- Used for client-side and server-side programming

### Basic Syntax

```javascript
// Variables
let name = "John";
const age = 30;
var isStudent = true;

// Functions
function greet(name) {
  return `Hello, ${name}!`;
}

// Arrow Functions
const multiply = (a, b) => a * b;
```

## 2. Advanced JavaScript Concepts

### Closures

```javascript
function outerFunction(x) {
  return function (y) {
    return x + y;
  };
}
```

### Promises

```javascript
const fetchData = () => {
  return new Promise((resolve, reject) => {
    // Async operation
  });
};
```

### Async/Await

```javascript
async function getData() {
  try {
    const response = await fetch("url");
    const data = await response.json();
    return data;
  } catch (error) {
    console.error(error);
  }
}
```

### ES6+ Features

- Destructuring
- Spread/Rest operators
- Template literals
- Modules
- Classes

## 3. Object-Oriented Programming

```javascript
class Person {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }

  introduce() {
    return `I'm ${this.name}`;
  }
}
```

## 4. Interview Questions

1. Explain hoisting

   - Variable and function declarations moved to top

2. What's the difference between `==` and `===`?

   - `==` loose equality (type coercion)
   - `===` strict equality (no type coercion)

3. Explain event loop and asynchronous programming

4. What are higher-order functions?
   - Functions that take or return functions

## 5. Best Practices

- Use strict mode
- Avoid global variables
- Use const/let instead of var
- Handle errors
- Write modular code
- Use meaningful variable names

## 6. Performance Optimization

- Use efficient algorithms
- Minimize DOM manipulation
- Implement lazy loading
- Use memoization
- Avoid memory leaks
