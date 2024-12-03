# Node.js Comprehensive Guide

## 1. Node.js Fundamentals

### What is Node.js?

- JavaScript runtime built on Chrome's V8 engine
- Event-driven, non-blocking I/O model
- Perfect for building scalable network applications

### Basic Server

```javascript
const http = require("http");

const server = http.createServer((req, res) => {
  res.statusCode = 200;
  res.setHeader("Content-Type", "text/plain");
  res.end("Hello World");
});

server.listen(3000, () => {
  console.log("Server running on port 3000");
});
```

## 2. Module System

```javascript
// Exporting
module.exports = {
  add: (a, b) => a + b,
  subtract: (a, b) => a - b,
};

// Importing
const math = require("./math");
console.log(math.add(5, 3));
```

## 3. Asynchronous Programming

### Callbacks

```javascript
function fetchData(callback) {
  setTimeout(() => {
    callback(null, "Data fetched");
  }, 1000);
}

fetchData((error, data) => {
  if (error) {
    console.error(error);
  } else {
    console.log(data);
  }
});
```

### Promises

```javascript
function fetchData() {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve("Data fetched");
    }, 1000);
  });
}

fetchData()
  .then((data) => console.log(data))
  .catch((error) => console.error(error));
```

### Async/Await

```javascript
async function getData() {
  try {
    const data = await fetchData();
    console.log(data);
  } catch (error) {
    console.error(error);
  }
}
```

## 4. npm and Package Management

```bash
# Initialize project
npm init

# Install package
npm install express

# Install dev dependency
npm install --save-dev nodemon
```

## 5. File System Operations

```javascript
const fs = require("fs").promises;

async function readFile() {
  try {
    const data = await fs.readFile("example.txt", "utf8");
    console.log(data);
  } catch (error) {
    console.error(error);
  }
}
```

## 6. Streams

```javascript
const fs = require("fs");

const readStream = fs.createReadStream("large-file.txt");
const writeStream = fs.createWriteStream("destination.txt");

readStream.pipe(writeStream);
```

## 7. Error Handling

```javascript
process.on("uncaughtException", (error) => {
  console.error("Uncaught Exception:", error);
  // Perform cleanup and exit
  process.exit(1);
});
```

## 8. Performance Optimization

- Use clustering
- Implement caching
- Use worker threads
- Optimize database queries
- Use connection pooling

## 9. Interview Questions

1. What is the event loop?
2. Explain Node.js architecture
3. Differences between `process.nextTick()` and `setImmediate()`
4. How does Node.js handle concurrency?
5. What are streams in Node.js?

## 10. Best Practices

- Use async/await
- Handle errors properly
- Use environment variables
- Implement logging
- Write modular code
- Use middleware
