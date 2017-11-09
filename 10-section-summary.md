# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Section Summary


In this section, we dove deeper into React. Here's what we covered:

## ES6/ES7/ESNext

You learned to write cleaner, more concise, and more readable code with ESNext syntax:

  - `const` and `let`: `const name = 'Jim'`; `let age = 25`
  - Arrow functions: `const doStuff = stuff => stuff + 5`
  - Object literal shorthand: `const name = 'Jim', jim = { name }`
  - Template literals: ``const greet = person => `Hi, ${person.firstName} ${person.lastName}``
  - Imports and modules: `import MyModule from './MyModule'`

## Functional Components

Functional components are React components that are simply JavaScript functions. They take props as their argument and return JSX (UI!).

```javascript
const MyFunctionalComponent = props => (
  <div>
    The weather in {props.city} is currently {props.condition}. The temperature is {props.temperature}.
  </div>
)
```

## Component Lifecycle

React class components have lifecycle methods that are invoked at certain stages of a component's "life" on the DOM. Some of the lifecycle methods you'll use a lot are:

  - `constructor()`: Initialize state, bind methods
  - `componentDidMount()`: Make AJAX requests, get DOM refs, bind event listeners, set `state` if necessary
  - `componentWillUnmount()`: Unbind event listeners, other cleanup
  - `componentWillReceiveProps()`: Update `state` based on changes in components
  - `render()`: Return markup/UI

## Unidirectional Data Flow

In React, data flows from the top down. Keep your data higher in your component tree so it's available to the sibling/children components that need it.

## Immutable Data

A React component's state and props are to be treated as immutable - never change them directly.

For `state`, use `setState`:

```javascript
handleChange(event) {
  this.setState(prevState => ({
    myPieceOfState: event.target.value,
  }))
}
```

**Never change props in a component** - changes to props happen in the component that passes them down.
