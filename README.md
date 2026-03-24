# Arrow Functions (JavaScript for React)

---

## 1. Overview

Arrow functions provide a **shorter syntax** for writing functions and handle the `this` keyword differently from regular functions.

Syntax:

```js id="af1"
const functionName = (parameters) => {
  // function body
};
```

* Use `()` for parameters
* Use `{}` for multiple statements
* If single expression, `{}` and `return` can be omitted

---

## 2. Basic Examples

### 2.1 Single-line arrow function

```js id="af2"
const add = (a, b) => a + b;

console.log(add(2, 3)); // 5
```

* Single expression → returns automatically

---

### 2.2 Multiple-line arrow function

```js id="af3"
const multiply = (a, b) => {
  const result = a * b;
  return result;
};

console.log(multiply(2, 3)); // 6
```

* Use `{}` and `return` for multiple statements

---

### 2.3 No parameters

```js id="af4"
const greet = () => "Hello World";

console.log(greet()); // Hello World
```

---

### 2.4 Single parameter (no parentheses needed)

```js id="af5"
const square = x => x * x;

console.log(square(4)); // 16
```

---

## 3. Arrow Functions in React

### 3.1 Functional Components

```jsx id="af6"
const App = () => <h1>Hello React</h1>;
```

* Always use `const` + arrow function for components

---

### 3.2 Event Handlers

```jsx id="af7"
const Button = () => {
  const handleClick = () => console.log("Clicked!");
  
  return <button onClick={handleClick}>Click me</button>;
};
```

* Arrow functions keep **`this` context** predictable

---

### 3.3 Map Function

```jsx id="af8"
const numbers = [1, 2, 3];
const doubled = numbers.map(n => n * 2);

console.log(doubled); // [2, 4, 6]
```

* Short and readable for array operations

---

## 4. Arrow Function with Destructuring

```js id="af9"
const printUser = ({ name, age }) => `${name} is ${age} years old`;

const user = { name: "Howard", age: 21 };

console.log(printUser(user)); // Howard is 21 years old
```

* Works well with objects and arrays

---

## 5. Common Mistakes

* Using `this` differently than expected in regular functions

```js id="af10"
// ❌ Might not behave as expected
function Person() {
  this.age = 21;
  setTimeout(function() { console.log(this.age); }, 1000);
}

// ✅ Arrow function fixes `this`
function Person() {
  this.age = 21;
  setTimeout(() => { console.log(this.age); }, 1000);
}
```

* Forgetting parentheses for multiple parameters

```js id="af11"
// ❌ Wrong
const add = a, b => a + b;

// ✅ Correct
const add = (a, b) => a + b;
```

---

## 6. Practice

Convert to arrow function:

```js id="af12"
function greet(name) {
  return `Hello ${name}`;
}
```

Answer:

```js id="af13"
const greet = name => `Hello ${name}`;
```

---

## 7. Summary

* Shorter syntax for functions
* Auto-return for single expressions
* Handles `this` differently → good for React events
* Common in components, handlers, and array methods

---

## Rule

Use **arrow functions** for **shorter, cleaner functions** and when you want **predictable `this` behavior**, especially in React.

