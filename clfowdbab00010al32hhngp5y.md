---
title: "Understanding Functions and Callbacks in JavaScript"
datePublished: Fri Mar 24 2023 16:13:20 GMT+0000 (Coordinated Universal Time)
cuid: clfowdbab00010al32hhngp5y
slug: understanding-functions-and-callbacks-in-javascript-f288bf19bc2e
canonical: https://medium.com/javascript-in-plain-english/understanding-functions-and-callbacks-in-javascript-f288bf19bc2e
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/g5jpH62pwes/upload/dd3cc3efc7284f725b57d5891565cb7b.jpeg
tags: functions, javascript, web-development, callback, programming-ciovqvfcb008mb253jrczo9ye

---

Hello World!

Functions are a key feature of JavaScript programming that allows developers to create modular, reusable code. In this post, we’ll explore the basics of functions in JavaScript, including function declarations, function expressions, and named function expressions. We’ll also discuss the concept of callbacks, a powerful technique used in asynchronous programming to manage the flow of execution and to handle events or responses that are not known in advance.

### Functions in JavaScript

A function in JavaScript is a block of code that can be executed on demand. Functions can take input values (called arguments) and can return output values. In JavaScript, functions can be defined using function declarations, function expressions, and arrow functions.

### Function Declarations

A function declaration defines a named function using the following syntax:

```javascript
function functionName(arguments) {
    // function code goes here
    return value;
}
```

The `functionName` is the name of the function, and `arguments` are the parameters that the function takes. The function code goes inside the curly braces and the `return` statement specifies the value that the function should return.

Example:

```javascript
function addNumbers(val1, val2) {
    return val1 + val2;
}
```

### Function Expressions

A function expression defines an unnamed function that is assigned to a variable, using the following syntax:

```javascript
const functionName = function(arguments) {
    // function code goes here
    return value;
};
```

In this case, the function is defined as an anonymous function and is assigned to the variable `functionName`. The function code goes inside the curly braces, and the `return` statement specifies the value that the function should return.

Example:

```javascript
const addNumbers = function(val1, val2) {
    return val1 + val2;
}
```

### Named Function Expressions

A named function expression is similar to a function expression, but it defines a named function that is assigned to a variable, using the following syntax:

```javascript
const func = function functionName(arguments) {
    // function code goes here
    return value;
};
```

The function has a name (`functionName` in this example), which can be useful for debugging.

### Callbacks in JavaScript

A callback is a function that is passed as an argument to another function and is executed by that function when a certain event or condition is met. Callbacks are a powerful technique used in asynchronous programming to manage the flow of execution and to handle events or responses that are not known in advance.

Here’s an example of using a callback in JavaScript:

```javascript
function addNumbers(a, b, callback) {
    const sum = a + b;
    callback(sum);
}

function displayResult(result) {
    console.log('The sum is ' + result);
}

addNumbers(5, 10, displayResult);
```

In this example, we call the `addNumbers` function with two arguments (`5` and `10`) and a callback function `displayResult`. The `addNumbers` function calculates the sum of the two arguments and passes the result to the callback function. The callback function then logs the result to the console.

Functions and callbacks are powerful tools in JavaScript that allow developers to create modular, reusable code and manage asynchronous operations. By understanding the basics of functions and callbacks, developers can create efficient and scalable code that can handle complex operations. In addition, understanding how callbacks work is essential for working with APIs, handling user input, and creating interactive web applications.

That’s all about the functions and callbacks in JavaScript. I hope you found this useful. Thanks for reading!

%%[cta-github-linkedin]