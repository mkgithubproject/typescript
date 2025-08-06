In TypeScript, `type`, `interface`, `union`, and `intersection` are powerful tools used to define the shape and composition of data. Here's a breakdown of each with **clear differences**, **use cases**, and **examples**.

---

## 🔹 1. `type`

* Used to define **aliases** for types.
* Can represent **primitives**, **unions**, **intersections**, **tuples**, etc.

### ✅ Syntax:

```ts
type UserId = string;
type Status = "active" | "inactive";
type Point = { x: number; y: number };
```

### ✅ Features:

* Can use `union` and `intersection`
* Cannot be extended after declaration

---

## 🔹 2. `interface`

* Used to define the **shape of objects/classes**.
* **Preferred for OOP and object contracts**.

### ✅ Syntax:

```ts
interface User {
  id: string;
  name: string;
}
```

### ✅ Features:

* Can be **extended**
* Can be **merged** (declaration merging)
* Only works for object types

```ts
interface A { a: number; }
interface A { b: number; } // Merged into { a: number; b: number }
```

---

## 🔹 3. `union (|)`

* A type that can be **one of many**.
* Great for **either/or logic**.

### ✅ Syntax:

```ts
type Status = "success" | "error" | "loading";
type Input = string | number;
```

### ✅ Usage:

```ts
function print(input: string | number) {
  if (typeof input === "string") {
    console.log(input.toUpperCase());
  } else {
    console.log(input.toFixed(2));
  }
}
```

---

## 🔹 4. `intersection (&)`

* Combines **multiple types into one**.
* Must satisfy **all** combined types.

### ✅ Syntax:

```ts
type Audit = { createdAt: Date };
type User = { name: string };
type AuditedUser = User & Audit;
```

### ✅ Result:

```ts
const user: AuditedUser = {
  name: "Mohit",
  createdAt: new Date(),
};
```

---

## 🧠 When to Use What?

| Use Case                          | Use `interface` | Use `type`                      |
| --------------------------------- | --------------- | ------------------------------- |
| Object shape with extension       | ✅ Yes           | ✅ Yes (via `&`)                 |
| Need union or intersection        | ❌ No            | ✅ Yes                           |
| Declaration merging               | ✅ Yes           | ❌ No                            |
| For primitives, functions, tuples | ❌ No            | ✅ Yes                           |
| Class implementation              | ✅ Yes           | ✅ Yes (but interface preferred) |

---

## 💡 Summary with Examples

```ts
// interface
interface Dog {
  name: string;
}
interface Dog {
  age: number; // merged
}

// type
type Cat = {
  name: string;
};
// type Cat = { age: number }; ❌ Cannot redeclare

// union
type Result = "pass" | "fail";

// intersection
type A = { x: number };
type B = { y: number };
type AB = A & B; // { x: number; y: number }
```

---

If you want a **visual or cheat sheet comparison**, let me know — I can generate that too.
