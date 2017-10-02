## Arrow Functions

"function", "function", "function"... Are you tired of writing that word? So are we. The arrow function `=>` is a more concise syntax for declaring functions. It looks like a little rocket arrow, in fact, and something that cool isn't usually in JavaScript. Arrow functions are not _only_ different in syntax, however - their scope is also different from a regular `function` declaration.

### Basic Syntax

Using the function keyword, to create a function that adds two to an argument, you'd write:

```javascript
function addTwo(num) {
  return num + 2;
}
```

> Here, we are naming our function `addTwo` and it takes in one parameter, `num`.

Using arrow syntax, you'd write:

```javascript
var addTwo = num => {
  return num + 2;
}
```

> Here, we declare our function as a variable: `var AddTwo`. To pass in the variable, we put it after an equal sign: `var addTwo = num`. Then we have the arrow function and the actual function definition.

If there are multiple parameters passed into an arrow function, you put them in parentheses, just like a traditional function. Before, using the function keyword, you would write:

```javascript
function multiply(x, y) {
  return x * y;
}
```

With the arrow syntax, it's:
```javascript
var multiply = (x, y) => {
  return x * y;
}
```

#### Do you remember `const`?
Anything that was a `var` in ES6 is better practice to write as a `let` or a `const`.
You can write functions using `const` or `let` as well. This can be helpful to know that the function's assignment later cannot change (in the case of `const`) or explicitly declared as can (in the case of `let`). Using `let` or `const` with a function is not necessary, but in some cases it's good practice (more on that later).

So now with the arrow syntax, we had:
```javascript
var addTwo = num => {
  return num + 2;
}
```
And we can simply change the `var` to a `const`.
```javascript
const addTwo = num => {
  return num + 2;
}
```
Another thing to note is that if the function does nothing except a return, we can simplify it even further. All of these function declarations are valid:

```javascript
// traditional
function addTwo(num) {
  return num + 2;
}

// arrow syntax
const addTwo = num => {
  return num + 2;
}

// now even further simplified
const addTwo = num => num + 2;
```
> note that we dropped the curly braces and `return` keyword

You can play with arrow functions in [this CodePen](https://codepen.io/SuperTernary/pen/qjQPzY). Remember, you can also use ES6 syntax in the Chrome dev-tools console, and your Create React App projects are transpiled with Babel, so you can use ES6 there too.
