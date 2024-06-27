# ALX Backend JavaScript - Promises

## Project Overview

This project focuses on mastering the use of Promises in JavaScript, a crucial concept for handling asynchronous operations. Each task introduces progressively complex scenarios, from simple promise creation to handling multiple promises and error management using `async`/`await`.

## Table of Contents

1. [Task 0: Keep every promise you make and only make promises you can keep](#task-0)
2. [Task 1: Don't make a promise...if you know you can't keep it](#task-1)
3. [Task 2: Catch me if you can!](#task-2)
4. [Task 3: Handle multiple successful promises](#task-3)
5. [Task 4: Simple promise](#task-4)
6. [Task 5: Reject the promises](#task-5)
7. [Task 6: Handle multiple promises](#task-6)
8. [Task 7: Load balancer](#task-7)
9. [Task 8: Throw error / try catch](#task-8)
10. [Task 9: Throw an error](#task-9)
11. [Task 10: Await / Async](#task-10)

## Task Details

### Task 0: Keep every promise you make and only make promises you can keep
- **Objective**: Implement a function `getResponseFromAPI` that returns a Promise.
- **File**: `0-promise.js`

### Task 1: Don't make a promise...if you know you can't keep it
- **Objective**: Implement `getFullResponseFromAPI(success)` which returns a promise.
  - Resolves with an object `{ status: 200, body: 'Success' }` if `success` is `true`.
  - Rejects with an error object `{ message: 'The fake API is not working currently' }` if `success` is `false`.
- **File**: `1-promise.js`

### Task 2: Catch me if you can!
- **Objective**: Implement `handleResponseFromAPI(promise)` to handle promise resolution and rejection.
  - On resolution, return `{ status: 200, body: 'success' }`.
  - On rejection, return an empty error object.
  - Log "Got a response from the API" for every resolution.
- **File**: `2-then.js`

### Task 3: Handle multiple successful promises
- **Objective**: Implement `handleProfileSignup` to resolve promises from `uploadPhoto` and `createUser`.
  - Log `body firstName lastName` on success.
  - Log "Signup system offline" on error.
- **File**: `3-all.js`

### Task 4: Simple promise
- **Objective**: Implement `signUpUser(firstName, lastName)` to return a resolved promise with the user object.
- **File**: `4-user-promise.js`

### Task 5: Reject the promises
- **Objective**: Implement `uploadPhoto(filename)` to return a rejected promise with an error message `$fileName cannot be processed`.
- **File**: `5-photo-reject.js`

### Task 6: Handle multiple promises
- **Objective**: Implement `handleProfileSignup(firstName, lastName, fileName)` to handle multiple promises.
  - Return an array with the promise results.
- **File**: `6-final-user.js`

### Task 7: Load balancer
- **Objective**: Implement `loadBalancer(chinaDownload, USDownload)` to return the result of the first resolved promise.
- **File**: `7-load_balancer.js`

### Task 8: Throw error / try catch
- **Objective**: Implement `divideFunction(numerator, denominator)` to handle division.
  - Throw an error if the denominator is `0`.
- **File**: `8-try.js`

### Task 9: Throw an error
- **Objective**: Implement `guardrail(mathFunction)` to manage errors and ensure a guardrail message.
- **File**: `9-try.js`

### Task 10: Await / Async
- **Objective**: Implement `asyncUploadUser` to call `uploadPhoto` and `createUser`, returning an object with their results.
  - Return an empty object if any function fails.
- **File**: `100-await.js`

## Repository Structure

```plaintext
alx-backend-javascript/
└── 0x01-ES6_promise/
    ├── 0-promise.js
    ├── 1-promise.js
    ├── 2-then.js
    ├── 3-all.js
    ├── 4-user-promise.js
    ├── 5-photo-reject.js
    ├── 6-final-user.js
    ├── 7-load_balancer.js
    ├── 8-try.js
    ├── 9-try.js
    └── 100-await.js
```

## Getting Started

1. **Clone the repository**:
   ```bash
   git clone https://github.com/<your-username>/alx-backend-javascript.git
   ```
2. **Navigate to the project directory**:
   ```bash
   cd alx-backend-javascript/0x01-ES6_promise
   ```
3. **Install dependencies**:
   ```bash
   npm install
   ```
4. **Run the tasks**:
   ```bash
   npm run dev <task-file.js>
   ```

## Contributing

1. Fork the repository.
2. Create a new branch (`git checkout -b feature-branch`).
3. Commit your changes (`git commit -am 'Add new feature'`).
4. Push to the branch (`git push origin feature-branch`).
5. Create a new Pull Request.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.