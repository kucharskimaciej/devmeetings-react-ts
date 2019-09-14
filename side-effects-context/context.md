# Context

The context API is designed to contain data that is common for a number of components in the application. Data in top-level context can be considered global.

## Creating context

The context object will be required to both write and read data in the context. It's best to have it in a separate file.

```typescript
import React from "react";

export const MessageContext = React.createContext("Hello!")
```

The `createContext` method takes an optional default value and returns the context object that contains both the `provider` (write data) and `consumer` (read data) bits:

```typescript
interface Context<T> {
    Provider: Provider<T>;
    Consumer: Consumer<T>;
    displayName?: string;
}
```

## Using the context

The easiest way to use context is the `useContext` hook:

```jsx
import React, { useContext } from "react";
import MessageContext from "./message-context";

const Message: React.FC = () => {
  const message = useContext(MessageContext);

  return <h1>{message}</h1>;
};

export default Message;
```

Given the Context object created earlier, the `useContext` hook returns the current context's value.

## Providing values

The above code will work without any modifications - it will just show the default value provided when creating the context.

Using the `Context.Provider` component its possible to provide a different value:

```jsx
import MessageContext from "./message-context";
import Message from "./Message";

function App() {
  return (
    <MessageContext.Provider value="Hello, Devmeetings">
      <Message />
    </MessageContext.Provider>
  );
}
```

[![Edit nervous-tharp-1eh3u](https://codesandbox.io/static/img/play-codesandbox.svg)](https://codesandbox.io/s/nervous-tharp-1eh3u?fontsize=14)

### Resources

- [Docs: Context](https://reactjs.org/docs/context.html)
- [Docs: `useContext` hook](https://reactjs.org/docs/hooks-reference.html#usecontext)
- [How the `useContext` Hook Works](https://daveceddia.com/usecontext-hook/)
