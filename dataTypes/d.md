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
Here’s a **deep dive into TypeScript data types** with theory, examples, and use cases. This will give you a solid understanding of how TypeScript handles types and how you can use them to build robust, maintainable applications.

---

# ✅ **TypeScript Data Types – Theory + Examples**

## 🔹 What are Data Types in TypeScript?

Data types define **what kind of data** a variable can hold. TypeScript adds static typing to JavaScript, helping developers catch type-related bugs **during development** rather than at runtime.

> 🎯 **Real-life analogy**: Just like you assign labels to boxes in a warehouse to know what's inside ("Books", "Electronics"), data types label your variables so you know what kind of value they should hold.

---

## 🧠 **Why Use Data Types in TypeScript?**

| Benefits                    | Description                                              |
| --------------------------- | -------------------------------------------------------- |
| ✅ Early Error Detection     | Type errors are caught at compile time.                  |
| ✅ Better IDE Support        | Autocomplete, IntelliSense, etc.                         |
| ✅ Improved Code Readability | Easier to understand what kind of data a variable holds. |
| ✅ Safer Refactoring         | Types make refactoring predictable.                      |
| ✅ Documentation via Types   | Code is self-documenting.                                |

---

## 🧱 **Types in TypeScript**

### 🔹 1. **Primitive Types**

These are the basic data types built into the language.

#### a. `number`

Represents all numeric values including integers and floating-point numbers.

```ts
let age: number = 25;
let price: number = 99.99;
```

**Real-life use case**: Tracking age, price, or quantity in a billing system.

#### b. `string`

Represents textual data.

```ts
let name: string = "John Doe";
let greeting: string = `Hello, ${name}`;
```

**Use case**: Displaying names, product descriptions, etc.

#### c. `boolean`

Represents true or false values.

```ts
let isLoggedIn: boolean = true;
```

**Use case**: User login status, toggles, switches.

#### d. `null` and `undefined`

Represents absence of value or not initialized.

```ts
let x: null = null;
let y: undefined = undefined;
```

> ✅ Tip: Use `strictNullChecks` in tsconfig to catch null-related bugs.

#### e. `bigint`

For arbitrarily large integers.

```ts
let big: bigint = 9007199254740991n;
```

**Use case**: Financial calculations with large numbers.

#### f. `symbol`

Represents unique identifiers.

```ts
let sym: symbol = Symbol("unique");
```

**Use case**: Keys in objects where you need uniqueness.

---

### 🔹 2. **Object Types**

Used to define complex structures.

#### a. `object`

```ts
let person: object = {
  name: "Alice",
  age: 30
};
```

#### b. **Custom Types (Type Aliases)**

```ts
type User = {
  name: string;
  age: number;
};

let user: User = {
  name: "Bob",
  age: 25
};
```

**Use case**: Representing a user, employee, or product in an app.

---

### 🔹 3. **Array Types**

Represents a list of elements.

#### a. `number[]` or `Array<number>`

```ts
let numbers: number[] = [1, 2, 3];
let names: Array<string> = ["Alice", "Bob"];
```

**Use case**: Cart items, user list, scores, etc.

---

### 🔹 4. **Tuple Types**

Represents a fixed-size array with defined types.

```ts
let person: [string, number] = ["Alice", 30];
```

**Use case**: Key-value pairs like \[latitude, longitude].

---

### 🔹 5. **Enum Type**

Gives names to constant values.

```ts
enum Direction {
  Up,
  Down,
  Left,
  Right
}
let move: Direction = Direction.Up;
```

> ⚠️ Prefer `const enum` for performance.

**Use case**: Representing user roles, directions, status codes.

---

### 🔹 6. **Any Type**

Disables type checking.

```ts
let data: any = 5;
data = "Now a string";
data = true;
```

**Use case**: Migrating from JS or working with unknown libraries.

---

### 🔹 7. **Unknown Type**

A safer alternative to `any`.

```ts
let value: unknown = "hello";
if (typeof value === "string") {
  console.log(value.toUpperCase());
}
```

