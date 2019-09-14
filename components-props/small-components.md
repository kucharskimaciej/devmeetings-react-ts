# Small components

The first rule of all best practices in programming is **keep it simple**. 
The shorter the code is, generally, the easier it is to understand and reuse. This holds true in React and having two small components that do one thing, and one thing only, 
is usually way better than having a larger component that needs to handle both of those responsibilities. 

Without experience in React or similar libraries/frameworks we usually underestimate just how **small** the components should be.

## Standard example

The images below are [shamelessly stolen from React docs](https://reactjs.org/docs/thinking-in-react.html). Here's a simple app, much like the one we'll develop:

![simple app mock](/assets/thinking-in-react-mock-1.png)

And here's how guys at Facebook would split it into components:

![simple app components](/assets/thinking-in-react-components.png)

It this too much? Probably. Way to much? Definitely not!

## When to create a new component?

There's no arbitrary number of lines that make the component too big. It comes down to intuition and experience, but try to ask the following questions:

- what does the component do? If your answer is something along the lines of `it does A and B`, you probably should split it into two components that do `A` and `B`.
- can I use this code somewhere else? If the answer is yes, then consider extracting the reusable piece into separate component.
- is this going to be hard to test? Again, if you've answered yes, split into simpler components.

And when in doubt... create a new component!

### Resources

- [Thinking in React](https://reactjs.org/docs/thinking-in-react.html)
- [Facebook has 30000 components](https://github.com/facebook/react/issues/9463#issuecomment-295643228)
