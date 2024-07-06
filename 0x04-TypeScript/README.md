# ALX Backend JavaScript

This repository contains various TypeScript tasks for the ALX Backend JavaScript course.

## Table of Contents

- [Tasks](#tasks)
  - [Task 0: Creating an Interface for a Student](#task-0-creating-an-interface-for-a-student)
  - [Task 1: Let's Build a Teacher Interface](#task-1-lets-build-a-teacher-interface)
  - [Task 2: Extending the Teacher Interface](#task-2-extending-the-teacher-interface)
  - [Task 3: Printing Teachers](#task-3-printing-teachers)
  - [Task 4: Writing a Class](#task-4-writing-a-class)
  - [Task 5: Advanced Types Part 1](#task-5-advanced-types-part-1)
  - [Task 6: Creating Functions Specific to Employees](#task-6-creating-functions-specific-to-employees)
  - [Task 7: String Literal Types](#task-7-string-literal-types)
  - [Task 8: Ambient Namespaces](#task-8-ambient-namespaces)
  - [Task 9: Namespace & Declaration Merging](#task-9-namespace--declaration-merging)
  - [Task 10: Update `task_4/js/main.ts`](#task-10-update-task_4jsmain.ts)
  - [Task 11: Brand Convention & Nominal Typing](#task-11-brand-convention--nominal-typing)

## Tasks

### Task 0: Creating an Interface for a Student

**Directory:** `0x04-TypeScript/task_0`

1. Copy the configuration files (`package.json`, `.eslintrc.js`, `tsconfig.json`, `webpack.config.js`) into `task_0`.
2. Write an interface named `Student` in `main.ts` that includes:
   - `firstName` (string)
   - `lastName` (string)
   - `age` (number)
   - `location` (string)
3. Create two students and an array `studentsList` containing them.
4. Render a table using Vanilla JavaScript that lists the first name and location of each student.

### Task 1: Let's Build a Teacher Interface

**Directory:** `0x04-TypeScript/task_1`

1. Copy the configuration files (`package.json`, `tsconfig.json`, `webpack.config.js`) into `task_1`.
2. Write an interface named `Teacher` in `main.ts` that includes:
   - `firstName` (string) - only modifiable at initialization
   - `lastName` (string) - only modifiable at initialization
   - `fullTimeEmployee` (boolean) - always defined
   - `yearsOfExperience` (number) - optional
   - `location` (string) - always defined
3. Allow additional attributes to be added to the `Teacher` object dynamically.

### Task 2: Extending the Teacher Interface

**Directory:** `0x04-TypeScript/task_1`

1. Extend the `Teacher` interface to create an interface named `Directors` in `main.ts`.
2. `Directors` includes a required attribute `numberOfReports` (number).

### Task 3: Printing Teachers

**Directory:** `0x04-TypeScript/task_1`

1. Write a function `printTeacher` in `main.ts`:
   - Accepts `firstName` and `lastName` as arguments.
   - Returns the first letter of `firstName` and the full `lastName`.
2. Create an interface `printTeacherFunction` for the function.

### Task 4: Writing a Class

**Directory:** `0x04-TypeScript/task_1`

1. Write a class `StudentClass` in `main.ts` with:
   - A constructor that accepts `firstName` and `lastName` (both strings).
   - A method `workOnHomework` that returns "Currently working".
   - A method `displayName` that returns the student's `firstName`.

### Task 5: Advanced Types Part 1

**Directory:** `0x04-TypeScript/task_2`

1. Create interfaces `DirectorInterface` and `TeacherInterface` with methods:
   - `workFromHome()` returns a string.
   - `getCoffeeBreak()` returns a string.
   - `workDirectorTasks()` / `workTeacherTasks()` returns a string.
2. Create classes `Director` and `Teacher` implementing these interfaces.
3. Write a function `createEmployee` that returns either a `Director` or a `Teacher` based on the salary argument.

### Task 6: Creating Functions Specific to Employees

**Directory:** `0x04-TypeScript/task_2`

1. Write a function `isDirector` that acts as a type predicate.
2. Write a function `executeWork` that calls the appropriate method based on the employee type.

### Task 7: String Literal Types

**Directory:** `0x04-TypeScript/task_2`

1. Create a string literal type `Subjects` allowing values `Math` or `History`.
2. Write a function `teachClass` that returns different strings based on the subject.

### Task 8: Ambient Namespaces

**Directory:** `0x04-TypeScript/task_3`

1. Create an interface `RowElement` and a type `RowID` in `interface.ts`.
2. Write an ambient declaration file `crud.d.ts` for `crud.js`.
3. In `main.ts`, utilize `crud.js` functions and ensure TypeScript recognizes the types.

### Task 9: Namespace & Declaration Merging

**Directory:** `0x04-TypeScript/task_4`

1. Create a namespace `Subjects` in multiple files and use declaration merging to add attributes to the `Teacher` interface.
2. Create classes `Cpp`, `Java`, and `React` extending `Subject`, each with specific methods.

### Task 10: Update `task_4/js/main.ts`

**Directory:** `0x04-TypeScript/task_4`

1. Create and export constants for `Cpp`, `Java`, and `React` subjects.
2. Create a `Teacher` object and use it in each subject's methods, logging the results.

### Task 11: Brand Convention & Nominal Typing

**Directory:** `0x04-TypeScript/task_5`

1. Create interfaces `MajorCredits` and `MinorCredits` with a unique `brand` property.
2. Write functions `sumMajorCredits` and `sumMinorCredits` that sum credits of the respective types.

---

To run any of the tasks, navigate to the respective directory and run:

```sh
npm install
npm run build
```

Ensure you have TypeScript and the required dependencies installed. For any TypeScript errors, check the `tsconfig.json` and the interfaces or classes defined within the task.