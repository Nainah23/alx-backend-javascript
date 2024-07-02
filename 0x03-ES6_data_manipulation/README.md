```markdown
# ALX Backend JavaScript: ES6 Data Manipulation

This repository contains a series of tasks focused on data manipulation using ES6 features in JavaScript. Below is a brief overview of each task and its purpose.

## Table of Contents
1. [Basic List of Objects](#basic-list-of-objects)
2. [More Mapping](#more-mapping)
3. [Filter](#filter)
4. [Reduce](#reduce)
5. [Combine](#combine)
6. [Typed Arrays](#typed-arrays)
7. [Set Data Structure](#set-data-structure)
8. [More Set Data Structure](#more-set-data-structure)
9. [Clean Set](#clean-set)
10. [Map Data Structure](#map-data-structure)
11. [More Map Data Structure](#more-map-data-structure)
12. [Weak Link Data Structure](#weak-link-data-structure)

## Basic List of Objects

Create a function named `getListStudents` that returns an array of objects. Each object should have three attributes: `id` (Number), `firstName` (String), and `location` (String).

- **File:** `0-get_list_students.js`

```javascript
export default function getListStudents() {
  return [
    { id: 1, firstName: 'Guillaume', location: 'San Francisco' },
    { id: 2, firstName: 'James', location: 'Columbia' },
    { id: 5, firstName: 'Serena', location: 'San Francisco' }
  ];
}
```

## More Mapping

Create a function `getListStudentIds` that returns an array of ids from a list of objects. This function takes one argument which is an array of objects in the same format as `getListStudents` from the previous task.

- **File:** `1-get_list_student_ids.js`

```javascript
export default function getListStudentIds(students) {
  if (!Array.isArray(students)) return [];
  return students.map(student => student.id);
}
```

## Filter

Create a function `getStudentsByLocation` that returns an array of objects who are located in a specific city. It should accept a list of students (from `getListStudents`) and a city (string) as parameters.

- **File:** `2-get_students_by_loc.js`

```javascript
export default function getStudentsByLocation(students, city) {
  return students.filter(student => student.location === city);
}
```

## Reduce

Create a function `getStudentIdsSum` that returns the sum of all the student ids. It should accept a list of students (from `getListStudents`) as a parameter.

- **File:** `3-get_ids_sum.js`

```javascript
export default function getStudentIdsSum(students) {
  return students.reduce((sum, student) => sum + student.id, 0);
}
```

## Combine

Create a function `updateStudentGradeByCity` that returns an array of students for a specific city with their new grades. It should accept a list of students (from `getListStudents`), a city (String), and `newGrades` (Array of "grade" objects) as parameters.

- **File:** `4-update_grade_by_city.js`

```javascript
export default function updateStudentGradeByCity(students, city, newGrades) {
  return students
    .filter(student => student.location === city)
    .map(student => {
      const gradeObj = newGrades.find(grade => grade.studentId === student.id);
      return { ...student, grade: gradeObj ? gradeObj.grade : 'N/A' };
    });
}
```

## Typed Arrays

Create a function named `createInt8TypedArray` that returns a new `ArrayBuffer` with an `Int8` value at a specific position. It should accept three arguments: `length` (Number), `position` (Number), and `value` (Number).

- **File:** `5-typed_arrays.js`

```javascript
export default function createInt8TypedArray(length, position, value) {
  const buffer = new ArrayBuffer(length);
  const view = new DataView(buffer);
  if (position >= length) {
    throw new Error('Position outside range');
  }
  view.setInt8(position, value);
  return view;
}
```

## Set Data Structure

Create a function named `setFromArray` that returns a `Set` from an array. It accepts an argument (Array) of any kind of element.

- **File:** `6-set.js`

```javascript
export default function setFromArray(array) {
  return new Set(array);
}
```

## More Set Data Structure

Create a function named `hasValuesFromArray` that returns a boolean if all the elements in the array exist within the set. It accepts two arguments: a set (Set) and an array (Array).

- **File:** `7-has_array_values.js`

```javascript
export default function hasValuesFromArray(set, array) {
  return array.every(value => set.has(value));
}
```

## Clean Set

Create a function named `cleanSet` that returns a string of all the set values that start with a specific string (`startString`). It accepts two arguments: a set (Set) and a `startString` (String).

- **File:** `8-clean_set.js`

```javascript
export default function cleanSet(set, startString) {
  if (startString === '' || startString === undefined) return '';
  let result = '';
  set.forEach(value => {
    if (value.startsWith(startString)) {
      result += `${value.slice(startString.length)}-`;
    }
  });
  return result.slice(0, -1);
}
```

## Map Data Structure

Create a function named `groceriesList` that returns a map of groceries with the following items (name, quantity):
- Apples, 10
- Tomatoes, 10
- Pasta, 1
- Rice, 1
- Banana, 5

- **File:** `9-groceries_list.js`

```javascript
export default function groceriesList() {
  const groceries = new Map();
  groceries.set('Apples', 10);
  groceries.set('Tomatoes', 10);
  groceries.set('Pasta', 1);
  groceries.set('Rice', 1);
  groceries.set('Banana', 5);
  return groceries;
}
```

## More Map Data Structure

Create a function named `updateUniqueItems` that returns an updated map for all items with an initial quantity of 1. It should accept a map as an argument. For each entry of the map where the quantity is 1, update the quantity to 100. If the argument is not a map, the error `Cannot process` should be thrown.

- **File:** `10-update_uniq_items.js`

```javascript
export default function updateUniqueItems(groceries) {
  if (!(groceries instanceof Map)) {
    throw new Error('Cannot process');
  }
  groceries.forEach((value, key) => {
    if (value === 1) {
      groceries.set(key, 100);
    }
  });
  return groceries;
}
```

## Weak Link Data Structure

Export a constant instance of `WeakMap` and name it `weakMap`. Export a new function named `queryAPI` that accepts an endpoint argument. Track within the `weakMap` the number of times `queryAPI` is called for each endpoint. When the number of queries is >= 5, throw an error with the message `Endpoint load is high`.

- **File:** `100-weak.js`

```javascript
export const weakMap = new WeakMap();

export function queryAPI(endpoint) {
  const count = weakMap.get(endpoint) || 0;
  if (count >= 4) {
    throw new Error('Endpoint load is high');
  }
  weakMap.set(endpoint, count + 1);
}
```

## License

This project is licensed under the MIT License.
```

This `README.md` provides a clear and concise description of each task, the purpose of the function, the file in which it is located, and the respective code snippet to achieve the desired functionality.