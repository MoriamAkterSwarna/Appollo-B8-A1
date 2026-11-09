# Generics in TypeScript and How They Help with Promise<T>

Generics let us write code for more than one type without losing type information. Instead of fixing a type inside a function, we pass a type parameter, usually named T.

## Real-life analogy

A generic function is like a box with a blank label, because the same box carries books or clothes until sealed. TypeScript treats T the same way: one function, and each call fills in the type. A Promise<T> is the tracking receipt, since it promises arrival and also states what is inside.

## The basic idea

```ts
function identity<T>(value: T): T {
  return value;
}

const num = identity(42);
const txt = identity("hi");
```

T is a placeholder: identity(42) makes it number, identity("hi") makes it string. The compiler knows the result type, so mistakes are caught early.

## Generics with Promise<T>

Promise is generic too: Promise<string> means the value arriving later is a string.

```ts
function findUser(id: number): Promise<string> {
  return new Promise((resolve) => {
    setTimeout(() => resolve("Rakib"), 1000);
  });
}

async function show(): Promise<void> {
  const name: string = await findUser(1);
  console.log(name.toUpperCase());
}
```

Since findUser returns Promise<string>, await gives a string here. A number would be flagged before we run anything.

```ts
async function getData<T>(url: string): Promise<T> {
  const response = await fetch(url);
  return (await response.json()) as T;
}
```

Calling getData<User[]> returns Promise<User[]>, not Promise<any>.

## Where you use it

This pattern appears in API helpers, form validation and shared utilities used by many entity types. Database records, route parameters and caching layers need it too.

## Conclusion

Generics keep code reusable and fully typed, and Promise<T> tells the compiler what value arrives after await. This removes bugs that would otherwise show up at runtime.
