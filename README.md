# Ternary Operator (Instead of if/else)

---

## 1. Overview

The **ternary operator** is a **shorter way to write simple if/else statements**.

Syntax:

```js
condition ? valueIfTrue : valueIfFalse
```

* `condition` → expression that evaluates to `true` or `false`
* `valueIfTrue` → returned if condition is true
* `valueIfFalse` → returned if condition is false

---

## 2. Basic Example

```js id="t1a2b3"
const age = 18;
const canVote = age >= 18 ? "Yes" : "No";

console.log(canVote); // Yes
```

* `age >= 18` → condition
* `"Yes"` → if true
* `"No"` → if false

---

## 3. Replacing Simple if/else

Instead of:

```js id="t4c5d6"
let status;
if (age >= 18) {
  status = "Adult";
} else {
  status = "Minor";
}
```

You can write:

```js id="t7e8f9"
const status = age >= 18 ? "Adult" : "Minor";
```

* Cleaner and shorter
* Works for simple conditions

---

## 4. Nested Ternaries (Advanced)

```js id="t1g2h3"
const score = 85;
const grade = score >= 90 ? "A" :
              score >= 80 ? "B" :
              score >= 70 ? "C" : "F";

console.log(grade); // B
```

* Can replace multiple if/else statements
* Be careful: **don’t over-nest**, it reduces readability

---

## 5. React Examples

### 5.1 Conditional Rendering

```jsx id="t4i5j6"
const isLoggedIn = true;

const App = () => (
  <div>
    {isLoggedIn ? <h1>Welcome back!</h1> : <h1>Please log in</h1>}
  </div>
);
```

* Ternary operators are **commonly used in JSX**
* Keeps rendering logic compact

---

### 5.2 Inline Class Names

```jsx id="t7k8l9"
const isActive = false;

const buttonClass = `btn ${isActive ? "btn-active" : "btn-inactive"}`;

console.log(buttonClass); // "btn btn-inactive"
```

---

## 6. Common Mistakes

* Using ternary for **complex logic** → makes code hard to read

```js id="t1m2n3"
// ❌ Hard to read
const value = condition1 ? (condition2 ? "A" : "B") : (condition3 ? "C" : "D");
```

* Forgetting `:` → SyntaxError

```js id="t4o5p6"
// ❌ Wrong
const value = condition ? "Yes"; 
```

---

## 7. Practice

Convert if/else to ternary:

```js id="t7q8r9"
let message;
if (score >= 50) {
  message = "Pass";
} else {
  message = "Fail";
}
```

Answer:

```js id="t0s1t2"
const message = score >= 50 ? "Pass" : "Fail";
```

---

## 8. Summary

* Ternary operator is a **shortcut for if/else**
* Syntax: `condition ? valueIfTrue : valueIfFalse`
* Great for **simple conditions and JSX rendering**
* Avoid nested ternaries for readability

---

## Rule

Use **ternary operators** for concise conditions instead of simple if/else, especially in React JSX.
