# Template Literals (JavaScript for React)

---

## 1. Overview

Template literals allow you to create **strings easily** and **embed variables** without using `+` for concatenation.

* Use **backticks** `` ` `` instead of quotes `' '` or `" "`
* Use **`${}`** to insert expressions

---

## 2. Basic Example

```js id="t1a2b3"
const name = "Howard";
const greeting = `Hello, ${name}!`;

console.log(greeting); // Hello, Howard!
```

---

## 3. Multi-line Strings

```js id="t4c5d6"
const message = `This is line 1
This is line 2
This is line 3`;

console.log(message);
/*
This is line 1
This is line 2
This is line 3
*/
```

* No need for `\n` for line breaks

---

## 4. Expressions Inside Template Literals

```js id="t7e8f9"
const a = 10;
const b = 20;

const result = `The sum of ${a} + ${b} is ${a + b}`;

console.log(result); // The sum of 10 + 20 is 30
```

---

## 5. Template Literals with Functions

```js id="t1g2h3"
const user = { name: "Howard", age: 21 };

const message = `Hello ${user.name}, you are ${user.age} years old.`;

console.log(message);
```

---

## 6. Using Template Literals in React

```jsx id="t4i5j6"
const name = "Howard";
const greeting = `Hello ${name}, welcome to React!`;

const App = () => <h1>{greeting}</h1>;
```

* Makes **JSX expressions cleaner**
* Easier than concatenation with `+`

---

## 7. Tagged Template Literals (Advanced)

```js id="t7k8l9"
function highlight(strings, ...values) {
  return strings.reduce(
    (result, str, i) => `${result}<strong>${values[i - 1] || ''}</strong>${str}`
  );
}

const name = "Howard";
const age = 21;

const message = highlight`My name is ${name} and I am ${age} years old.`;

console.log(message);
// My name is <strong>Howard</strong> and I am <strong>21</strong> years old.
```

* Advanced feature: process template literal values with a function

---

## 8. Common Mistakes

* Using quotes instead of backticks

```js id="t1m2n3"
// ❌ Wrong
const msg = 'Hello ${name}';
console.log(msg); // prints literally: Hello ${name}

// ✅ Correct
const msg = `Hello ${name}`;
```

* Forgetting `${}` for expressions

```js id="t4o5p6"
const a = 10;
const msg = `Value is a`; // prints: Value is a

const msgCorrect = `Value is ${a}`; // prints: Value is 10
```

---

## 9. Practice

```js id="t7q8r9"
const firstName = "Howard";
const lastName = "Dazo";

// Create a greeting using template literals
```

Answer:

```js id="t0s1t2"
const greeting = `Hello ${firstName} ${lastName}!`;
console.log(greeting); // Hello Howard Dazo!
```

---

## 10. Summary

* Template literals use **backticks `` ` ``**
* Use **`${}`** to embed variables or expressions
* Support **multi-line strings**
* Useful in React for JSX and dynamic content
* Advanced: tagged template literals for custom string processing

---

## Rule

Use **template literals** instead of string concatenation to make code **cleaner, readable, and dynamic**.
