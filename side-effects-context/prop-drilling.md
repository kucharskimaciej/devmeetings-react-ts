# Prop drilling

Prop drilling is a problem that is not unique to React: when the component tree gets bigger there's an issue of passing unwanted data through multiple components even though its only required by one of them.

![distant components](/assets/distant_components.png)

## Solutions

Until recently the `context` was an unofficial API, used mostly by libraries, so regular users chose more advanced state management solutions, like Flux, Redux, and MobX.

In result, those libraries were overused and installed even in smaller projects they were not exactly meant for.

With the introduction of React Hooks the `context` API became official and standardized.

### Resources

- [React Anti-Pattern: Prop-Drilling](https://codeburst.io/react-anti-pattern-prop-drilling-54474d5236bd)
- [Prop drilling is not discouraged](https://twitter.com/dan_abramov/status/1021849622002782208)
