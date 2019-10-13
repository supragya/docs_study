# Javascript
Link: [https://wiki.developer.mozilla.org/en-US/docs/Web/JavaScript/Guide](https://wiki.developer.mozilla.org/en-US/docs/Web/JavaScript/Guide)

**Basic thought**: Everything in javascript is object, objects are passed, used as blueprints, replicated etc.

## First class functions
When functions are treated like variables
```
const foo = function() {
    console.log("xyz");
}
```
This allows passing of function as args
```
function greeting(foo, "name");
```
Allows to return functions as well
```
function say(){
    return function(){
        console.log("Hello from return");
    }
}
```
Hence double paranthesis like `say()()` invokes returned function/

You dont have to be concerned whether methods are public, private or protected or implement interfaces.

## Javascript declarations
1. var: Declares a variable, optionally initto value
2. let: Block-scoped, optionally init to value
3. block-scoped, read only

**NOTE**: JS variables can begin with _ or $ also

## Variable hoisting
```

var a;
console.log(a); //undefined

console.log(b); //undefined - variable hoisting
var b;

console.log(c); //uncaught ReferenceError
let c;

```

Undefined can be tested using ==.
example: `if (input == undefined)`

Variable outside a functino have global scope
```
if (true) {
    var x = 2015;
}
console.log(x); //ok
```

```
if (true) {
    let x = 2015;
}
console.log(x); //wrong
```

**NOTE**: Let and const are hoisted but not initalized, temporal deadzones.

Because of hoisting, all var statements in a function should be placed as near to the top of the function as possible. This best practice increases the clarity of the code.

## Function hoisting
For functions, only declarations get hoisted to the top.

```
foo()
function foo(){
    console.log("Foo");
}
```

This will however not work:
```
foo()
var foo = function() {
    console.log("Foo");
}
```

## Global variables


