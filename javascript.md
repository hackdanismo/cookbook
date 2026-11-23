# JavaScript
`JavaScript` files usually end with the `.js` file extension. A `<script>` tag is usually added before the closing `</body>` tag.

```html
<script src="script.js></script>
</body>
</html>
```

## Functions
`Functions` are reusable blocks of code. A `function` in `JavaScript` is usually declared with the `function` keyword followed by the name of the function, called the `identifier`.

```javascript
function boo() {
    // Code to be executed when the function is called
}

// Call the function to execute the code block
boo();
```

`Functions` can also be writted using `arrow function` syntax:

```javascript
const boo = () => {
    // Code to be executed when the function is called
}

// Call the function to execute the code block
boo();
```

A function can be written in shorthand, as with this `multiply` example, without the brackets:

```javascript
const multiply = (x, y) => x * y;
```

If a function has a single `parameter`, such as `name` in this example, the brackets can be removed.

```javascript
const sayHello = name => console.log("Hello, " + name);
```

Using a `template literal` and removing the braces around a single `parameter` in the function can make the syntax easier to read.

```javascript
const sayHello = name => console.log(`Hello, ${name}`);
```

### Parameters and Arguments
In `JavaScript`, `parameters` are variables that allow you to pass information into a function. Think of `parameters` as placeholders for values that a function will use when it runs. In this example, the `parameter` is `name`. A function can have multiple `arguments` and `parameters`. If a function has more than one `parameter`, braces are needed.

```javascript
const boo = (name, age) => {
    console.log(`Hello, ${name}. You are ${age} years old.`);    // Hello, Dan. You are 41 years old.
}

// Call the function to execute the code block
boo("Dan", 41);
```

Default `parameter` values can be used in-place of values being passed as `arguments` so should a function be called without a value passed, the default value will be used.

```javascript
// Use the default parameter values of "Peat" and 9
const boo = (name = "Peat", age = 9) => {
    console.log(`Hello, ${name}. You are ${age} years old.`);    // Hello, Peat. You are 9 years old.
}

// Call the function to execute the code block without values/arguments
boo();
```

### IIFE
An `IIFE (Immediately Invoked Function Expression)` is a `JavaScript` function that executes immediately after it is defined, without needing to call it separately. We don't need to call the function separately. It executes automatically.

```javascript
(() => {
    console.log("This is an IIFE.");
})();
```

This can also be writted with the `function` keyword instead of the arrow function syntax:

```javascript
(function () {
    console.log("This is an IIFE.");
})();
```

Just like regular functions, an `IIFE` can accept parameters.

```javascript
((name, age) => {
    console.log(`Hello, ${name}. You are ${age} years old.`);
})("Peat", 9);
```

One important reason to use an `IIFE` is to keep `variables` private to the function, so they don't interfere with variables outside it. The message `variable` only exists inside the `IIFE`.

```javascript
(() => {
    // This is a private variable and only available from inside the IIFE
    const message = "Hello, Peat!";
    console.log(message);
})();

console.log(message); // ReferenceError
```
