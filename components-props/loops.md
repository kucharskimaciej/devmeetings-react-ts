# Loops in JSX

More often than not we'll be dealing with lists and collections and not just simple singular items. 
That means we'll need to iterate over data, but there's no way to use `for` loops in JSX. Let's use `.map`.

```jsx
const App: React.FC = () => {
    const products: Product[] = [
        {
          name: "JavaScript: The Definitive Guide",
          description: `Since 1996, JavaScript: The Definitive Guide...`,
          price: 28.89
        },
        {
          name: "Eloquent JavaScript",
          description: `JavaScript lies at the heart...`,
          price: 21.22
        },
        {
          name: "JavaScript: The Good Parts",
          description: `Most programming languages...`,
          price: 16.59
        }
    ]

    return (
        <section>
            <h1>Products</h1>
            { products.map(product => (
                <div key={product.name}>
                    <header>{ product.name }</header>
                    <p>
                        { product.description }
                    </p>
                    <span>{ product.price }$</span>
                </div>
            )) }
        </section>
    )
}
```

Overall, quite straightforward: there's an array of items, over which we iterate using `.map` and return some JSX for each element.
Similar to using components, each piece of JSX returned by the `.map` transformation must have exactly one root element.

There's also the `key` property on the root element of each product. This not *strictly* required (will work, React will just complain),
but it allows React to easily distinguish between elements during the reconcilation process. Should be unique for each element in the array.

### Resources

- [Lists and keys](https://reactjs.org/docs/lists-and-keys.html)
- [Array.prototype.map()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map)
- [Reconcilation](https://reactjs.org/docs/reconciliation.html)
- [Index as a key is an anti-pattern](https://medium.com/@robinpokorny/index-as-a-key-is-an-anti-pattern-e0349aece318)
- [The significance of React keys - a visual explanation](https://dev.to/jtonzing/the-significance-of-react-keys---a-visual-explanation--56l7)
