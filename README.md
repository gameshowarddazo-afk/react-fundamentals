# Short-Circuiting and Logical Operators (`&&`, `||`, `??`)

---

## 1. Overview

Logical operators can be used not only for **true/false checks** but also for **short-circuit evaluation**.

* **`&&`** → returns right-hand side if left-hand side is truthy
* **`||`** → returns left-hand side if truthy, otherwise right-hand side
* **`??`** → nullish coalescing, returns right-hand side if left-hand side is `null` or `undefined`

---

## 2. AND (`&&`) Operator

```js
const isLoggedIn = true;
const message = isLoggedIn && "Welcome back!";

console.log(message); // "Welcome back!"
```

* If `isLoggedIn` is `true` → returns right-hand value
* If `isLoggedIn` is `false` → returns `false`

### React Example

```jsx
const isLoggedIn = true;

const App = () => (
  <div>
    {isLoggedIn && <h1>Welcome back!</h1>}
  </div>
);
```

* Common pattern for **conditional rendering**

---

## 3. OR (`||`) Operator

```js
const username = "";
const defaultName = username || "Guest";

console.log(defaultName); // "Guest"
```

* Returns **first truthy value**
* Useful for **default values**

### React Example

```jsx
const user = { name: "" };

const App = () => (
  <h1>Hello {user.name || "Guest"}</h1>
);
```

---

## 4. Nullish Coalescing (`??`) Operator

```js
const count = 0;
const displayCount = count ?? 10;

console.log(displayCount); // 0
```

* Only returns right-hand side if **left-hand side is ****`null`**** or ****`undefined`**
* Different from `||` because `0`, `""`, `false` are considered valid

### React Example

```jsx
const user = { name: null };

const App = () => <h1>Hello {user.name ?? "Guest"}</h1>;
```

---

## 5. Combining Operators

```js
const isLoggedIn = true;
const username = "";

const displayName = isLoggedIn && (username || "Guest");

console.log(displayName); // "Guest"
```

* Use `&&` to check conditions
* Use `||` or `??` for default values

---

## 6. Common Mistakes

* Using `||` when `0` or `""` is valid

```js
//  Wrong
const value = 0;
const display = value || 10; // 10 instead of 0

//  c
const display = value ?? 10; // 0
```

* Forgetting parentheses in complex expressions

```js
// Wrong
const result = isLoggedIn && username || "Guest"; // can be confusing

// Correct
const result = isLoggedIn && (username || "Guest");
```

---

## 7. Practice

```js
const user = { name: "" };
const isLoggedIn = false;

// Create a displayName that shows "Guest" if not logged in or name is empty
```

Answer:

```js
const displayName = isLoggedIn && (user.name || "Guest");
console.log(displayName); // false
```

---

## 8. Summary

* `&&` → run right-hand side if left is truthy
* `||` → return first truthy value
* `??` → return right-hand side only if left is `null` or `undefined`
* Common in React for **conditional rendering** and **default values**
* Use parentheses to avoid confusion in combined expressions

---

## Rule

Use logical operators for **short, readable conditions** and to **provide defaults** without `if/else` statements.
