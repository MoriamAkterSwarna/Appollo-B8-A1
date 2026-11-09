# Assignment 1 — Problem Solving with TypeScript & OOP

This repository contains my solutions for the Problem Solving assignment and two blog posts based on the TypeScript course.

## File structure

```
├── solutions.ts
├── generics-with-promises.md
├── union-and-intersection-types.md
└── README.md
```

## What is inside solutions.ts

The file contains all eight problems in one place, with explicit parameter and return types on every function and method.

| # | Name | Topic |
|---|------|-------|
| 1 | `multiplyValue` | Optional parameter with default handling |
| 2 | `processInput` | Union type and `typeof` narrowing |
| 3 | `formatCoordinate` | Readonly tuple |
| 4 | `concatenateArrays` | Generics with rest parameters |
| 5 | `Course`, `getPopularCourses` | Interface and array filtering |
| 6 | `pluckValues` | Generics with `keyof` constraint |
| 7 | `Employee`, `Manager` | Classes, inheritance, access modifiers |
| 8 | `validateAgeAsync` | Promises and async/await |

There are no `console.log` statements or sample test calls in `solutions.ts`, as required by the assignment rules. Every function returns its value instead of printing it.

## Blog posts

- `generics-with-promises.md` — How generics work in TypeScript and how `Promise<T>` keeps asynchronous code type safe, with a real-life analogy and common use cases.
- `union-and-intersection-types.md` — Practical use of union (`|`) and intersection (`&`) types, how they are combined in real code, with a real-life analogy and common use cases.

## How to run

Type check the file:

```bash
npx tsc --noEmit
```

Run it with tsx (Node.js 18+ required):

```bash
npx tsx solutions.ts
```

Since the file only declares functions, classes and interfaces, running it produces no output. To see a result, call a function from a separate test file, for example `console.log(multiplyValue(10, 5))`.
