# Rest and Spread Operators (JavaScript for React)

---

## 1. Overview

Rest (`...`) and Spread (`...`) look the same but have **different uses**:

* **Spread**: expands elements of arrays or properties of objects
* **Rest**: collects multiple elements into a single array or object

---

## 2. Spread Operator (`...`)

### 2.1 Arrays

```js id="a1b2c3"
const numbers = [1, 2, 3];
const newNumbers = [...numbers, 4, 5];

console.log(newNumbers); // [1, 2, 3, 4, 5]
```

* Expands elements of `numbers` into a new array
* Useful to **avoid mutating the original array**

---

### 2.2 Objects

```js id="d4e5f6"
const user = { name: "Howard", age: 21 };
const updatedUser = { ...user, country: "PH" };

console.log(updatedUser);
// { name: "Howard", age: 21, country: "PH" }
```

* Copies all properties from `user` into a new object
* Can **add or override properties**

---

### 2.3 Function Arguments

```js id="g7h8i9"
const nums = [1, 2, 3];

const sum = (a, b, c) => a + b + c;

console.log(sum(...nums)); // 6
```

* Expands array into individual arguments

---

## 3. Rest Operator (`...`)

### 3.1 Arrays

```js id="j1k2l3"
const [first, ...rest] = [1, 2, 3, 4];

console.log(first); // 1
console.log(rest);  // [2, 3, 4]
```

* Collects the **remaining elements** into an array

---

### 3.2 Objects

```js id="m4n5o6"
const { name, ...others } = { name: "Howard", age: 21, country: "PH" };

console.log(name);   // Howard
console.log(others); // { age: 21, country: "PH" }
```

* Collects **remaining properties** into a new object

---

### 3.3 Function Parameters

```js id="p7q8r9"
const sum = (...numbers) => {
  return numbers.reduce((acc, curr) => acc + curr, 0);
};

console.log(sum(1, 2, 3, 4)); // 10
```

* Collects **any number of arguments** into an array

---

## 4. React Examples

### 4.1 Props Spread

```jsx id="s1t2u3"
const props = { name: "Howard", age: 21 };

const User = (props) => <h1>{props.name}, {props.age}</h1>;

// Use spread
<User {...props} />
```

---

### 4.2 State Update with Spread

```jsx id="v4w5x6"
const [user, setUser] = useState({ name: "Howard", age: 21 });

// Update only age without mutating original
setUser({ ...user, age: 22 });
```

---

## 5. Common Mistakes

* Confusing rest and spread

```js id="y7z8a9"
// ❌ Wrong
const nums = [1, 2, 3];
const [rest, first] = nums; // Not correct
```

* Mutating objects instead of spreading

```js id="b1c2d3"
const user = { name: "Howard" };
user.age = 21; // avoid, use spread instead
```

---

## 6. Practice

### 6.1 Arrays

```js id="e4f5g6"
const numbers = [1, 2, 3, 4, 5];
const [first, ...rest] = numbers;
```

Answer:

```js id="h7i8j9"
first // 1
rest  // [2, 3, 4, 5]
```

---

### 6.2 Objects

```js id="k1l2m3"
const user = { name: "Howard", age: 21, country: "PH" };
const { name, ...others } = user;
```

Answer:

```js id="n4o5p6"
name   // "Howard"
others // { age: 21, country: "PH" }
```

---

## 7. Summary

* **Spread (`...`)**: expand arrays/objects
* **Rest (`...`)**: collect remaining elements/properties
* Very useful in React for **props, state, and arrays**
* Helps **avoid mutation** and keeps code clean

---

## Rule

Use **spread to expand** and **rest to collect** values in objects, arrays, or function parameters.
