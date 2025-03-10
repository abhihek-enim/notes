# MERN Stack Session Management with Redis

## 📌 Introduction

This project demonstrates how to implement **session management** in a **MERN stack** application using **Redis**. Sessions are stored in Redis instead of memory, ensuring better scalability, persistence, and performance.

## 🚀 Features

- **User Authentication (Login/Logout)**
- **Session Persistence with Redis**
- **Protected Routes**
- **Scalable & Secure Session Storage**

---

## 📂 Folder Structure

```
/mern-app
│── /backend
│   ├── /config                # Configuration files (DB, Redis, etc.)
│   │   ├── db.js              # MongoDB connection
│   │   ├── redis.js           # Redis connection
│   ├── /middlewares           # Express middlewares
│   │   ├── sessionMiddleware.js # Redis session config
│   ├── /routes                # API routes
│   │   ├── authRoutes.js       # Authentication routes (login/logout)
│   │   ├── protectedRoutes.js  # Example of protected endpoints
│   ├── /controllers           # Business logic for authentication
│   │   ├── authController.js   # Login/logout/session handling
│   ├── /models                # Mongoose models
│   │   ├── userModel.js        # User schema
│   ├── /utils                 # Utility functions (e.g., session helpers)
│   │   ├── sessionUtils.js     # Helper functions for session management
│   ├── server.js              # Main Express app file
│   ├── .env                   # Environment variables
│   ├── package.json           # Dependencies and scripts
│── /frontend                  # React frontend (if needed)
│   ├── /src
│   │   ├── /components        # React components
│   │   ├── /pages             # React pages (Login, Dashboard)
│   │   ├── App.js             # Main entry file
│   │   ├── index.js           # ReactDOM rendering
│── README.md                  # Documentation
```

---

## 🛠 Installation & Setup

### 1️⃣ Install Dependencies

Inside the **backend** folder, run:

```sh
npm install express express-session connect-redis ioredis redis mongoose dotenv cors
```

### 2️⃣ Configure Redis Connection (`/config/redis.js`)

```javascript
const Redis = require("ioredis");

const redisClient = new Redis({
  host: "127.0.0.1",  // Change for production
  port: 6379,         // Default Redis port
  password: process.env.REDIS_PASSWORD || "", // Optional password
});

redisClient.on("connect", () => console.log("✅ Connected to Redis"));
redisClient.on("error", (err) => console.error("❌ Redis Error:", err));

module.exports = redisClient;
```

### 3️⃣ Set Up Express Session Middleware (`/middlewares/sessionMiddleware.js`)

```javascript
const session = require("express-session");
const RedisStore = require("connect-redis").default;
const redisClient = require("../config/redis");

const sessionMiddleware = session({
  store: new RedisStore({ client: redisClient }),
  secret: process.env.SESSION_SECRET || "supersecretkey",
  resave: false,
  saveUninitialized: false,
  cookie: {
    secure: process.env.NODE_ENV === "production",  // Enable in production
    httpOnly: true,   // Prevent XSS attacks
    maxAge: 1000 * 60 * 60 * 24,  // 24 hours session expiry
  },
});

module.exports = sessionMiddleware;
```

### 4️⃣ Authentication Routes (`/routes/authRoutes.js`)

```javascript
const express = require("express");
const { login, logout } = require("../controllers/authController");

const router = express.Router();

router.post("/login", login);
router.post("/logout", logout);

module.exports = router;
```

### 5️⃣ Implement Authentication Logic (`/controllers/authController.js`)

```javascript
const login = (req, res) => {
  const { username } = req.body;

  if (!username) {
    return res.status(400).json({ error: "Username is required" });
  }

  req.session.user = { username };
  res.json({ message: `Welcome, ${username}!` });
};

const logout = (req, res) => {
  req.session.destroy((err) => {
    if (err) return res.status(500).json({ error: "Logout failed" });

    res.clearCookie("connect.sid");
    res.json({ message: "Logged out successfully" });
  });
};

module.exports = { login, logout };
```

### 6️⃣ Secure Protected Routes (`/routes/protectedRoutes.js`)

```javascript
const express = require("express");
const router = express.Router();

const isAuthenticated = (req, res, next) => {
  if (!req.session.user) {
    return res.status(401).json({ error: "Unauthorized" });
  }
  next();
};

router.get("/dashboard", isAuthenticated, (req, res) => {
  res.json({ message: `Welcome ${req.session.user.username}` });
});

module.exports = router;
```

### 7️⃣ Configure Express App (`server.js`)

```javascript
require("dotenv").config();
const express = require("express");
const cors = require("cors");
const sessionMiddleware = require("./middlewares/sessionMiddleware");
const authRoutes = require("./routes/authRoutes");
const protectedRoutes = require("./routes/protectedRoutes");

const app = express();

app.use(express.json());
app.use(cors({ credentials: true, origin: "http://localhost:3000" }));
app.use(sessionMiddleware);

app.use("/auth", authRoutes);
app.use("/api", protectedRoutes);

const PORT = process.env.PORT || 5000;
app.listen(PORT, () => console.log(`🚀 Server running on port ${PORT}`));
```

---

## 🛑 Common Issues & Solutions

### 🚨 1️⃣ Redis Connection Fails

Run the following command to check Redis status:

```sh
redis-cli ping
```

If Redis is not running, start it:

```sh
redis-server
```

### 🚨 2️⃣ Sessions Reset After Restart

Enable Redis persistence:

```sh
redis-cli config set save 60 1
```

### 🚨 3️⃣ Load Balancing Issues

Use a **centralized Redis instance** instead of storing sessions in memory.

### 🚨 4️⃣ Security Concerns

- Use **HTTPS (**``**)** in production.
- Set **httpOnly: true** to prevent client-side access.
- Rotate session IDs after login.

---

## ✅ Summary

By integrating Redis with **Express-session**, we achieve **efficient session storage** in a **scalable and secure** way. 🚀

### **Next Steps**

Would you like to implement **role-based access control (RBAC)** or **JWT fallback for stateless sessions?** 🔐

