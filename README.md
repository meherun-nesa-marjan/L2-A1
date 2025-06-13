# Mastering TypeScript: Essential Concepts Every Developer Should Know

TypeScript has quickly become the go-to language for scalable, maintainable JavaScript development. By adding static types and powerful language features, it helps developers write more robust and error-free code. In this post, we’ll explore some fundamental TypeScript concepts that will boost your productivity and code quality.

---

## 1. Interfaces vs Types in TypeScript: What’s the Difference?

Both **interfaces** and **type aliases** are used to define the shape of objects in TypeScript, but they have important differences:

- **Interfaces** support **declaration merging** — you can define the same interface multiple times and TypeScript merges them.
- **Type aliases** are more flexible: they can represent not only object shapes but also primitives, unions, intersections, and tuples.
- Interfaces can only describe object-like shapes, whereas type aliases can define complex types.

**Example:**

```ts
interface User {
  name: string;
}

interface User {
  age: number;  // This merges with the previous interface
}

type ID = string | number;  // Union type alias
```

## 2. What is the use of the keyof keyword in TypeScript?

The keyof keyword extracts the keys of an object type as a union of string literals. This allows dynamic yet type-safe operations on object properties.

**Example:**

```ts
type Person = {
  name: string;
  age: number;
};

type PersonKeys = keyof Person;  // "name" | "age"

function getProperty<T, K extends keyof T>(obj: T, key: K): T[K] {
  return obj[key];
}

const person: Person = { name: "Alice", age: 30 };
const name = getProperty(person, "name");  // returns "Alice"
```
