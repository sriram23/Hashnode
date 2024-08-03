---
title: "Currying in JavaScript"
datePublished: Sat Aug 03 2024 02:17:41 GMT+0000 (Coordinated Universal Time)
cuid: clzdi7ar1000009l1ci967izj
slug: currying-in-javascript
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1722650989054/6c63d917-26ff-4b8d-a9bf-ab7ffb67a6ac.png
tags: javascript, es6, functional-programming, currying, javascript-functions, closures-in-javascript

---

Currying is a technique in JavaScript, where the function with multiple arguments is transformed into a series of functions, each taking one argument.

## Why Currying?

* **Flexibility**: It allows us to create new functions from existing functions, presetting some arguments and leaving other open.
    
* **Reusability**: Functions can be reused with some arguments pre-filled.
    
* **Simplicity**: It makes easier to code when dealing with complex logics.
    

## How to achieve?

Currying in JavaScript can be achieved in two ways:

* Using **Bind**
    
* Using **Closures**
    

Let us explore both the implementations using a simple multiplication function that takes two parameters `num1` and `num2`. Now I need a function that multiplies a number by two, which means it requires a single parameter and the provided number will be multiplied by 2. Let us use currying to solve this.

### Bind implementation

Let's have a function that multiplies two numbers

```javascript
let multiply = (num1, num2) => {
    return num1 * num2
}
```

This is how we can use currying to implement our second function multiplyBy2.

```javascript
let multiplyBy2 = multiply.bind(this, 2)
```

This is how the functions can be invoked

```javascript
multiply(2, 3) // Returns 6
multiplyBy2(4) // Returns 8
```

### Closure implementation

In case of closure, we will need to have to modify the `multiply` function in such a way that it has an inner function for the second argument.

```javascript
let multiply = function(x) {
    return function(y) {
        return x*y
    }
}
```

Here the inner function has the access to the scope of it's parent function. This is called **closure** in JavaScript. Let's implement our `multiplyBy2` function here.

```javascript
let multiplyBy2 = multiply(2)
```

This is how the functions can be invoked

```javascript
multiply(2)(3) // Returns 6
multiplyBy2(4) // Returns 8
```

This is how Currying can be implemented in JavaScript.

## Use Cases

One real world example where we can use Currying is with logging function implementation. The function will take two arguments Level and Message. We can use Currying to create functions for different log levels. Let us see how we can implement.

```javascript
const logger = (level) => (message) => `[${level}] ${message}`

// Currying
const debug = logger('debug')
const info = logger('info')
const warning = logger('warning')
const error =  logger('error')

// Functions invocation
debug("Checking if the values is coming")  // Returns "[debug] Checking if the values is coming"
info("API called successfully")  // Returns "[info] API called successfully"
warning("Server returned a warning message")  // Retuns "[warning] Server returned a warning message"
error("Something went wrong while calling the API")  // returns "[error] Something went wrong while calling the API"
```

Thank you for reading! Appreciate your time and hope you found this post valuable. Give currying a try in your next JavaScript project and let me know how it improves your coding experience in the comments below!