# Destructuring: Object & Array

---

## 1. Overview

Destructuring is a way to **extract values from objects and arrays**.

Benefits:

- Shorter code
- Cleaner syntax
- Easier to read and maintain

---

## 2. Object Destructuring

### Basic Example

```js
const user = {
  name: "Howard",
  age: 21,
};

const { name, age } = user;

console.log(name); // Howard
console.log(age); // 21
```

---

### Renaming Variables

```js
const user = { name: "Howard" };

const { name: username } = user;

console.log(username); // Howard
```

---

### Default Values

```js
const user = { name: "Howard" };

const { age = 18 } = user;

console.log(age); // 18
```

---

### Nested Destructuring

```js
const user = {
  name: "Howard",
  address: { city: "Manila" },
};

const {
  address: { city },
} = user;

console.log(city); // Manila
```

---

### Using Spread with Objects

```js
const user = { name: "Howard", age: 21, country: "PH" };

const { name, ...rest } = user;

console.log(name); // Howard
console.log(rest); // { age: 21, country: "PH" }
```

---

## 3. Array Destructuring

### Basic Example

```js
const fruits = ["apple", "banana", "mango"];

const [first, second] = fruits;

console.log(first); // apple
console.log(second); // banana
```

---

### Skipping Values

```js
const fruits = ["apple", "banana", "mango"];

const [first, , third] = fruits;

console.log(third); // mango
```

---

### Default Values in Arrays

```js
const numbers = [10];

const [a, b = 20] = numbers;

console.log(a); // 10
console.log(b); // 20
```

---

## 4. React Examples

### Props Destructuring

```jsx
const Welcome = ({ name }) => {
  return <h1>Hello {name}</h1>;
};
```

---

### Function Parameter Destructuring

```js
const printUser = ({ name, age }) => {
  console.log(name, age);
};
```

---

## 5. Common Mistakes

- Wrong variable name

```js
const { username } = user; // undefined
```

- Destructuring undefined

```js
const { name } = undefined; // error
```

---

## 6. Practice

Object:

```js
const product = { title: "Laptop", price: 50000 };
const { title, price } = product;
```

Array:

```js
const numbers = [10, 20, 30];
const [first, second] = numbers;
```

---

## Summary

- Object destructuring uses `{}`
- Array destructuring uses `[]`
- Supports default values, renaming, nested extraction
- Very common in React for props and state
- Helps make code shorter and cleaner

---

## Rule

Use destructuring whenever you need to **extract values from objects or arrays** to keep code readable and concise.
