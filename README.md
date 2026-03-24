# The Array `map()` Method

---

## 1. Overview

The `map()` method **creates a new array** by applying a function to each element of an existing array.

* Original array **is not modified**
* Very common in React for **rendering lists**

Syntax:

```js id="map1"
const newArray = array.map((element, index) => {
  // return new value
});
```

* `element` → current item
* `index` → current item’s position (optional)
* Function returns the **new element**

---

## 2. Basic Example

```js id="map2"
const numbers = [1, 2, 3];
const doubled = numbers.map(n => n * 2);

console.log(doubled); // [2, 4, 6]
```

* Original `numbers` array stays `[1, 2, 3]`

---

## 3. Using Index

```js id="map3"
const fruits = ["apple", "banana", "mango"];
const fruitList = fruits.map((fruit, i) => `${i + 1}. ${fruit}`);

console.log(fruitList);
// ["1. apple", "2. banana", "3. mango"]
```

* Index is useful for **numbering** or as **React keys**

---

## 4. Objects in Array

```js id="map4"
const users = [
  { name: "Howard", age: 21 },
  { name: "Alice", age: 25 }
];

const names = users.map(user => user.name);

console.log(names); // ["Howard", "Alice"]
```

* Extract specific properties from objects

---

## 5. React Example: Rendering Lists

```jsx id="map5"
const users = [
  { id: 1, name: "Howard" },
  { id: 2, name: "Alice" }
];

const UserList = () => (
  <ul>
    {users.map(user => (
      <li key={user.id}>{user.name}</li>
    ))}
  </ul>
);
```

* Always provide a **unique `key`** for list items in React

---

## 6. Chaining with Other Methods

```js id="map6"
const numbers = [1, 2, 3, 4, 5];

const doubledEven = numbers
  .filter(n => n % 2 === 0)
  .map(n => n * 2);

console.log(doubledEven); // [4, 8]
```

* Combine with `filter()`, `sort()`, etc.

---

## 7. Common Mistakes

* Forgetting to **return** a value in a multi-line function:

```js id="map7"
// ❌ Wrong
const numbers = [1,2,3];
const doubled = numbers.map(n => { n * 2 }); // undefined

// ✅ Correct
const doubledCorrect = numbers.map(n => { return n * 2 });
```

* Using `map()` when you just want **side-effects** → use `forEach()` instead

---

## 8. Practice

```js id="map8"
const numbers = [1, 2, 3, 4, 5];

// Use map to create an array of strings: "Number: X"
```

Answer:

```js id="map9"
const numberStrings = numbers.map(n => `Number: ${n}`);
console.log(numberStrings); 
// ["Number: 1", "Number: 2", "Number: 3", "Number: 4", "Number: 5"]
```

---

## 9. Summary

* `map()` transforms each element in an array **without modifying the original**
* Can work with numbers, strings, or objects
* In React, commonly used to **render dynamic lists**
* Remember to **return** a value and use **keys for JSX lists**

---

## Rule

Use `map()` to **create a new array** based on the old one or **render lists** in React.
