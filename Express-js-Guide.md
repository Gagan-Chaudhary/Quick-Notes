# Express.js Comprehensive Guide

## 1. Express.js Fundamentals

### What is Express.js?

- Web application framework for Node.js
- Provides robust features for web and mobile applications
- Simplifies routing and middleware integration

### Basic Server

```javascript
const express = require("express");
const app = express();
const port = 3000;

app.get("/", (req, res) => {
  res.send("Hello World!");
});

app.listen(port, () => {
  console.log(`Server running on port ${port}`);
});
```

## 2. Routing

```javascript
// Basic Routes
app.get("/users", (req, res) => {
  res.json([{ id: 1, name: "John" }]);
});

// Route with parameters
app.get("/users/:id", (req, res) => {
  const userId = req.params.id;
  res.send(`User ID: ${userId}`);
});

// POST route
app.post("/users", (req, res) => {
  const newUser = req.body;
  res.status(201).json(newUser);
});

// Multiple HTTP methods
app
  .route("/book")
  .get((req, res) => {
    res.send("Get a book");
  })
  .post((req, res) => {
    res.send("Add a book");
  })
  .put((req, res) => {
    res.send("Update a book");
  });
```

## 3. Middleware

```javascript
// Built-in middleware
app.use(express.json()); // Parse JSON bodies
app.use(express.urlencoded({ extended: true })); // Parse URL-encoded bodies

// Custom middleware
const loggerMiddleware = (req, res, next) => {
  console.log(`${req.method} ${req.url}`);
  next(); // Continue to next middleware/route handler
};
app.use(loggerMiddleware);

// Error handling middleware
app.use((err, req, res, next) => {
  console.error(err.stack);
  res.status(500).send("Something broke!");
});
```

## 4. Router

```javascript
// Modular routing
const express = require("express");
const router = express.Router();

router.get("/profile", (req, res) => {
  res.send("User Profile");
});

router.get("/settings", (req, res) => {
  res.send("User Settings");
});

app.use("/user", router);
```

## 5. Template Engines

```javascript
// Using EJS as template engine
app.set("view engine", "ejs");

app.get("/", (req, res) => {
  res.render("index", {
    title: "Home Page",
    message: "Welcome!",
  });
});
```

## 6. Authentication

```javascript
const passport = require("passport");
const jwt = require("jsonwebtoken");

app.post("/login", (req, res) => {
  // Authenticate user
  const token = jwt.sign({ id: user.id }, process.env.JWT_SECRET, {
    expiresIn: "1h",
  });
  res.json({ token });
});

// Protected route
const authenticateToken = (req, res, next) => {
  const authHeader = req.headers["authorization"];
  const token = authHeader && authHeader.split(" ")[1];

  if (token == null) return res.sendStatus(401);

  jwt.verify(token, process.env.JWT_SECRET, (err, user) => {
    if (err) return res.sendStatus(403);
    req.user = user;
    next();
  });
};

app.get("/protected", authenticateToken, (req, res) => {
  res.json({ message: "Access granted" });
});
```

## 7. Error Handling

```javascript
// Centralized error handling
class AppError extends Error {
  constructor(message, statusCode) {
    super(message);
    this.statusCode = statusCode;
  }
}

app.use((err, req, res, next) => {
  const { statusCode = 500 } = err;
  if (!err.message) err.message = "Something went wrong";
  res.status(statusCode).json({
    error: {
      message: err.message,
    },
  });
});
```

## 8. Database Integration

```javascript
const mongoose = require("mongoose");

// MongoDB connection
mongoose.connect("mongodb://localhost/myapp", {
  useNewUrlParser: true,
  useUnifiedTopology: true,
});

// Mongoose model
const User = mongoose.model("User", {
  username: String,
  email: String,
});

// Route with database interaction
app.get("/users", async (req, res) => {
  try {
    const users = await User.find();
    res.json(users);
  } catch (error) {
    res.status(500).json({ message: error.message });
  }
});
```

## 9. Performance Optimization

- Use compression middleware
- Implement caching
- Use load balancing
- Optimize database queries
- Use connection pooling

## 10. Interview Questions

1. What is middleware in Express?

   - Functions that have access to request/response cycle
   - Can modify req/res objects
   - Can end request-response cycle

2. Differences between `app.use()` and `app.get()`

   - `app.use()`: Works for all HTTP methods
   - `app.get()`: Specific to GET requests

3. How do you handle async errors in Express?

   - Use try-catch with async/await
   - Use error-handling middleware
   - Utilize express-async-errors package

4. Explain routing in Express

   - Defining how an application responds to client requests
   - Matching URL patterns to specific handlers

5. What are the key features of Express.js?
   - Robust routing
   - Focus on high performance
   - Minimalist framework
   - Supports multiple middleware

## 11. Best Practices

- Use environment variables
- Implement proper error handling
- Validate input data
- Use security middleware
- Keep routes modular
- Implement logging
- Use async/await for async operations
- Secure your application against common web vulnerabilities
