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


## Quirks
### Arrays and commas

```
var myList = ['home', , 'school', ];
```
Commas in middle mean they are `undefined`.
However last comma at the end may be ignored


### Objects
Inside the objects, you can look as follows: `obj.value`. However sometimes this may not work. In those cases, use `obj['value']`.

### Multiline strings
Use backquotes to have multiline strings.
Such as:
```
var name = `This is one line
            This is another line`
```

### String interpolation
Can be done using `${varname}` addition. Such as:
```
var str = "Hello ${name}, how are you today?"
```

## Control statements:
1. if else
2. switch
3. try catch throw finally
4. for loop 
5. do while
6. while
7. break, continue
8. for in `for (let i in obj)`
9. for of

## Defining functions
There are two ways to define function: function declarations and function expresssion
### Function declaration
General form:
```
function square(number) {
    return number * number;
}
```
Primitive params are passed to function **by value**. The value does not change if the function tries to change it.
However, if you pass an object or something like an array, it is passed **by reference** and function has the ability to change it.

### Function expressions
Anonymous functions without a name
```
var square = function(number) {
    return number * number;
}
```
Function expressions are convenient way to pass the function as an argument.

In JS, a function can be defined based on a condition as well. Following function defines only if `num==0`:
```
var myFunc;
var num = 2;
if (num == 0) {
    myFunc = function () {
        console.log("Hello there");
    }
}
```

## Other things about function
`var` have a function scope and are hoisted.
```
var foo = function bar() {
    // things
}
```
within the function body, all three below can be used to reference itself:
1. `foo()`
2. `bar()`
3. `arguments.callee()`

## Nested functions and closures
You can nest function withing the function.
The inner function is private to containing function.
It also forms a closure.
    The inner function can use the vars and args of outer function
    The outer function cannot use the vars and args of inner function
Closure example:
```
function outer(x) {
    function inner(y) {
        return x+y;
    }
    return inner;
}
fn_inside = outer(3); //Gives access to inner with 3 are a parameter already
console.log(fn_inside(5)); // 8
console.log(outer(3)(5)); // 8
```
A new closure is created everytime a call to `outside` is done. The memory can be freed only when the access to `inner` is not longer available.

## Scope and name conflicts
When multiscope access to variable is available, the innermost scope takes precedence.



