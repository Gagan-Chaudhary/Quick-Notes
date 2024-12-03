# React.js Comprehensive Guide

## 1. React Fundamentals

### What is React?

- JavaScript library for building user interfaces
- Component-based architecture
- Virtual DOM for efficient rendering

### Basic Component

```jsx
import React from "react";

function Greeting(props) {
  return <h1>Hello, {props.name}</h1>;
}
```

### Class Components

```jsx
class Counter extends React.Component {
  constructor(props) {
    super(props);
    this.state = { count: 0 };
  }

  render() {
    return (
      <div>
        <p>Count: {this.state.count}</p>
        <button onClick={() => this.setState({ count: this.state.count + 1 })}>
          Increment
        </button>
      </div>
    );
  }
}
```

## 2. Functional Components & Hooks

### useState

```jsx
import React, { useState } from "react";

function Example() {
  const [count, setCount] = useState(0);
  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => setCount(count + 1)}>Increment</button>
    </div>
  );
}
```

### useEffect

```jsx
import React, { useState, useEffect } from "react";

function DataFetcher() {
  const [data, setData] = useState(null);

  useEffect(() => {
    fetch("https://api.example.com/data")
      .then((response) => response.json())
      .then((data) => setData(data));
  }, []); // Empty dependency array means run once

  return <div>{data ? JSON.stringify(data) : "Loading..."}</div>;
}
```

### Custom Hooks

```jsx
function useLocalStorage(key, initialValue) {
  const [storedValue, setStoredValue] = useState(() => {
    try {
      const item = window.localStorage.getItem(key);
      return item ? JSON.parse(item) : initialValue;
    } catch (error) {
      return initialValue;
    }
  });

  const setValue = (value) => {
    setStoredValue(value);
    window.localStorage.setItem(key, JSON.stringify(value));
  };

  return [storedValue, setValue];
}
```

## 3. State Management

### Redux Basics

```jsx
// Action
const increment = () => ({ type: "INCREMENT" });

// Reducer
function counterReducer(state = { count: 0 }, action) {
  switch (action.type) {
    case "INCREMENT":
      return { count: state.count + 1 };
    default:
      return state;
  }
}
```

### Context API

```jsx
const ThemeContext = React.createContext("light");

function App() {
  return (
    <ThemeContext.Provider value="dark">
      <Toolbar />
    </ThemeContext.Provider>
  );
}
```

## 4. Performance Optimization

- Use React.memo()
- Implement shouldComponentUpdate
- Code splitting
- Lazy loading
- Memoize expensive computations

## 5. Interview Questions

1. Controlled vs Uncontrolled Components
2. Differences between props and state
3. What is reconciliation?
4. Explain React Fiber
5. How do you prevent unnecessary re-renders?

## 6. Best Practices

- Keep components small
- Use functional components
- Lift state up
- Avoid prop drilling
- Use prop types
- Follow single responsibility principle
