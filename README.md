# The Array `sort()` Method

---

## 1. Overview

The `sort()` method **sorts the elements of an array in place** and **returns the sorted array**.

* Default sort is **lexicographical** (like strings)
* Can provide a **compare function** for numeric or custom sorting
* **Original array is modified**

Syntax:

```js id="sort1"
array.sort((a, b) => {
  // return < 0 → a before b
  // return 0 → keep order
  // return > 0 → b before a
});
```

---

## 2. Sorting Strings

```js id="sort2"
const fruits = ["banana", "apple", "mango"];
fruits.sort();

console.log(fruits); // ["apple", "banana", "mango"]
```

* Default sort works well for **strings**

---

## 3. Sorting Numbers

```js id="sort3"
const numbers = [10, 5, 20, 1];
numbers.sort();

console.log(numbers); // [1, 10, 20, 5] ❌ unexpected
```

* Default sort treats numbers as strings → **not numeric**

### Correct Numeric Sort

```js id="sort4"
const numbers = [10, 5, 20, 1];
numbers.sort((a, b) => a - b);

console.log(numbers); // [1, 5, 10, 20]
```

* `a - b` → ascending
* `b - a` → descending

---

## 4. Sorting Objects

```js id="sort5"
const users = [
  { name: "Howard", age: 21 },
  { name: "Alice", age: 25 },
  { name: "Bob", age: 18 }
];

users.sort((a, b) => a.age - b.age);

console.log(users);
// [{ name: "Bob", age: 18 }, { name: "Howard", age: 21 }, { name: "Alice", age: 25 }]
```

* Sort by **object property** using a compare function

---

## 5. React Example: Rendering Sorted List

```jsx id="sort6"
const users = [
  { id: 1, name: "Howard", age: 21 },
  { id: 2, name: "Alice", age: 25 }
];

const UserList = () => (
  <ul>
    {users
      .sort((a, b) => a.name.localeCompare(b.name))
      .map(user => <li key={user.id}>{user.name}</li>)}
  </ul>
);
```

* Use `localeCompare` for **alphabetical sorting in strings**
* Combine with `map()` for React list rendering

---

## 6. Common Mistakes

* Not providing a compare function for numbers → gives **incorrect order**
* Forgetting that `sort()` **modifies the original array**

```js id="sort7"
// ❌
const numbers = [3, 1, 2];
const sorted = numbers.sort(); // numbers is modified
```

* To avoid modifying the original array, copy first:

```js id="sort8"
const numbers = [3, 1, 2];
const sorted = [...numbers].sort((a, b) => a - b);
```

---

## 7. Practice

```js id="sort9"
const numbers = [50, 10, 40, 20];

// Sort numbers ascending
```

Answer:

```js id="sort10"
const sortedNumbers = [...numbers].sort((a, b) => a - b);
console.log(sortedNumbers); // [10, 20, 40, 50]
```

---

## 8. Summary

* `sort()` **orders array elements** in place
* Default is **lexicographical** → bad for numbers
* Use **compare functions** for numeric or custom sorting
* Works with **numbers, strings, and objects**
* Combine with `map()` in React to render **sorted lists**

---

## Rule

Use `sort()` to **arrange array elements** as needed, and copy arrays first if you want to **avoid modifying the original**.

