# Functional Components: Exercise!

Now that we've learned about functional components, is there any place we can apply them?

Look through the projects you've done so far. Are there any places you could use a functional component?

Let's do one together. Open your to-do list project.

Look at your `ListItem.js`. All it does is return JSX. This is prime functional component material.

First, rewrite `ListItem.js` to be a functional component.

```javascript
import React, { Component } from 'react';
import './App.css';

const ListItem = props => (
  <div>
    <li>{props.doThis}</li>
  </div>
)

export default ListItem


```

All that has changed is that `ListItem` now looks much more like a function than a component. However, `ListItem` is still a component - it returns JSX of UI to be rendered to the virtual DOM - therefore, we still need to export it (so we can call it from `App.js`), and we still need the `import` statements - a React component won't work without React!

What else in your projects can you change?

Check for more information on the next page!
