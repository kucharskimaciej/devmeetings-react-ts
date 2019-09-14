# State

Let's do a little bit more with the button. Let's make it count clicks.

![count clicks](/assets/click_count.gif)

## Naive implementation

```jsx
const Clicker: React.FC = () => {
    let clicks = 0;
    const handleButtonClick = () => {
        clicks++;
    }

    return (
        <button onClick={handleButtonClick}>Clicked { clicks } times</button>
    )
}
```

[![Edit bad clicker](https://codesandbox.io/static/img/play-codesandbox.svg)](https://codesandbox.io/s/working-clicker-lri99?fontsize=14)

Boom, done. Except is doesn't work, because React has no idea that it should rerender the `Clicker` component or keep track of the `clicks` variable.

## Using the `useState` hook

Current **Industry Best Practice ™** for keeping track of the state. Previously, we would use class components, but hooks have some advantages over them.

```jsx
import React, { useState } from "react"

const Clicker: React.FC = () => {
    const [clicks, setClicks] = useState<number>(0)
    const handleButtonClick = () => {
        setClicks(clicks + 1)
    }

    return (
        <button onClick={handleButtonClick}>Clicked { clicks } times</button>
    )
}
```

[![Edit working clicker](https://codesandbox.io/static/img/play-codesandbox.svg)](https://codesandbox.io/s/stupefied-dawn-y5bdl?fontsize=14)

## Resources

- [Docs: State](https://reactjs.org/docs/faq-state.html)
- [Docs: `useState` hook](https://reactjs.org/docs/hooks-state.html)
- [`useState` hook examples](https://daveceddia.com/usestate-hook-examples/)
