# JavaScript Cheatsheet: Beginner to Advanced (with Explanations)

## Beginner Level

### Variables and Data Types
```javascript
// Variable declaration
let variableName = value;  // 'let' declares a block-scoped variable
const constantName = value;  // 'const' declares a constant (can't be reassigned)
var oldStyleVariable = value; // 'var' is function-scoped (avoid using it)

// Data types
let string = "Hello";  // Textual data
let number = 42;  // Numeric data (integers and floats)
let boolean = true;  // True or false
let array = [1, 2, 3];  // Ordered list of values
let object = { key: "value" };  // Collection of key-value pairs
let nullValue = null;  // Intentional absence of any object value
let undefinedValue;  // Variable declared but not assigned a value
```
Explanation: JavaScript has several ways to declare variables and multiple data types. 'let' and 'const' are block-scoped and preferred over 'var'. Each data type serves a different purpose in storing and manipulating data.

### Basic Operators
```javascript
// Arithmetic operators
let sum = 5 + 3;  // Addition
let difference = 10 - 4;  // Subtraction
let product = 6 * 7;  // Multiplication
let quotient = 20 / 4;  // Division
let remainder = 15 % 4;  // Modulus (remainder after division)

// Comparison operators
let equal = (5 == "5");  // true (loose equality, compares value only)
let strictEqual = (5 === "5");  // false (strict equality, compares value and type)
let notEqual = (5 != "6");  // true (loose inequality)
let greaterThan = (10 > 5);  // true (greater than)
```
Explanation: Operators perform operations on variables and values. Arithmetic operators perform mathematical calculations. Comparison operators compare values and return boolean results. The strict equality operator (===) is generally preferred as it checks both value and type.

### Control Structures
```javascript
// If-else statement
if (condition) {
    // code executed if condition is true
} else if (anotherCondition) {
    // code executed if anotherCondition is true
} else {
    // code executed if no conditions are true
}

// Loops
for (let i = 0; i < 5; i++) {
    console.log(i);  // Prints numbers 0 to 4
}

while (condition) {
    // code executed repeatedly while condition is true
}

do {
    // code executed at least once, then repeatedly while condition is true
} while (condition);
```
Explanation: Control structures direct the flow of the program. If-else statements allow conditional execution of code. Loops (for, while, do-while) allow repeated execution of code blocks. The 'for' loop is often used when the number of iterations is known, while 'while' and 'do-while' are used when the number of iterations depends on a condition.

### Functions
```javascript
function functionName(parameter1, parameter2) {
    // code to be executed
    return result;  // Optional: returns a value
}

// Arrow function (ES6+)
const arrowFunction = (param1, param2) => {
    // code to be executed
    return result;
};
```
Explanation: Functions are reusable blocks of code. They can take parameters (inputs) and return values (outputs). Arrow functions provide a more concise syntax for writing function expressions, especially for simple, single-expression functions.

## Intermediate Level

### Array Methods
```javascript
let arr = [1, 2, 3, 4, 5];

arr.push(6);  // Adds 6 to the end of the array
arr.pop();    // Removes and returns the last element
arr.unshift(0);  // Adds 0 to the beginning of the array
arr.shift();  // Removes and returns the first element

let mapped = arr.map(x => x * 2);  // Creates a new array with each element doubled
let filtered = arr.filter(x => x > 2);  // Creates a new array with elements greater than 2
let reduced = arr.reduce((acc, curr) => acc + curr, 0);  // Sums all elements
```
Explanation: Array methods are powerful tools for manipulating arrays. push/pop work with the end of the array, while unshift/shift work with the beginning. map creates a new array by transforming each element, filter creates a new array with elements that pass a test, and reduce executes a reducer function on each element to produce a single output value.

### Object Manipulation
```javascript
let obj = { a: 1, b: 2 };
let keys = Object.keys(obj);  // Returns an array of the object's keys
let values = Object.values(obj);  // Returns an array of the object's values
let entries = Object.entries(obj);  // Returns an array of [key, value] pairs

// Spread operator (ES6+)
let newObj = { ...obj, c: 3 };  // Creates a new object by spreading obj and adding a new property
```
Explanation: These methods provide ways to work with object properties. The spread operator (...) is a convenient way to create new objects or arrays by expanding existing ones.

