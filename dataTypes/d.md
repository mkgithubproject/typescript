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
If you declare the same variable `a` in **two different files** with **different types** — like `let a: string` in one file and `let a: number` in another — here's what will happen when you run `tsc` (TypeScript compiler):

---

### ✅ **Case 1: `a` is declared in different scopes (not global)**

#### File 1 (`file1.ts`):

```ts
function func1() {
  let a: string = "hello";
}
```

#### File 2 (`file2.ts`):

```ts
function func2() {
  let a: number = 123;
}
```

* ✅ **No error**
* Because both `a` variables are in separate **local scopes**, there is **no conflict**.
* TypeScript compiles successfully.

---

### ❌ **Case 2: `a` is declared as a global variable (top-level in both files)**

#### File 1 (`file1.ts`):

```ts
let a: string = "hello";
```

#### File 2 (`file2.ts`):

```ts
let a: number = 123;
```

* ❌ **Compilation Error** when you run `tsc`:

```
error TS2451: Cannot redeclare block-scoped variable 'a'.
```

* TypeScript treats these `let` declarations at the top level of modules (or script files if you're not using modules) as **global declarations**, and **block-scoped variables (`let`) cannot be redeclared**.

---

### ✅ **How to Avoid Conflict**

1. **Use `export`/`import` (Modules)**:
   Wrap each variable in its own module to avoid polluting the global scope.

2. **Encapsulate variables inside functions or classes** to keep their scopes local.

---

### ✅ **Tip**: If both files are modules (they use `export` or `import`), then each file has its **own module scope**, and `let a: string` in one file and `let a: number` in another will NOT conflict.

#### Example:

**file1.ts**

```ts
export let a: string = "hello";
```

**file2.ts**

```ts
export let a: number = 42;
```

✅ This is valid — no error — because each `a` is in its own module scope.

---

### ✅ What Happens in JavaScript (`.js` files)?

#### File 1 (`file1.js`)

```js
let a = "hello";
```

#### File 2 (`file2.js`)

```js
let a = 123;
```

#### 👉 If you run them separately:

```bash
node file1.js
node file2.js
```

* ✅ No error — each file has its own execution context.

#### 👉 If you combine them (e.g., browser `<script>` tags or bundling):

* ❌ JavaScript throws a **SyntaxError**:

```
SyntaxError: Identifier 'a' has already been declared
```

* Because `let` is block-scoped and can't be redeclared in the same scope.

---

### ✅ Local Scope Example in JS (No Error)

**file1.js**

```js
function f1() {
  let a = "hello";
}
```

**file2.js**

```js
function f2() {
  let a = 123;
}
```

* ✅ No error — separate local scopes.

---

### ✅ Using Modules in JS (ES6 `export`/`import`)

**file1.js**

```js
export let a = "hello";
```

**file2.js**

```js
export let a = 123;
```

✅ Works fine — each module has its own isolated scope.

---

### 🧠 Why TypeScript gives an error but JavaScript doesn't

TypeScript and JavaScript behave differently because of **how they handle global variables and module scope**:

| Feature                     | TypeScript (`ts`)                                      | JavaScript (`js`)                          |
| --------------------------- | ------------------------------------------------------ | ------------------------------------------ |
| Compilation model           | Analyzes all `.ts` files together                      | Executes one file at a time                |
| Global `let` conflict check | ✅ Yes, throws `TS2451` if top-level variables conflict | ❌ No conflict when files run separately    |
| Scope model                 | Shared global scope unless using `export`/`import`     | Each run has its own scope unless combined |
| Static analysis             | Strong type + scope tracking                           | No static analysis, just runtime           |

#### ✅ How to fix the conflict in TypeScript:

* Make each file a **module** using `export` or `import`.
* That isolates their scope and avoids global conflicts.

---

### Summary

| Situation                                 | Error? | Explanation                                       |
| ----------------------------------------- | ------ | ------------------------------------------------- |
| TypeScript: Top-level `let` in both files | ✅ Yes  | Redeclaration error (`TS2451`)                    |
| TypeScript: Inside functions              | ❌ No   | Local scopes are separate                         |
| TypeScript: In modules (`export`)         | ❌ No   | Module scopes are isolated                        |
| JavaScript: Run files separately          | ❌ No   | Different runtime contexts                        |
| JavaScript: Combined files, global `let`  | ✅ Yes  | SyntaxError — can't redeclare `let` in same scope |
| JavaScript: Local `let` inside functions  | ❌ No   | No conflict in local scopes                       |
| JavaScript: Using ES modules              | ❌ No   | Isolated module scopes, like TypeScript modules   |

Let me know if you want to test this live or need examples for modules or namespaces.


