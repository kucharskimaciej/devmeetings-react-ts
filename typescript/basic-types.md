# Basic types

[![Edit divine-worker-p713i](https://codesandbox.io/static/img/play-codesandbox.svg)](https://codesandbox.io/s/divine-worker-p713i?fontsize=14)

Basic (primitive) types in JavaScript are `String`, `Number`, `Boolean`, `null`, `undefined`, and `Symbol`.

Types in TypeScript add couple more: `any`, `void`, and `never`. Let's add some types to the code!

```typescript
let baz: any = "hello";
baz = 12;
```

The `any` type is the default value for any variable or argument: this behaves exactly like JavaScript.

```typescript
const foo: number = 12;
const bar: boolean = false;
const title: string = "Hello, Devmeetings!";

const onlyThisVerySpecificString: "specific string" = "specific string";
```

## Unions

The last one is quite fun: the variable can only have one particular value, everything else will throw an error. Let's make this useful:

```typescript
const eventType: "workshop" | "boring" = "workshop";
```

Now the `eventType` variable can only have one of the two values. This is called a **union type** and can be used with all types:

```typescript
let numberOrString: number | string;
```

## Built-in types

There is some more complex built-in types that we can use:

```typescript
const start: Date = new Date();
const e: Error = new Error("boo!");
```

## Arrays

It's also possible to tell TypeScript that we expect an array of some elements:

```typescript
const numbers: number[] = [1, 2, 3] 
```

We can also provide types for individual elements in an array (`tuple` types):

```typescript
const tuple: [string, number] = ["hello", 42]
```

Tuples require an exact number of elements at exact positions.

## Custom types

We can declare custom types using the `type` keyword:

```typescript
type EventType = "workshop" | "boring";
```

And then use them in same way as any other type:

```typescript
const eventType: EventType = "workshop";
const resultTuple: [EventType, number] = ["boring", 1337]
```

### Resources

- [Basic types](https://www.typescriptlang.org/docs/handbook/basic-types.html)
