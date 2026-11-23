# JavaScript
`JavaScript` files usually end with the `.js` file extension. A `<script>` tag is usually added before the closing `</body>` tag.

```html
<script src="script.js></script>
</body>
</html>
```

## Variables
A `variable` in `JavaScript` is used to store data that you can access and use later in your code. `JavaScript` has three keywords for declaring variables:

- `let`
- `const`
- `var`

Use `let` when you expect the value to change. Use `const` when you don't want the variable to reference a different value. Before modern JavaScript, developers commonly used `var`. `JavaScript` is **dynamically typed**, meaning you don't have to specify a variable's `data type`.

**The Recommendation:** Prefer `const` by default, use `let` when reassignment is needed, and generally avoid `var` in modern JavaScript.

```javascript
// Declare a variable using the legacy var keyword
var name = "Dan";
// Declare a variable using let as this value may change
let age = 41;
// Declare a variable using const (recommended) and this value will not change
const isMale = true;
```

### What does block scope mean?
A block is code enclosed in curly brackets `{}`. A variable inside of the brackets is block scoped. The variable message only exists inside the if block.

```javascript
if (true) {
    let message = "Hello";
    console.log(message);     // Hello
}

console.log(message);     // ReferenceError, the variable cannot be accessed outside of the block
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

Sometimes we pass global objects such as `window` and `document` into the function.

```javascript
(function (window, document) {
    // Code is executed here.
})(window, document);
```

## Class
In `JavaScript`, a `class` is a blueprint for creating objects that share the same `properties` (data) and `methods` (functions). Classes are especially useful when you want to create multiple objects that behave similarly without repeating code.

```javascript
class User {
    constructor(name, age) {
        this.name = name;
        this.age = age;
    }
}
```

- `class User` defines a class called User.
- `constructor()` is a special method that runs when you create a new object.
- `this.name` is a property belonging to the object being created.
- `this.age` is another property belonging to that object.

Now we can create users from our class. The `new` keyword creates a new instance of the class:

```javascript
const user1 = new User("John", 25);
const user2 = new User("Sarah", 30);

console.log(user1.name); // John
console.log(user2.name); // Sarah
```

Classes become more useful when you add `methods`. A `method` is simply a `function` that belongs to the class and can be used by its objects.

```javascript
class User {
    constructor(name, age) {
        this.name = name;
        this.age = age;
    }

    greet() {
        return `Hello, my name is ${this.name}`;
    }

    getAge() {
        return this.age;
    }
}
```

We can use the `methods` of a class:

```javascript
const user1 = new User("John", 25);

console.log(user1.greet());     // Hello, my name is John
console.log(user1.getAge());    // 25
```

Notice that we don't need to write `function` when defining methods inside a class.

Imagine you're building a banking application. This is a more practical example.

```javascript
class BankAccount {
    constructor(owner, balance) {
        this.owner = owner;
        this.balance = balance;
    }

    deposit(amount) {
        this.balance += amount;
    }

    withdraw(amount) {
        if (amount > this.balance) {
            return "Insufficient funds";
        }
        this.balance -= amount;
    }

    getBalance() {
        return this.balance;
    }
}
```

Now let's create an account and interact with it.

```javascript
const account = new BankAccount("John", 1000);

account.deposit(500);

console.log(account.getBalance());    // 1500

account.withdraw(200);

console.log(account.getBalance());    // 1300
```

For example, you could have a `Vehicle` class and then create a `Car` class that inherits from it using the `extends` keyword:

```javascript
class Vehicle {
    constructor(brand) {
        this.brand = brand;
    }

    start() {
        console.log("Vehicle started");
    }
}

// Create a Car class thar inherits methods and properties from the Vehicle class
class Car extends Vehicle {
    drive() {
        console.log(`${this.brand} is driving`);
    }
}

const car = new Car("BMW");

car.start();     // Vehicle started
car.drive();     // BMW is driving
```
