React Tutorial
===

- [W3Schools React Tutorial](https://www.w3schools.com/REACT/DEFAULT.ASP)
- Windows 10 up

## Installation - Node.js

1. Download [Node.js LTS](https://nodejs.org/en/)

2. Check `Node.js` version

    ```bash=
    node -v
    ```

3. Check `npm` version

    ```bash=
    npm -v
    ```
    
## Installation - React

1. Project creation

    ```bash= 
    npm install -g create-react-app
    create-react-app {project_name} # ex:create-react-app react-t 
    cd {project_name} # ex:cd react-t
    ```
    
2. Run project

    ```bash=
    npm start {project_name}
    ```
    
3. Creat successfully

## React Introduction

React, sometimes referred to as a frontend JavaScript framework, is a JavaScript library created by Facebook.

- React is a JavaScript library for building user interfaces.
- React is used to build single-page applications.
- React allows us to create reusable UI components.
- **React creates a VIRTUAL DOM in memory.**
- **React only changes what needs to be changed!**

### Sample Code 

src/App.js:

```javascript=
function App() {
  return (
    <div className="App">
      <h1>Hello World!</h1>
    </div>
  );
}

export default App;
```

src/index.js

```javascript=
import React from 'react';
import ReactDOM from 'react-dom/client';

const myFirstElement = <h1>Hello React!</h1>

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(myFirstElement);
```

### New root API

Before

```javascript=
import ReactDOM from 'react-dom';
ReactDOM.render(<App />, document.getElementById('root'));
```

After (React 18)
```javascript=
import ReactDOM from 'react-dom/client';
const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(<App />);
```

## React ES6

- Classes
- Arrow Functions
- Variables (let, const, var)
- Array Methods like .map()
- Destructuring
- Modules
- Ternary Operator
- Spread Operator

### Classes

```javascript=
class Car {
  constructor(name) {
    this.brand = name;
  }

  present() {
    return 'I have a ' + this.brand;
  }
}

class Model extends Car {
  constructor(name, mod) {
    super(name);
    this.model = mod;
  }  
  show() {
      return this.present() + ', it is a ' + this.model
  }
}

const mycar = new Model("Ford", "Mustang");
mycar.show();
```

The `super()` method refers to the parent class.

By calling the `super()` method in the constructor method, we call the parent's constructor method and **get access to the parent's properties and methods**.

### Arrow Functions

Before

```javascript=
hello = function() {
  return "Hello World!";
}
```

After

```javascript=
hello = () => {
  return "Hello World!";
}

hello = () => "Hello World!";
hello = (val) => "Hello " + val;
```

- With a regular function, `this` represents **the object that called the function**: (button)

```javascript=
class Header {
  constructor() {
    this.color = "Red";
  }

// Regular function:
  changeColor = function() {
    document.getElementById("demo").innerHTML += this;
  }
}
```

- With an arrow function, `this` represents the **Header object** no matter who called the function: (object)

```javascript=
class Header {
  constructor() {
    this.color = "Red";
  }

// Arrow function:
  changeColor = () => {
    document.getElementById("demo").innerHTML += this;
  }
}
```

### Variables

**`var` has a function scope, not a block scope**.

- If you use `var` outside of a function, it belongs to the global scope.
- If you use `var` inside of a function, it belongs to that function.
- If you use `var` inside of a block, i.e. a for loop, the variable is still available outside of that block.

**`let` has a block scope.**

- If you use `let` inside of a block, i.e. a for loop, the variable is only available inside of that loop.

**`const` is a variable that once it has been created, its value can never change, has a block scope.**

- It does not define a constant value. It defines a **constant reference** to a value.

you can NOT:

- Reassign a constant value
- Reassign a constant array
- Reassign a constant object

But you CAN:

- Change the elements of constant array
- Change the properties of constant object

### Array Methods

- The `.map()` method allows you to run a function on each item in the array, returning a new array as the result.
- In React, `map()` can be used to generate lists.

```javascript=
const myArray = ['apple', 'banana', 'orange'];

const myList = myArray.map((item) => <p>{item}</p>)
```

### Destructuring

- Here is the new way of **assigning array items to a variable**:

```javascript=
const vehicles = ['mustang', 'f-150', 'expedition'];

const [car, truck, suv] = vehicles;
const [car,, suv] = vehicles;
```

Destructuring comes in handy when a **function** returns an array:

```javascript=
function calculate(a, b) {
  const add = a + b;
  const subtract = a - b;
  const multiply = a * b;
  const divide = a / b;

  return [add, subtract, multiply, divide];
}

const [add, subtract, multiply, divide] = calculate(4, 7);
```

Here is the new way of **using an object inside a function**:

```javascript=
const vehicleOne = {
  brand: 'Ford',
  model: 'Mustang',
  type: 'car',
  year: 2021, 
  color: 'red'
}

myVehicle(vehicleOne);

function myVehicle({type, color, brand, model}) {
  const message = 'My ' + type + ' is a ' + color + ' ' + brand + ' ' + model + '.';
}
```

**Nested object**:

```javascript=
const vehicleOne = {
  brand: 'Ford',
  model: 'Mustang',
  type: 'car',
  year: 2021, 
  color: 'red',
  registration: {
    city: 'Houston',
    state: 'Texas',
    country: 'USA'
  }
}

myVehicle(vehicleOne)

function myVehicle({ model, registration: { state } }) {
  const message = 'My ' + model + ' is registered in ' + state + '.';
}
```

### Spread Operator

The JavaScript spread operator `(...)` allows us to quickly copy all or part of an existing **array or object** into another array or object.

```javascript=
const numbersOne = [1, 2, 3];
const numbersTwo = [4, 5, 6];
const numbersCombined = [...numbersOne, ...numbersTwo];
```

The spread operator is often used in combination with destructuring.

```javascript=
const numbers = [1, 2, 3, 4, 5, 6];
const [one, two, ...rest] = numbers;
```

We can use the spread operator with **objects** too.

```javascript=
const myVehicle = {
  brand: 'Ford',
  model: 'Mustang',
  color: 'red'
}

const updateMyVehicle = {
  type: 'car',
  year: 2021, 
  color: 'yellow'
}

const myUpdatedVehicle = {...myVehicle, ...updateMyVehicle}
```

Notice the properties that did not match were combined, but the property that did match, `color`, was **overwritten by the last object that was passed**, `updateMyVehicle`. The resulting color is now yellow.

### Modules

ES Modules rely on the `import` and `export` statements.

#### Export

Named Exports

```javascript=
const name = "Jesse"
const age = 40

export { name, age }
```

Default Exports

```javascript=
const message = () => {
  const name = "Jesse";
  const age = 40;
  return name + ' is ' + age + 'years old.';
};

export default message;
```

#### Import

```javascript=
import { name, age } from "./person.js";

import message from "./message.js";
```

### Ternary Operator

Before

```javascript=
if (authenticated) {
  renderApp();
} else {
  renderLogin();
}
```

With Ternary


```javascript=
authenticated ? renderApp() : renderLogin();
```

## React Render HTML