# JSX

JSX is the small language that handles rendering of React elements. Internally all the tags are replaced with calls to `React.createElement`, so this:


```jsx
const workshopTitle = <p>Devmeeting React + Typescript</p>;
```

becomes this:

```jsx
const workshopTitle = React.createElement('p', {}, "Devmeeting React + Typescript");
```

This comes with couple of problems or gotchas, first of which is why you need to import React in every component file, even when you don't reference it directly. 
This kind of goes away when using TypeScript, because more than likely the component will be typed with `React.FC`, which makes it harder to forget to import React at all.

## Almost like HTML

Because the JSX code we write compiles into JavaScript, there are some reserved keywords that you can't just use in your code. 
Unfortunately, some of those keywords are quite useful in HTML code, like `class`. In JSX we use `className` instead. 

Here's a list of keywords we might run into, and their replacements:

- `class` becomes `className`,
- `for` (used on labels to indicate which input they describe) should be replaced with `htmlFor`,
- `tabindex` becomes `tabIndex` (capital 'I'),
- `checked` works differently, for normal behavior use `defaultChecked`,
- `onclick`, `onchange`, ... -> `onClick`, `onChange`

Other differences:

- all attributes are case sensitive and have to be `camelCased`, no hyphens,
- all elements can be self closing, if they have no children (so `<div />` is legal),
- `style` attribute takes and object of css-like properties (`{ backgroundColor: blue }`)

## Interpolation

Everything that goes between `{` and `}` will be evaluated as an JavaScript expression:

```jsx
const titleClass = "workshop__title";
const workshop = {
    name: "Devmeeting React + Typescript"
};

<h2 className={titleClass}>{ workshop.name }</h2>
```

That also means that:

- `if` *statement* is not allowed, but a ternary *expression* (`condition ? whenTrue : whenFalse`) is OK
- `function` *statement* cannot be used, but arrow function *expression* can
- `for` loops are *statements*, calling `.map` is an *expression*

## Gotcha with TypeScript

There's an issue with JSX and TypeScript where casting using the bracket notation 
(like this: `(<string>foo).toLowerCase()`) causes cryptic and hard to track errors,
basically interpreting the `<X>` casting operator as part of the JSX code and attempts to transform it into `React.createElement` call.

For this reason TypeScript introduced a new casting operator `as`, ie: `(foo as string).toLowerCase()`,
that should be always used instead of the bracket notation.


### Resources

- [Introducing JSX](https://reactjs.org/docs/introducing-jsx.html)
- [JSX in Depth](https://reactjs.org/docs/jsx-in-depth.html)
