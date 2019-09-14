# Smart component, dumb component

A well-written React app will have two "types" of components: **Containers**, often called **smart** and **Presentational** called **dumb**.

Before we get to that, let's introduce a couple of concepts:

## Side-effect

A side-effect of a function is anything the function does that affects any part of the system outside of the function scope.

- changing a value of a local variable is **not** a side-effect
- changing a value of a global variable is a side-effect
- making a network request is a side-effect
- changing the DOM is a side-effect
- logging to a console is a side-effect
- registering a event listener is a side-effect
- using external code might be a side-effect

## Pure function

A pure function is a function that always returns the same result given the same arguments and has no side-effects. Those are pure functions:

```typescript
const square = x => x*x

const getExpensiveBooksCount = (books) => {
    const expensiveBooks = books.filter(book => book.price > 20)
    return expensiveBooks.length
}
```

Those are not pure:

```typescript
let callCount = 0;
const square = x => {
    callCount++
    return x*x
}

const fetchBooks = () => getBooks().then(doStuffWithBooks)

const sleep = time => new Promise(resolve => setTimeout(resolve, time))
```

## Dumb components

Those components should be pure functions that receive some data from their parent using `props` and based on that return JSX element. They have no internal state, very little (or none at all) logic.

They are easy to write, easy to understand and easy to test.

## Smart components

Usually impure functions, have some internal state, make requests to server, etc. This is where the application logic and 99% of bugs are.

## In action

Let's get back to the counting `Clicker` component and split it into a smart and a dumb component:

```jsx
type ClickerProps = {
  clicks: number;
  incrementClicks: () => void;
};
const Clicker: React.FC<ClickerProps> = ({ clicks, incrementClicks }) => {
  return <button onClick={incrementClicks}>Clicked {clicks} times</button>;
};


const ClickerContainer: React.FC = () => {
  const [clicks, setClicks] = useState<number>(0);
  const handleClickerClick = () => {
    setClicks(clicks + 1);
  };

  return <Clicker incrementClicks={handleClickerClick} clicks={clicks} />;
};
```

[![Edit smart and dumb clicker](https://codesandbox.io/static/img/play-codesandbox.svg)](https://codesandbox.io/s/working-clicker-4n7f5?fontsize=14)


The `Clicker` now is only concerned about the UI - how the clicker looks. It has clearly defined API, can be changed completely, without risking breaking any logic related to state or potential side-effects. It can be reused by another component, that does something entirely different when the button is clicked.

On the other hand, the `ClickerContainer` only knows how to update the state in reaction to the `incrementClicks` event. More abstract application of this pattern is called **Higher Order Components** or **HOC** and is a primary (little outdated) tool for sharing code among React components.

## Resources

- [Presentational and Container Components](https://medium.com/@dan_abramov/smart-and-dumb-components-7ca2f9a7c7d0)

