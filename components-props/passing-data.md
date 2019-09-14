# Passing data to components

Let's take a look at the `App` component we've created earlier:

```jsx
const App: React.FC = () => {
    const product = {
      name: "JavaScript: The Definitive Guide",
      description: `Since 1996, JavaScript: The Definitive Guide...`,
      price: 28.89
    }
    
    return (
        <section>
            <h1>Hello DevMeetings!</h1>
    
            <div>
                <header>{ product.name }</header>
                <p>
                    { product.description }
                </p>
                <span>{ product.price }$</span>
            </div>
        </section>
    )
}
```

It's simple, but there still is *some* complexity: 

- some (primitive) state inside, 
- title displayed
- product displayed

First target for extraction should be the code that is responsible for displaying a product.

## The product component

After some copy-pasting, here's the extracted `SingleProduct` component:

```jsx
const SingleProduct: React.FC = () => {
    return (
        <div>
            <header>{ product.name }</header>
            <p>
                { product.description }
            </p>
            <span>{ product.price }$</span>
        </div>
    )
}
```

The problem here is of course that the `product` variable is in the `App` component and undefined in the `SingleProduct` component. 
We need to be able to pass data from a parent (`App`) to the child (`SingleProduct`). If we were talking about functions, and not components it would look more or less like that:

```typescript

function SingleProduct(product: Product) {
    /* ... */
}

function App() {
    const product = { /* ... */ };
    
    SingleProduct(product);
}
```

This is a terrible piece of pseudo-code, but it illustrates the idea: we want to be able to pass arguments to the `SingleProduct` function.

## Props

The proper way of passing data down the component tree (from parent to child) is through props. They embody the same concept as function above, just use different syntax:

```jsx
<Component foo={42} bar={"Hello, Devmeetings"} /> 
```

That's it - we just passed two pieces of data into the `Component`: `foo` that is equal to `42`, and `bar`: the string `"Hello, Devmeetings"`. 

Let's get back to the function analogy for a second. Defining it like this would make no sense:

```typescript
function Component(foo: number, bar: string) {
    /* ... */
}
```

In this case we are entirely reliant on the order of arguments, and their names don't matter event though we typed them. This is much better:

```typescript
function Component(props: { foo: number; bar: string; }) {
    /* ... */
}
```

## Component with props

This is exactly what happens in React:

```jsx
const SingleProduct: React.FC = (props: { product: Product }) => {
    return (
        <div>
            <header>{ props.product.name }</header>
            <p>
                { props.product.description }
            </p>
            <span>{ props.product.price }$</span>
        </div>
    )
}
```

We can even improve the component's code, so it's easier to use:

```jsx
export type SingleProductProps = { product: Product };

const SingleProduct: React.FC<SingleProductProps> = ({ product }) => {
    return (
        <div>
            <header>{ product.name }</header>
            <p>
                { product.description }
            </p>
            <span>{ product.price }$</span>
        </div>
    )
}
```

Much better! With couple of simple changes, we gained:

- understanding that the `React.FC` is a generic type we got better type safety and IDE support,
- by destructuring the `props` argument simplifies code inside the component,
- by extracting the `SingleProductProps` into a type we got a minimalistic documentation

### Resources

- [Components and props](https://reactjs.org/docs/components-and-props.html)