### Promises and Async/Await
```javascript
// Promise
const myPromise = new Promise((resolve, reject) => {
    // Asynchronous operation
    if (/* operation successful */) {
        resolve(result);
    } else {
        reject(error);
    }
});

myPromise.then(result => {
    // Handle success
}).catch(error => {
    // Handle error
});

// Async/Await (ES8+)
async function asyncFunction() {
    try {
        const result = await myPromise;
        // Handle success
    } catch (error) {
        // Handle error
    }
}
```
Explanation: Promises provide a way to handle asynchronous operations. They represent a value that may not be available immediately. Async/Await is syntactic sugar for working with Promises, making asynchronous code look and behave more like synchronous code.

### Classes (ES6+)
```javascript
class MyClass {
    constructor(param) {
        this.property = param;  // Initialize instance property
    }

    method() {
        return this.property;  // Instance method
    }

    static staticMethod() {
        return "I'm static";  // Static method (called on the class, not instances)
    }
}

const instance = new MyClass("Hello");
console.log(instance.method());  // "Hello"
console.log(MyClass.staticMethod());  // "I'm static"
```
Explanation: Classes provide a cleaner, more object-oriented way to create objects and implement inheritance. The constructor method is called when creating new instances. Instance methods are available on instances, while static methods are called on the class itself.

## Advanced Level

### Closures
```javascript
function outerFunction(x) {
    return function(y) {
        return x + y;  // Inner function has access to x from outer scope
    };
}

const closure = outerFunction(5);
console.log(closure(3));  // 8
```
Explanation: A closure is a function that has access to variables in its outer (enclosing) lexical scope, even after the outer function has returned. This allows for data privacy and the creation of function factories.

### Prototypes and Inheritance
```javascript
function Animal(name) {
    this.name = name;
}

Animal.prototype.speak = function() {
    console.log(this.name + ' makes a sound.');
}

function Dog(name) {
    Animal.call(this, name);  // Call the parent constructor
}

Dog.prototype = Object.create(Animal.prototype);  // Set up inheritance
Dog.prototype.constructor = Dog;  // Fix the constructor property

Dog.prototype.bark = function() {
    console.log(this.name + ' barks.');
}

const dog = new Dog('Rex');
dog.speak();  // "Rex makes a sound."
dog.bark();   // "Rex barks."
```
Explanation: This demonstrates prototypal inheritance in JavaScript. Objects inherit properties and methods from their prototype. We create a Dog constructor that inherits from Animal, showing how to set up the prototype chain and add methods specific to the child constructor.

### Modules (ES6+)
```javascript
// module.js
export const namedExport = "I'm named";
export default function() {
    return "I'm default";
}

// main.js
import defaultExport, { namedExport } from './module.js';
```
Explanation: Modules allow you to split your code into separate files for better organization and reusability. You can have named exports and a default export. When importing, you can import the default and named exports separately.

### Generators and Iterators
```javascript
function* numberGenerator() {
    yield 1;
    yield 2;
    yield 3;
}

const gen = numberGenerator();
console.log(gen.next().value);  // 1
console.log(gen.next().value);  // 2
console.log(gen.next().value);  // 3
```
Explanation: Generators are functions that can be paused and resumed, yielding multiple values over time. They're useful for creating custom iterables and handling streams of data. The `yield` keyword is used to pause the generator and return a value.

### Proxy and Reflect
```javascript
const target = { a: 1, b: 2 };
const handler = {
    get: function(obj, prop) {
        return prop in obj ? obj[prop] : 37;  // Return 37 if property doesn't exist
    }
};

const proxy = new Proxy(target, handler);
console.log(proxy.a);  // 1
console.log(proxy.c);  // 37
```
Explanation: Proxy allows you to create an object that can intercept and redefine fundamental operations for another object. This example shows a get trap that returns a default value for non-existent properties. Reflect is a related API that provides methods for interceptable JavaScript operations.

### WebAssembly
```javascript
WebAssembly.instantiateStreaming(fetch('module.wasm'))
.then(obj => {
    // Use exported functions
});
```
Explanation: WebAssembly is a binary instruction format that allows you to run high-performance code in web browsers. This example shows how to load and instantiate a WebAssembly module asynchronously. Once loaded, you can use the exported functions from the WebAssembly module in your JavaScript code.

This expanded cheatsheet now includes explanations for each code section, providing context and clarification for the concepts presented. It should serve as a more comprehensive reference guide for JavaScript developers at various skill levels.
