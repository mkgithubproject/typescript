Great! In TypeScript, **data types** help you write safer, more predictable code by telling the compiler what kind of value a variable can hold.

Here’s a beginner-friendly guide to **all important TypeScript data types** 👇

---

## ✅ **Basic Data Types in TypeScript**

| Type        | Example                                               | Description                             |
| ----------- | ----------------------------------------------------- | --------------------------------------- |
| `number`    | `let age: number = 25;`                               | Any number: integer or float            |
| `string`    | `let name: string = "Mohit";`                         | Text                                    |
| `boolean`   | `let isDone: boolean = true;`                         | `true` or `false`                       |
| `null`      | `let data: null = null;`                              | Null value                              |
| `undefined` | `let result: undefined = undefined;`                  | Undefined value                         |
| `any`       | `let value: any = "Hello";`                           | Can be **any** type — avoid if possible |
| `unknown`   | `let x: unknown = 10;`                                | Like `any` but safer                    |
| `never`     | `function error(): never { throw new Error("Oops") }` | Function that never returns             |

---

## ✅ **Other Important Data Types**

### 1. **Arrays**

```ts
let numbers: number[] = [1, 2, 3];
let names: string[] = ["Alice", "Bob"];
```

### 2. **Tuples** (fixed-length array with specific types)

```ts
let user: [string, number] = ["Mohit", 25];
```

### 3. **Enums** (named constants)

```ts
enum Color {
  Red,
  Green,
  Blue
}
let c: Color = Color.Green;
```

### 4. **Objects**

```ts
let person: { name: string; age: number } = {
  name: "Shiva",
  age: 30,
};
```

---

## ✅ **Custom Types**

### 1. **Type Alias**

```ts
type User = {
  name: string;
  age: number;
};

let user1: User = {
  name: "John",
  age: 25
};
```

### 2. **Interface**

```ts
interface Product {
  id: number;
  title: string;
}

let item: Product = {
  id: 1,
  title: "Laptop"
};
```

---

## ✅ **Function Types**

```ts
function greet(name: string): string {
  return `Hello, ${name}`;
}
```

---

## ✅ **Union & Intersection Types**

### Union (`|`) → value can be one of multiple types

```ts
let value: string | number = "Hello";
value = 123; // valid
```

### Intersection (`&`) → must satisfy **both** types

```ts
type A = { name: string };
type B = { age: number };

let person: A & B = {
  name: "Mohit",
  age: 25
};
```

---

## 🧠 Summary

| Category   | Types                                              |
| ---------- | -------------------------------------------------- |
| Primitives | `string`, `number`, `boolean`, `null`, `undefined` |
| Special    | `any`, `unknown`, `never`                          |
| Structured | `array`, `tuple`, `object`, `enum`                 |
| Custom     | `type`, `interface`, `union`, `intersection`       |
| Functions  | Return & parameter types                           |

---
Great! Let's now look at the **difference between `undefined` and `null` in JavaScript** (not just TypeScript).

Even though TypeScript builds on JavaScript, JavaScript also has its own specific behavior for these two special values.

---

## ✅ In JavaScript: `undefined` vs `null`

| Feature       | `undefined`                                                | `null`                                            |
| ------------- | ---------------------------------------------------------- | ------------------------------------------------- |
| **Meaning**   | A variable that has been declared but not assigned a value | A variable that is explicitly assigned “no value” |
| **Set by?**   | JavaScript itself                                          | You (the developer)                               |
| **Type**      | `"undefined"`                                              | `"object"` *(weird quirk)*                        |
| **Use case**  | “Not yet defined”                                          | “Intentionally empty”                             |
| **Common in** | Default return of unassigned variables or missing values   | Resetting object properties or clearing a value   |

---

## 🔍 Detailed Examples

### ➤ `undefined` examples

```js
let a;
console.log(a); // ➡️ undefined (variable declared, not assigned)

function greet() {}
console.log(greet()); // ➡️ undefined (no return value)

let obj = {};
console.log(obj.name); // ➡️ undefined (property doesn’t exist)
```

---

### ➤ `null` examples

```js
let name = null;
console.log(name); // ➡️ null (developer assigned “no value”)

let user = { name: null };
console.log(user.name); // ➡️ null (intentionally set to no value)
```

---

## ⚖️ Comparing `undefined` vs `null`

### 1. Loose equality (`==`)

```js
undefined == null // ✅ true (they're equal in value but not in type)
```

### 2. Strict equality (`===`)

```js
undefined === null // ❌ false (different types)
```

---

## 🔍 Type Checking

```js
typeof undefined; // "undefined"
typeof null;      // "object"  <-- historical JavaScript bug/quirk
```

Yes, `typeof null === "object"` is a known **JavaScript bug** from the early days of JS (not a TypeScript issue).

---

## 🧠 Simple Summary

| Concept             | `undefined`         | `null`              |
| ------------------- | ------------------- | ------------------- |
| Default by JS       | ✅                   | ❌                   |
| Manually assignable | ❌                   | ✅                   |
| Means               | "Not assigned"      | "Intentional empty" |
| Type                | `"undefined"`       | `"object"`          |
| `==` comparison     | Equal (`true`)      | Equal (`true`)      |
| `===` comparison    | Not equal (`false`) | Not equal (`false`) |

---

### ✅ Best Practice in JavaScript:

* Use `undefined` when the value is **not provided**.
* Use `null` when you want to **manually clear** or **empty** a variable.

---


