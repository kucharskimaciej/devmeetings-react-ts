# Talking to a parent component

We learned earlier that parent passes data to a child component by using `props`. What about the other way around? 
Like a function, the child has no idea who called it and so it cannot pass data to the caller (with exception of returning the data). 

Solution is the same for both functions and React components: let's pass a callback as one of the arguments.

```jsx
type CounterProps = { increment: () => void; decrement: () => void; }

const Counter: React.FC<CounterProps> = ({ increment, decrement }) => {
    return (
        <div>
            <button onClick={increment}>+</button>
            <button onClick={decrement}>-</button>
        </div>
    )
}
```

```jsx

const App: React.FC = () => {
    const [count, setCount] = useState<number>(0)
    
    const onIncrement = () => setCount(count + 1)
    const onDecrement = () => setCount(count - 1)

    return (
        <div>
            { count }
            <Counter increment={onIncrement} decrement={onDecrement} />
        </div>
    )
}
```

[![Edit talking with parent](https://codesandbox.io/static/img/play-codesandbox.svg)](https://codesandbox.io/s/peaceful-wood-mlh9k?fontsize=14)
