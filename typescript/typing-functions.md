# Functions

When declaring a function we can type both the arguments and the return value:

```typescript
function multiply(a: number, b: number): number {
    return a * b;
}
```

## Reusable function type

Let's say the above function implements a very common pattern in out app: do some calculation with two numbers.

```typescript
function sum(a: number, b: number): number {
    return a + b;
}

function modulo(a: number, b: number): number {
    return a % b;
}
```

We can create a function type:

```typescript
type BinaryOperator = (a: number, b: number) => number;
const subtract: BinaryOperator = (a, b) => a - b;
```

## The `void` type

One type is particularly useful with functions is `void`: to signify that nothing will be returned from the function:

```
function log(message): void {
    console.log(message);
}
``` 

## Optional and default arguments

Function arguments can be marked as optional using the `?` sign

```typescript
function done(error?: Error): void {
    /* ... */
}
```

We can also provide a default value; any argument with a default value will automatically be marked as optional.

```typescript
function complete(success: boolean = true): void {
    /* ... */
}
```

### Resources

- [Handbook: Functions](https://www.typescriptlang.org/docs/handbook/functions.html)
