
### Implicit return

Continuing a thought, the last thing we noted is that if the function does nothing except a return, we can simplify it even further:

```javascript
const addTwo = num => num + 2;
```
> We dropped the curly braces and `return` keyword.

If there is no block following the arguments of an arrow function (meaning nothing in `{ }` curly braces), whatever follows is the return value of the function. The `addTwo` example above simply returns the value of `num + 2`. This is called an **implicit return**.
```js
const addTwo = num => num + 2;
```
**Importantly**, we can only use implicit return for functions which only contain a `return` statement.

Consider these two functions.

- `addTwo` can be simplified to one line, as it's just a `return` statement.
- `mutateNumbers` contains more than just a return statement, so we still need the curly braces.

```javascript
const addTwo = num => {
  return num + 2;
}

// The same with implicit return
const addTwo = num => num + 2;

// Cannot have implicit return
const mutateNumbers = num => {
  newNum = 6;
  alert(newNum);
  return num + newNum;
}
```

Using implicit returns can shorten our syntax and make our code more readable. The following function `lowercaseListOfWords` takes one argument- an array of strings- and returns a new array of lowercase strings.

Written with functions, this would look something like:

```javascript
function lowercaseListOfWords(arrayToModify) {
  return arrayToModify.map(function(word) {
    return word.toLocaleLowerCase();
  });
}
```

However, using ES6, the arrow function, and implicit returns, we can make that one (albeit long!) line:

```javascript
const lowercaseListOfWords = arrayToModify => arrayToModify.map(word => word.toLocaleLowerCase());
```

**Importantly**, one gotcha to be aware of with implicit returns is that object literals must be wrapped in parentheses, so the interpreter (browser, compiler, etc.) can distinguish them from blocks. An example:

```javascript
const isItActive = isActive => ({ active: isActive });
```

> This function only returns one thing, but because it implicitly returns an object literal, it must be wrapped in parentheses.

Play around with implicit returns from arrow functions [in this CodePen](https://codepen.io/SuperTernary/pen/ZymXgK?editors=001).

### This binding - and the lack thereof

So - now that we've learned all the fun syntax of the arrow function, let's talk about the benefits of actually using it.

In non-arrow functions, every function defines its own `this`. There are tons of hacks to preserve the context, like `var that = this` and using `.bind(this)`. This might look familiar:

```javascript
function eatBreakfast(pancakes) {
  var that = this;
  that.food = 'Knife please?';
  Waiter.bringCutlery(function (silverware) {
    that.food = silverware;
  });
}
```

Another popular variant is `var self = this`. Whatever hack you've been using, you don't need to do it anymore!

Arrow functions don't change the definition of `this`. So, if `this` is already defined in the scope, and you call an arrow function, you can access `this` directly.

```javascript
// Original function
function eatBreakfast(pancakes) {
  var that = this;
  that.food = 'Knife please?';
  Waiter.bringCutlery(function (silverware) {
    that.food = silverware;
  });
}

// Equivalent arrow function
const eatBreakfast = pancakes => {
  this.food = 'Knife please?';
  Waiter.bringCutlery((silverware) => this.food = silverware);
}
```
> Check it out - the arrow function can be anywhere you declare a function!
