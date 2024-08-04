---
title: "Mastering Type Coercion in JavaScript"
datePublished: Sun Aug 04 2024 13:59:05 GMT+0000 (Coordinated Universal Time)
cuid: clzfmp5az000y09mecb4o5sk2
slug: mastering-type-coercion-in-javascript
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1722779645547/37dbc17c-0bc4-4f05-bfcc-ee5125ef0fc0.png
tags: js, javascript, type-conversion, javascript-tips, javascript-fundamentals, javascript-type-coercion

---

Type coercion in JavaScript refers to the conversion of one type to another, either explicitly or implicitly. JavaScript is known for being a loosely typed language (sometimes referred to as 'weakly typed,' though I prefer not to use that term 😊). This means that JavaScript variables can hold values of any type without strict type definitions. Consequently, JavaScript often needs to convert variable types when performing operations.

%[https://x.com/RyanEls4/status/1810216892147114307] 

There are two types of Coercions:

1. Explicit
    
2. Implicit
    

# Explicit Coercion

Explicit Coercion is when we manually convert values from one type to another using built-in functions or operators.

**Examples:**

```javascript
// Converting String to Number
const str = "123";
const num = Number(str); // num is 123 (number)

// Converting Number to String
const num = 123;
const str = String(num); // str is "123" (string)

// Converting Boolean to Number
const bool = true;
const num = Number(bool); // num is 1 (number)
```

## Real World Scenarios

### Form Input Validation

In form fields like text box, we will be getting the values as String. Validation for field can be done with explicit type coercion

```javascript
const ageInput = document.getElementById("age").value; // "25"
const age = Number(ageInput); // 25

if (isNaN(age)) {
  alert("Please enter a valid number for age.");
} else {
  console.log(`User's age is ${age}`);
}
```

### Parsing JSON

In some cases, while fetching JSON data from APIs, it will be String, that we need to convert into Object explicitly.

```javascript
const jsonResponse = '{"name": "Sriram", "age": 28}';
const user = JSON.parse(jsonResponse);

console.log(user.name); // "Sriram"
console.log(user.age);  // 28
```

### Handling Local Storage/Session Storage

Local Storage and Session Storage will accept string values only. If we want to store any non-string value like a number, we will have to explicitly convert it to String.

```javascript
const id=189764
sessionStorage.setItem('id', String(id))
```

# Implicit Coercion

Implicit Coercion happens when we try to perform some operations. JavaScript will automatically convert the types in order to perform the operation.

**Examples:**

```javascript
// String Concatenation
const num = 42;
const result = "The answer is " + num; // "The answer is 42"
const str = 5 + " apples"; // "5 apples"

// Arithmetic Operations
const result1 = "5" - 2; // 3 (string "5" is converted to number 5)
const result2 = "6" * 2; // 12 (string "6" is converted to number 6)
const result3 = "10" / 2; // 5 (string "10" is converted to number 10)
const result4 = "10" % 3; // 1 (string "10" is converted to number 10)

// Comparison Operations
const result1 = "10" > 5; // true (string "10" is converted to number 10)
const result2 = "20" < 15; // false (string "20" is converted to number 20)
const result3 = "5" <= 5; // true (string "5" is converted to number 5)
const result4 = "3" >= 2; // true (string "3" is converted to number 3)

// Equality Comparisons
const result1 = 1 == "1"; // true (string "1" is converted to number 1)
const result2 = true == 1; // true (boolean true is converted to number 1)
const result3 = false == 0; // true (boolean false is converted to number 0)
const result4 = null == undefined; // true (both are considered equal)

// Logical Operators
const result1 = "hello" && 0; // 0 (string "hello" is truthy, so returns 0)
const result2 = "" || "default"; // "default" (empty string is falsy, so returns "default")
const result3 = !0; // true (number 0 is falsy, so returns true)
const result4 = !"non-empty string"; // false (non-empty string is truthy, so returns false)
```

## Common Pitfalls

Type coercion may lead to unexpected results, that will lead to bugs. Understanding on how JavaScript handles coercion can help to avoid such errors.

## Best Practices

* Use strict equality (===) and inequality (!==) operators to prevent any unintended type coercion
    
* Make use of explicit type coercion functions/operators wherever we are sure about the type.
    
* Understand the **truthy** and **falsy** values to avoid logical errors.
    
* Use **Typescript**, which makes the language Strongly typed.
    

Thank you for reading! I appreciate your time and hope you found this post valuable. Please let me know your thoughts in the comments below!