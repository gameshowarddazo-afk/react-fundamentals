# Working with Immutable Arrays

---

## 1. Overview

In React, **immutability is important**.

* Avoid modifying the original array directly
* Use **methods that return a new array** instead of mutating the old one

Common **mutable methods**: `push`, `pop`, `splice`, `sort`
Common **immutable methods**: `map`, `filter`, `reduce`, `concat`, `slice`, `spread (...)`

---

## 2. Why Immutability Matters

```js id="ia1"
const numbers = [1, 2, 3];
const doubled = numbers.map(n => n * 2);

console.log(numbers); // [1, 2, 3] ✅ original not changed
console.log(doubled); // [2, 4, 6]
```

* React relies on **state changes**
* If you mutate the array, React may **not detect changes**

---

## 3. Adding Items (Immutable)

```js id="ia2"
const fruits = ["apple", "banana"];

// Using spread
const newFruits = [...fruits, "mango"];
console.log(newFruits); // ["apple", "banana", "mango"]
```

* Original `fruits` array **not changed**

---

## 4. Removing Items (Immutable)

```js id="ia3"
const numbers = [1, 2, 3, 4];

// Remove number 2
const newNumbers = numbers.filter(n => n !== 2);
console.log(newNumbers); // [1, 3, 4]
```

* Use `filter()` to remove items **without mutating**

---

## 5. Updating Items (Immutable)

```js id="ia4"
const users = [
  { id: 1, name: "Howard" },
  { id: 2, name: "Alice" }
];

// Change name of user with id 2
const updatedUsers = users.map(user =>
  user.id === 2 ? { ...user, name: "Alicia" } : user
);

console.log(updatedUsers);
// [{ id: 1, name: "Howard" }, { id: 2, name: "Alicia" }]
```

* Use `map()` + **spread** to update objects immutably

---

## 6. React State Example

```jsx id="ia5"
const [tasks, setTasks] = useState(["Task 1", "Task 2"]);

const addTask = task => setTasks([...tasks, task]);
const removeTask = task => setTasks(tasks.filter(t => t !== task));
```

* Always create **new array** when updating state
* Avoid `tasks.push()` or `tasks.splice()`

---

## 7. Common Mistakes

* Using `push`, `splice`, or `sort` directly on **state arrays**

```js id="ia6"
// ❌ Mutates state directly
tasks.push("Task 3");
setTasks(tasks);
```

* Correct approach: **use spread or array methods that return new arrays**

```js id="ia7"
setTasks([...tasks, "Task 3"]); // ✅ Immutable
```

---

## 8. Practice

```js id="ia8"
const numbers = [1, 2, 3];

// Add 4 immutably
```

Answer:

```js id="ia9"
const newNumbers = [...numbers, 4];
console.log(newNumbers); // [1, 2, 3, 4]
```

---

## 9. Summary

* Immutability avoids **unexpected bugs in React**
* Use **map, filter, reduce, slice, spread**
* Avoid **push, pop, splice, sort** directly
* Always **return a new array** when updating state

---

## Rule

Work with arrays **immutably** in React to ensure **state updates** are detected and UI re-renders correctly.
