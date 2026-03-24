# `const` and `let` Patterns (Beginner → Advanced for React)

---

## 1. Golden Rule

* Use `const` by default
* Use `let` if the value will change

```js
const name = "Howard";

let count = 0;
count++;
```

---

## 2. Beginner Pattern

Start with `const`:

```js
const price = 100;
```

Switch to `let` only when needed:

```js
let total = 0;
total += 10;
```

---

## 3. React Basic Pattern

Components use `const`:

```jsx
const App = () => {
  return <h1>Hello React</h1>;
};
```

Props also use `const`:

```jsx
const Welcome = ({ name }) => {
  return <h1>Hello {name}</h1>;
};
```

---

## 4. Avoid Mutation

Do not change arrays or objects directly.

Bad:

```js
const arr = [1, 2];
arr.push(3);
```

Good:

```js
const arr = [1, 2];
const newArr = [...arr, 3];
```

---

## 5. Loop Pattern

Use `let` when values change in loops:

```js
for (let i = 0; i < 5; i++) {
  console.log(i);
}
```

---

## 6. Conditional Pattern

Use `let` when value depends on logic:

```js
let result;

if (score > 50) {
  result = "Pass";
} else {
  result = "Fail";
}
```

---

## 7. Derived Values

Use `const` for computed values:

```js
const total = price * quantity;
```

Avoid unnecessary `let`:

```js
let total = price * quantity;
```

---

## 8. React State Pattern

Do not reassign state directly.

Wrong:

```jsx
const [count, setCount] = useState(0);
count++;
```

Correct:

```jsx
setCount(count + 1);
```

---

## 9. Immutability Pattern

Arrays:

```js
const items = ["a", "b"];
const newItems = [...items, "c"];
```

Objects:

```js
const user = { name: "Howard" };
const updatedUser = { ...user, age: 21 };
```

---

## 10. Block Scope

Both `const` and `let` are block scoped:

```js
if (true) {
  const message = "Hello";
}

console.log(message); // error
```

---

## 11. Anti-Patterns

Using `let` unnecessarily:

```js
let name = "Howard";
```

Reassigning `const`:

```js
const age = 21;
age = 22;
```

Mutating data:

```js
arr.push(3);
```

---

## 12. Practice

Fix:

```js
let price = 100;
```

Answer:

```js
const price = 100;
```

---

Fix:

```js
const count = 0;
count++;
```

Answer:

```js
let count = 0;
count++;
```

---

## Summary

* Use `const` by default
* Use `let` only when needed
* Do not mutate arrays or objects
* Use spread (`...`) for updates
* Components and props use `const`
* React state must be updated using functions

---

## Rule

If the value does not change, use `const`.
If the value changes, use `let`.
