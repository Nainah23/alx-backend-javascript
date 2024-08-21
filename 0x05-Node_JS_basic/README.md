---

# ALX Backend JavaScript - Node.js Basics

This repository contains basic Node.js tasks designed to introduce core concepts and functionalities. The tasks range from basic JavaScript execution using Node.js to creating HTTP servers with Node's `http` module and Express.

## Table of Contents

1. [Task 0: Executing Basic JavaScript with Node.js](#task-0-executing-basic-javascript-with-nodejs)
2. [Task 1: Using Process stdin](#task-1-using-process-stdin)
3. [Task 2: Reading a File Synchronously](#task-2-reading-a-file-synchronously)
4. [Task 3: Reading a File Asynchronously](#task-3-reading-a-file-asynchronously)
5. [Task 4: Creating a Simple HTTP Server](#task-4-creating-a-simple-http-server)
6. [Task 5: Creating a Complex HTTP Server](#task-5-creating-a-complex-http-server)
7. [Task 6: Creating an HTTP Server with Express](#task-6-creating-an-http-server-with-express)
8. [Task 7: Creating a Complex HTTP Server with Express](#task-7-creating-a-complex-http-server-with-express)
9. [Task 8: Organizing a Complex HTTP Server](#task-8-organizing-a-complex-http-server)

## Task 0: Executing Basic JavaScript with Node.js

**File:** `0-console.js`

- Implements `displayMessage` function that prints a string argument to STDOUT.

### Usage
```bash
node 0-main.js
```

## Task 1: Using Process stdin

**File:** `1-stdin.js`

- Creates a program that interacts with user input via command line.

### Usage
```bash
node 1-stdin.js
```

## Task 2: Reading a File Synchronously

**File:** `2-read_file.js`

- Implements `countStudents` function to read a CSV file synchronously and output student data.

### Usage
```bash
node 2-main_1.js
```

## Task 3: Reading a File Asynchronously

**File:** `3-read_file_async.js`

- Implements `countStudents` function to read a CSV file asynchronously and return a Promise.

### Usage
```bash
node 3-main_1.js
```

## Task 4: Creating a Simple HTTP Server

**File:** `4-http.js`

- Creates an HTTP server that responds with "Hello Holberton School!" for any endpoint.

### Usage
```bash
node 4-http.js
curl localhost:1245
```

## Task 5: Creating a Complex HTTP Server

**File:** `5-http.js`

- Extends the HTTP server to handle two endpoints:
  - `/` - Responds with "Hello Holberton School!"
  - `/students` - Responds with a list of students based on the provided CSV database.

### Usage
```bash
node 5-http.js database.csv
curl localhost:1245/students
```

## Task 6: Creating an HTTP Server with Express

**File:** `6-http_express.js`

- Creates a simple HTTP server using Express that responds with "Hello Holberton School!" for the `/` endpoint.

### Usage
```bash
node 6-http_express.js
curl localhost:1245
```

## Task 7: Creating a Complex HTTP Server with Express

**File:** `7-http_express.js`

- Recreates the server from Task 5 using Express, with routes `/` and `/students`.

### Usage
```bash
node 7-http_express.js database.csv
curl localhost:1245/students
```

## Task 8: Organizing a Complex HTTP Server

**Directory:** `full_server/`

- Organizes the complex HTTP server into a proper directory structure with controllers, routes, and utilities.
- Uses `babel-node` for ES6 features.

### File Structure
```
full_server/
├── controllers/
│   ├── AppController.js
│   └── StudentsController.js
├── routes/
│   └── index.js
├── utils.js
└── server.js
```

### Usage
```bash
npm run dev
curl localhost:1245/students
```

---
