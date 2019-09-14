# What's in the project

We are going to be looking at the `src` directory, but first:

## tsconfig.json

This file contains the config for the TypeScript compiler; here's couple of interesting lines to check out:

```json
"target": "es5"
```

Version of JavaScript standard to compile to. ES5 is fine for semi-modern browsers,
ES6 can be used for controlled environments (like node).

```json
"strict": true
```
Enables 4 flags:

- `alwaysStrict` - enables JavaScript strict mode for every emitted file
- `strictNullChecks` - forces better checks for `null`/`undefined`
- `noImplicitAny` - forces typing for variables/arguments
- `noImplicitThis` - forces typing for `this`, [preventing](https://github.com/facebook/react/issues/5040) [context](https://stackoverflow.com/questions/33973648/react-this-is-undefined-inside-a-component-function) [sheningans](https://stackoverflow.com/questions/47626045/typeerror-this-is-undefined-react-js-javascript)

:warning: Personal opinion: should be turned on for ALL new projects,
but it's probably a good idea to turn this option to false for existing codebases.

## src/App.css

Styles for the `App` component.

## src/App.test.tsx

Unit tests for the component.

## src/App.tsx

Finally, the component file itself. There's some code written already that we'll replace. 

- capital "A" - all component names (and filenames) should be written in upper camel case, without any pre- or suffixes. ( :warning: according to AirBnB style-guide )
- `export default App;` - default exports are a standard practice for React.
- `return ( ...` - allows for better formatting

By the way, `.tsx` stands for TypeScript + JSX.

## src/index.tsx

Entry point of the whole operation, starts our React app with the `ReactDOM.render` line. 
This is where most of the global stuff, like global styles, should go. 

## src/index.css

Global styles

## src/logo.svg

Not interesting in itself, but why here and not in `/public` directory? `/public` contains only truly static assets,
while importing them into the component file allows for easier usage and webpack transformations.

## src/react-app-env.d.ts

Typings for the React environment internals. 
Not interesting from the app development standpoint, but removing it will break the project.

## src/serviceWorker.ts

Contains the code for a default service worker enabling PWA style app. 
Also, all files that don't contain components should be named using the lower camel-case style.

### Resources

- [Strict mode](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Strict_mode)
- [strictNullChecks](https://basarat.gitbooks.io/typescript/docs/options/strictNullChecks.html)
- [noImplicitAny](https://basarat.gitbooks.io/typescript/docs/options/noImplicitAny.html)
- [noImplicitThis](https://www.logicbig.com/tutorials/misc/typescript/no-implicit-this.html)
- [AirBnB Style Guide](https://github.com/airbnb/javascript/tree/master/react#naming)

