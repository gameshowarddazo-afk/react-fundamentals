# Asynchronous JavaScript: Async/Await

---

## 1. Overview

`async`/`await` is **syntactic sugar for Promises**.

* Makes asynchronous code **look and behave like synchronous code**
* Helps avoid **callback hell** and messy `.then()` chains

---

## 2. Basic Syntax

```js id="aa1"
const fetchData = () => {
  return new Promise(resolve => {
    setTimeout(() => resolve("Data loaded!"), 1000);
  });
};

const getData = async () => {
  const data = await fetchData();
  console.log(data); // "Data loaded!"
};

getData();
```

* `async` → marks a function as asynchronous
* `await` → pauses execution until promise resolves

---

## 3. Handling Errors

```js id="aa2"
const fetchData = () => Promise.reject("Error occurred!");

const getData = async () => {
  try {
    const data = await fetchData();
    console.log(data);
  } catch (error) {
    console.error(error); // "Error occurred!"
  }
};

getData();
```

* Always use **try/catch** to handle rejected promises

---

## 4. Returning Values from Async Functions

```js id="aa3"
const fetchNumber = async () => 10;

fetchNumber().then(result => console.log(result)); // 10
```

* `async` functions always return a **Promise**
* `return` value is **wrapped in a promise**

---

## 5. Multiple Async Calls

```js id="aa4"
const fetchUser = () => Promise.resolve({ name: "Howard" });
const fetchPosts = () => Promise.resolve(["Post 1", "Post 2"]);

const getData = async () => {
  const user = await fetchUser();
  const posts = await fetchPosts();
  console.log(user, posts);
};

getData();
```

* Sequential execution → **one after another**

---

### 5.1 Parallel Execution

```js id="aa5"
const getData = async () => {
  const [user, posts] = await Promise.all([fetchUser(), fetchPosts()]);
  console.log(user, posts);
};

getData();
```

* `Promise.all()` → **run multiple async tasks in parallel**

---

## 6. React Example: Fetching Data

```jsx id="aa6"
import { useState, useEffect } from "react";

const App = () => {
  const [user, setUser] = useState(null);

  useEffect(() => {
    const fetchUser = async () => {
      const response = await fetch("https://jsonplaceholder.typicode.com/users/1");
      const data = await response.json();
      setUser(data);
    };

    fetchUser();
  }, []);

  return <div>{user ? user.name : "Loading..."}</div>;
};
```

* Async function inside `useEffect` for **API calls**
* Avoid directly making `useEffect` callback `async` → wrap it

---

## 7. Common Mistakes

* Using `await` outside of `async` function

```js id="aa7"
// ❌
const data = await fetchData(); // SyntaxError

// ✅
const fetch = async () => {
  const data = await fetchData();
};
```

* Forgetting `try/catch` → unhandled rejected promise

* Sequentially awaiting **independent promises** when parallel would be faster

---

## 8. Practice

```js id="aa8"
const fetchNumber = () => Promise.resolve(5);

// Use async/await to double the number and log it
```

Answer:

```js id="aa9"
const getNumber = async () => {
  const num = await fetchNumber();
  console.log(num * 2); // 10
};

getNumber();
```

---

## 9. Summary

* `async/await` → modern, readable way to handle promises
* Use `try/catch` for error handling
* `async` functions **always return a promise**
* Can run **parallel tasks** with `Promise.all()`
* Ideal for **API calls** in React

---

## Rule

Use `async/await` for **clean, readable asynchronous code**, especially in React components and hooks.
