---
layout: post
title: "Notes on Understanding ECMAScript 6"
categories:
  - Book Notes
tags: ecmascript javascript
comments: true
---

Notes on *Understanding ECMAScript 6* written by Nicholas C. Zakas (2016).

{% include toc %}

## Chapter 1: Block Bindings

### `var` Declarations and Hoisting

A variable declared with `var` would be *hoisted* at the top of a function body (or in the global scope, if declared outside of any function). Tha means, only function body will create a new scope for `var` declarations.

```javascript
function foo(condition) {
    if (condition) {
        var value = "hello";
    }
}
```

The above code fragment is equivalent to

```javascript
function foo(condition) {
    var value;
    if (condition) {
        value = "hello";
    }
}
```

### Block-Level Declarations

#### The Temporal Dead Zone

The *temporal dead zone* (TDZ) is used to describe why `let` and `const` bindings are not accessible before their declaration.

```javascript
if (condition) {
    console.log(typeof value); // throws an error
    let value = "blue";
}
```

```javascript
if (condition) {
    console.log(typeof value); // undefined
    var value = "blue";
}
```

When the JavaScript engine meet a new block, it first moves all bindings declared with `let` or `const` into the TDZ, and when the execution flows to a `let` or `const` declaration the engine will remove that binding out from the TDZ. Any attemption to access bindings in the TDZ would throw an error.

This is a very technical aspect of the block-scoping.

## Chapter 2: Strings and Regular Expressions
## Chapter 3: Functions
## Chapter 4: Expanded Object Functionality
## Chapter 5: Destructuring for Easier Data Access
## Chapter 6: Symbols and Symbol Properties
## Chapter 7: Sets and Maps
## Chapter 8: Iterators and Generators
## Chapter 9: Introducing JavaScript Classes
## Chapter 10: Improved Array Capabilities
## Chapter 11: Promises and Asynchronous Programming
## Chapter 12: Proxies and the Reflection API
## Chapter 13: Encapsulating Code with Modules
## Appendix A: Minor Changes in ECMAScript 6
## Appendix B: Understanding ECMAScript 7 (2016)