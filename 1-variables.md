# Declarations
##### There are three kinds of declarations in JavaScript.
1. var:- Declares a variable, optionally initializing it to a value.
2. let:- Declares a block-scoped, local variable, optionally initializing it to a value.
3. const:- Declares a block-scoped, read-only named constant.

# Variables
You use variables as symbolic names for values in your application.The names of variables, called identifiers, conform to certain rules
1. A JavaScript identifier must start with a letter.
2. Underscore (_), or dollar sign ($); subsequent characters can also be digits (0-9)
3. JavaScript is case sensitive, letters include the characters "A" through "Z" (uppercase) and the characters "a" through "z" (lowercase).

##### Global Vairables
Global variables are in fact properties of global object(window.object)
##### Constant Variables
We can create read-only constants with the ***const*** keyword
```Javascript
const a = 10;
a = 4 // Uncaught TypeError: Assignment to constant variable.

```


 #### Declaring variables
**You can declare a variable in three ways:**
1. With a keyword **var**
    ```Javascript
        var x = 10;
    ```
2. By simply assigning it a value.
    ```Javascript
        x = 10;
    ```
    >If this form is used outside the function, it declares a global variable.It generates a strict JavaScript warning. You shouldn't use this variant.

3. With a keyword let
    ```Javascript
        let x = 10
    ```
    >This syntax can be used to declare a block-scope local variable

#### Evaluating variables
A variable declared using the var and let with no assigned value specified has the value of ***undefined***.
>an attempt to access an undeclared variable results in a ***ReferenceError*** exception being thrown:

```Javascript
var a;
console.log('The value of a is ' + a); // The value of a is undefined

console.log('The value of b is ' + b); // The value of b is undefined
var b;

console.log('The value of c is ' + c); // Uncaught ReferenceError: c is not defined

let x;
console.log('The value of x is ' + x); // The value of x is undefined

console.log('The value of y is ' + y); // Uncaught ReferenceError: y is not defined
let y;
```

#### Variable scope
When you declare a variable ***outside of any function***, it is called a ***global*** variable.
When you declare a variable ***within a function***, it is called a ***local*** variable.

JavaScript before ECMAScript 2015 does not have block statement scope;rather, a variable declared within a block is local to the function
```Javascript
if (true) {
  var x = 5;
}
console.log(x);  // x is 5
```

This behavior changes, when using the let declaration introduced in ECMAScript 2015.
```Javascript
if (true) {
  let y = 5;
}
console.log(y);  // ReferenceError: y is not defined
```

#### Variable hoisting
Another unusual thing about variables in JavaScript is that you can refer to a variable declared later, without getting an exception. This concept is known as ***hoisting***

```Javascript
//example 1
console.log(x === undefined); // true
var x = 3;

//example 2
var myvar = 'my value';

(function() {
  console.log(myvar); // undefined
  var myvar = 'local value';
})();
```
***The above examples will be interpreted the same as:***
```Javascript
//example 1
var x;
console.log(x === undefined); // true
x = 3;

//example2
var myvar = 'my value';

(function() {
  var myvar;
  console.log(myvar); // undefined
  myvar = 'local value';
})();
```

#### Function hoisting
For functions, only the function declaration gets hoisted to the top and not the function expression.
```Javascript
/* Function declaration */
foo(); // "bar"
function foo() {
  console.log('bar');
}

/* Function expression */
baz(); // TypeError: baz is not a function
var baz = function() {
  console.log('bar2');
};
```

***
# Type Coercion
Type coercion means that when the operands of an operator are different types, one of them will be converted to an "equivalent" value of the other operand's type.
```Javascript
console.log(5+true) // 5 this is intger
console.log(10 + '20') // 1020 this is string
console.log(10 - '20') // -10 this is integer
```
The boolean operand will be converted to an integer: false becomes 0, true becomes 1. Then the two values are compared.
