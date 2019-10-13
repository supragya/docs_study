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
Everything in js is an object, hence global variables (in we) are part of `window` object. Access them using `window.varname`.

## Constants
A constant does not change, however for a few things in js, it acts as a reference too. See below:
```
const MY_OBJ = {'key' : 'value'};
MY_OBJ.key = 'othervalue';
```
The above is valid since `MY_OBJ` is acting as a reference.

## Data structure and types
8 data types - 7 primitive and 1 object type.

7 primitives:
1. `Boolean`: true or false
2. `null`: not equivalent to Null or NULL
3. `undefined`
4. `Number`: Integer or Float
5. `BigInt`: Arbitrary precision Int
6. `String`
7. `Symbol`: new in ECMAscript 2015.

JavaScript is dynamically typed, hence you don't need to specify.
`str = "This is me"` is a string
`str = "Number: " + 42` is a string
`num = 42 - 7` is a number

## Converting string to number
Use `parseInt()` and `parseFloat()`. Both need a string as an argument.

## Literals
1. `Array`: `var coffee = ['cof1', 'cof2'];`
2. `Boolean`
3. `Numeric`: You can use `0x`, `0o` or `0b` before numbers also to denote base
4. `Floating point`
5. `Object`: Anything of the form `x = {}` with one or more than one pairing inside `{}`
    Property names that are not valid identifiers also cannot be accessed as a dot (.) property, but can be accessed and set with the array-like notation("[]").
6. `RegExp`: Enclosed between slashes. `/ab+c/`
7. `String`: Enclosed between double quotes or single quotes.



