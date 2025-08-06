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

Would you like a **cheat sheet image** or a mini quiz to test your understanding?
