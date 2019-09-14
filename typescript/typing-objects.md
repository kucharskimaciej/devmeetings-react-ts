# Object types

Typing objects is just as simple as typing primitive values:

```typescript
type Profiler = {
    logger?: string;
    start: Date;
    done(info?: string): boolean;
    run: () => void;
}
```

Properties of an object can be marked as optional with the `?`.

## Combining object types

Those types have common fields: `_id`, `price`, and `category`.

```typescript
type Book = {
    _id: string;
    price: number;
    category: number;
    title: string;
    description: string;
}

type Pen = {
    _id: string;
    price: number;
    category: number;
    brand: string;
    type: string;
}
```

Let's create a separate type for the common properties and rewrite the types:

```typescript
type Product = {
    _id: string;
    price: number;
    category: number;
}

type Book = Product & {
    title: string;
    description: string;
}

type Pen = Product & {
    brand: string;
    type: string;
}
```

## Interfaces

Interfaces are another way of creating custom types.

```typescript
interface IProduct {
    _id: string;
    price: number;
    category: number;
}

interface IBook extends IProduct {
    title: string;
    description: string; 
}

interface IPen extends IProduct {
    brand: string;
    type: string;    
}
```

There are some very minor differences between `type aliases` and `interfaces`. 
In general `interfaces` seem to be more suitable for object-oriented code with classes.


### Resources

- [Handbook: Interfaces](https://www.typescriptlang.org/docs/handbook/interfaces.html)
- [Handbook: Type aliases](https://www.typescriptlang.org/docs/handbook/advanced-types.html#type-aliases)
- [Interface vs Type alias](https://medium.com/@martin_hotell/interface-vs-type-alias-in-typescript-2-7-2a8f1777af4c)
