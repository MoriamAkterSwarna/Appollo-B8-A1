# Combining Union (|) and Intersection (&) Types in TypeScript

TypeScript gives us two operators to combine types, and they do opposite jobs. A union (|) means a value can be one of several types, and an intersection (&) means it must satisfy every type at once.

## Real-life analogy

A union is like a wallet slot that takes either cash or a card, one at a time. An intersection is like a job form that lists every requirement at once.

## Union types

```ts
function printId(id: string | number): void {
  if (typeof id === "string") console.log(id.toUpperCase());
  else console.log(id.toFixed(2));
}
```

The parameter takes a string or a number, not both. typeof narrows it before any method is used.

## Intersection types

```ts
interface Author {
  name: string;
}

interface Stats {
  views: number;
}

type Article = Author & Stats & { title: string };
```

An Article needs every property from all three parts. Nothing is optional.

## Using both together

An API result is usually a union of two object shapes.

```ts
type Result<T> =
  | { ok: true; data: T }
  | { ok: false; error: string };
```

Here | says success or failure, while & adds fields to a base type.

```ts
type WithId<T> = T & { id: string };
type UserRecord = WithId<{ email: string; isActive: boolean }>;
```

UserRecord ends up with id, email, and isActive in one object.

## Where you use it

Unions cover form fields, theme names and status values like null. Intersections suit configuration objects, database rows and merged request payloads.

## Conclusion

Use a union when a value can be one of a few shapes, and an intersection when it must carry every property of several shapes. Real data often needs both.
