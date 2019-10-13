# Javascript
Link: [https://wiki.developer.mozilla.org/en-US/docs/Web/JavaScript/Guide](https://wiki.developer.mozilla.org/en-US/docs/Web/JavaScript/Guide)

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