**Use case**: Handling dynamic inputs or third-party API responses.

---

### 🔹 8. **Union Types (`|`)**

Allows a variable to hold multiple types.

```ts
let id: number | string;
id = 101;
id = "E101";
```

**Use case**: Accepting both numeric and alphanumeric user IDs.

---

### 🔹 9. **Intersection Types (`&`)**

Combines multiple types into one.

```ts
type Person = { name: string };
type Employee = { id: number };
type Staff = Person & Employee;
const emp: Staff = {
  name: "Alice",
  id: 101
};
```

**Use case**: Merging two interfaces like profile + role info.

---

### 🔹 10. **Literal Types**

Restricts a variable to specific values.

```ts
let status: "success" | "error" | "loading";
status = "success"; // ✅
status = "failed";  // ❌ Error
```

**Use case**: Representing UI or API states.

---

### 🔹 11. **Function Types**

Defines the shape of a function.

#### a. With Parameter and Return Types

```ts
function add(x: number, y: number): number {
  return x + y;
}
```

#### b. Function as a Type

```ts
let greet: (name: string) => string;
greet = function(name: string) {
  return `Hello, ${name}`;
};
```

**Use case**: Event handlers, callbacks.

---

### 🔹 12. **Void Type**

Used for functions that don't return a value.

```ts
function logMessage(msg: string): void {
  console.log(msg);
}
```

**Use case**: Logging, status updates.

---

### 🔹 13. **Never Type**

Used when a function never returns.

```ts
function throwError(msg: string): never {
  throw new Error(msg);
}
```

**Use case**: Error handling, infinite loops.

---

### 🔹 14. **Type Inference**

TS can automatically assign a type.

```ts
let score = 100; // inferred as number
```

**Use case**: Decluttering code while maintaining safety.

---

### 🔹 15. **Type Assertion**

Forcefully tell TypeScript the type.

```ts
let someValue: unknown = "hello";
let strLength: number = (someValue as string).length;
```

**Use case**: When you're certain of the type, such as DOM manipulation.

---

### 🔹 16. **Optional and Default Parameters**

```ts
function greet(name: string, age?: number) {
  console.log(`Hello ${name}`);
}
function multiply(a: number, b: number = 2): number {
  return a * b;
}
```

**Use case**: Optional user input fields, default configurations.

---

### 🔹 17. **Readonly Type**

Prevents reassignment.

```ts
type User = {
  readonly id: number;
  name: string;
};
const user: User = { id: 1, name: "Alice" };
user.id = 2; // ❌ Error
```

**Use case**: Enforcing immutability, such as IDs.

---

## ✅ Summary Table

| Type       | Example                               |          |
| ---------- | ------------------------------------- | -------- |
| `number`   | `let x: number = 10;`                 |          |
| `string`   | `let name: string = "Alice";`         |          |
| `boolean`  | `let isOpen: boolean = true;`         |          |
| `array`    | `let nums: number[] = [1, 2, 3];`     |          |
| `tuple`    | `let data: [string, number]`          |          |
| `enum`     | `enum Direction { Up, Down }`         |          |
| `any`      | `let x: any = 5;`                     |          |
| `unknown`  | `let x: unknown = "test";`            |          |
| `union`    | \`let id: string                      | number\` |
| `function` | `function greet(name: string): void`  |          |
| `never`    | `function fail(): never { throw ...}` |          |
| `literal`  | \`let status: "success"               | "fail"\` |

---

## 🧪 Real-World Example

```ts
type Product = {
  id: number;
  name: string;
  price: number;
  inStock: boolean;
};

function printProduct(product: Product): void {
  console.log(`${product.name} - ₹${product.price}`);
}

const pen: Product = {
  id: 1,
  name: "Ball Pen",
  price: 10,
  inStock: true
};

printProduct(pen);
```

> 🛒 **Real-life scenario**: This `Product` type could represent an item in an e-commerce app where you display product details, price, and availability.

---

Would you like this in a **PDF note format** or want a **cheat sheet version** for revision?



