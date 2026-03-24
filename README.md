# Asynchronous JavaScript: Promises

---

## 1. Overview

A **Promise** is an object representing the **eventual completion or failure** of an asynchronous operation.

* Helps avoid **callback hell**
* Can be in **three states**:

  1. **Pending** – initial state
  2. **Fulfilled** – operation succeeded
  3. **Rejected** – operation failed

Syntax:

```js id="p1"
const promise = new Promise((resolve, reject) => {
  // asynchronous code
});
```

* `resolve(value)` → marks promise as fulfilled
* `reject(error)` → marks promise as rejected

---

## 2. Basic Example

```js id="p2"
const fetchData = new Promise((resolve, reject) => {
  const success = true;

  setTimeout(() => {
    if (success) resolve("Data received!");
    else reject("Error occurred!");
  }, 1000);
});

fetchData
  .then(data => console.log(data))   // "Data received!"
  .catch(error => console.error(error));
```

* `then()` → handles **fulfilled**
* `catch()` → handles **rejected**

---

## 3. Promises in React (Async Functions)

```js id="p3"
const fetchUser = () => {
  return new Promise(resolve => {
    setTimeout(() => resolve({ name: "Howard", age: 21 }), 1000);
  });
};

fetchUser().then(user => console.log(user.name)); // Howard
```

* Promises often used with **API calls**

---

## 4. Chaining Promises

```js id="p4"
const fetchNumber = () => Promise.resolve(5);

fetchNumber()
  .then(num => num * 2)
  .then(result => console.log(result)); // 10
```

* Each `then()` receives the value returned from previous step

---

## 5. Promise.all

```js id="p5"
const promise1 = Promise.resolve(1);
const promise2 = Promise.resolve(2);
const promise3 = Promise.resolve(3);

Promise.all([promise1, promise2, promise3])
  .then(values => console.log(values)); // [1, 2, 3]
```

* Waits for **all promises to resolve**
* Rejects if **any promise fails**

---

## 6. Async/Await (Syntactic Sugar)

```js id="p6"
const fetchData = () => Promise.resolve("Data loaded!");

const getData = async () => {
  try {
    const data = await fetchData();
    console.log(data); // "Data loaded!"
  } catch (error) {
    console.error(error);
  }
};

getData();
```

* `async` functions always return a **promise**
* `await` pauses execution until promise resolves

---

## 7. Common Mistakes

* Forgetting `catch()` → unhandled promise rejection

```js id="p7"
// ❌
fetchData().then(data => console.log(data)); // if rejected → error
```

* Using `await` outside of `async` function

```js id="p8"
// ❌
const data = await fetchData(); // SyntaxError

// ✅
const fetch = async () => {
  const data = await fetchData();
};
```

* Not returning value in chained `then()`

---

## 8. Practice

```js id="p9"
const fetchNumber = () => Promise.resolve(10);

// Double the number and log it
```

Answer:

```js id="p10"
fetchNumber()
  .then(num => num * 2)
  .then(result => console.log(result)); // 20
```

---

## 9. Summary

* Promises handle **asynchronous operations**
* States: **pending, fulfilled, rejected**
* `.then()` → handle success
* `.catch()` → handle failure
* `async/await` → cleaner syntax
* `Promise.all()` → wait for multiple promises

---

## Rule

Use **promises** to manage **async tasks** in JavaScript, especially for **API calls** or **delayed operations** in React.
