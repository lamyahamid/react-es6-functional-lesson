# Functional Components: Solution

Not only can the `ListItem` be converted into a functional component. The
entire `ToDoList` can be its own functional component as well. Here is `ListItem`.

```js
import React, { Component } from 'react';
import './App.css';

const ListItem = props => (
  <div>
    <li>{props.doThis}</li>
  </div>
)

export default ListItem
```

Make a new file called `ToDoList.js` and have it look very much like the
`const ListItem` functional component above. It should have the following
properties:

* Define as `const ToDoList` similar to `ListItem`.
* Import `ListItem` because it will render `ListItems`.
* Accept `props` like `ListItem`.
* Expect there something called `toDoItemArray` attached to props.
* Use `props.toDoItemArray.map(item, index)` to iterate over each item.
* Render `<ListItem>` components inside the map.
* Pass the proper properties (`doThis` and `key`) to the `<ListItem>` component

The syntax of getting the mapping to work can be tricky. Notice that it must
be surrounded in curly braces, like the fruit list example that uses `.map()`
to generate a table.

All in all, the functional `ToDoList` component should look like this:

```js
import React from 'react';
import ListItem from './ListItem';

const ToDoList = props => (
  <ul>
    {props.toDoItemArray.map((item, index) => (
      <ListItem doThis={item} key={index} />
    ))}
  </ul>
)

export default ToDoList
```

If you'd like to see this work, all you need to do is change your `MyList.js` to call the new component.
First, import the new `ToDoList` component and file at the top of `MyList.js`.
Then, delete the `let todoItems...` `map` method from the `render` function- you now do this in the ToDoList component.
Finally, change the call in the `return` statement from `{todoItems}` to `<ToDoList toDoItemArray={this.state.toDoItemArray} />` - calling the ToDoList component and passing in the ToDoList.

Great job! You've mastered functional components.
