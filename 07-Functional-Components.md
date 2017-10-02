# Functional Components

Functional components give you a simpler way of declaring React components. React **class** components give you properties that you don't always need, namely state, methods like `setState`, lifecycle methods like `componentDidMount` and `componentWillReceiveProps`, `refs` and more.

Some components are purely presentational. They take props and render UI. As a React class, these components usually just contain a `render` method.

Rather than create them as classes, you can write them as functions. A React Functional Component takes the `props` object as its argument and returns JSX. Here's a very simple example.

As a class, we might have:


```javascript
class Name extends React.Component {
  render() {
    return (
      <div>
        Name: {this.props.firstName} {this.props.lastName}
      </div>
    )
  }
}
```

But with ES6, we now have:

```javascript
const Name = props => (
  <div>
    Name: {props.firstName} {props.lastName}
  </div>
)
```

> The whole declaration of `class`, `extends`, `React.component`, etc - it's all been replaced. We now just have the component name, an input for the `props`, and what is returned. Simplicity at its finest!

Functional components don't have to be "simple" - they can contain all kinds of logic. They're just JavaScript functions - so they can be as simple or complex as we make them. Let's make a more complicated example. What if we wanted a table of fruits?


`FruitTable` will render a table that looks something like this:

![Rendered fruit table](./assets/fruit-table.png)


This component written as a class, as we're used to, would look like this:

```javascript
class FruitTable extends React.Component {

  render() {
    return (
      <table style={{ borderSpacing: 20, borderStyle: 'solid' }}>
        <tbody>
          {this.props.data.map((fruitList, index) => (
            <tr key={index}>
              {fruitList.map((fruit, i) => (
                <td key={i}>
                  {fruit}
                </td>
              ))}
            </tr>
          ))}
        </tbody>
      </table>
    )
  }
}
```

The thing is, using a class here doesn't give you any benefits over a Functional component. The class literally only has a render and a return, so all it really does is requires you to write a few more lines of code.

* _A quick note on the `key`s in this example - When you render an array of items in React, you need to give each member of the array a unique `key`. React uses these keys to optimize changes to the DOM._

What if we rewrite this as a Functional Component?

```javascript

const FruitTable = props => (
  <table style={{ borderSpacing: 20, borderStyle: 'solid' }}>
    <tbody>
      {props.data.map((fruitList, index) => (
        <tr key={index}>
          {fruitList.map((fruit, i) => (
            <td key={i}>
              {fruit}
            </td>
          ))}
        </tr>
      ))}
    </tbody>
  </table>
)

const data = [
  ['apple', 'banana', 'cherry'],
  ['grape', 'pear', 'orange'],
  ['plum', 'watermelon', 'canteloupe'],
]

const App = () => <FruitTable data={data} />

ReactDOM.render(<App />, document.getElementById('app'))

```

[Try it yourself in this CodePen](https://codepen.io/SuperTernary/pen/BZGmya?editors=001).

So, when should you use Functional Components, and when should you use Class Components?

If:

- you don't need anything special
- if you are purely just returning JSX to render something

Use a functional component. But:

* If you need your component to be stateful - that is, if you need the ability to use `setState` to respond to changes -- use a class.
* If you need lifecycle methods - if you need to do something when the component mounts, or receives `props`, or unmounts -- use a class.
* If you need a `ref` -- that is, a reference to the DOM element rendered by the component - use a class.

And only if you _don't_ need any of those things -- use a Functional Component.

Functional Components are a great example of what people talk about when they say that React is "declarative", or gives us a declarative API. Rather than telling the DOM _how_ to render the UI we want - which nodes to change and how - we can use JSX to "declare" how we want the markup to look, and React alters the DOM accordingly.
