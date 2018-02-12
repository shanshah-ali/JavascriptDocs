# Functions
A function is a set of statements that perform a task or calculates a value.

### Defining functions
##### Function declarations
A function definition (also called a function declaration, or function statement) consists of the function keyword, followed by:
* The name of the function.
* A list of parameters to the function, enclosed in parentheses and separated by commas
* The JavaScript statements that define the function, enclosed in curly brackets, { }.

```
    function square(number, number2) {
        return number * number2;
}
```

##### Function expressions
While the function declaration above is syntactically a statement, functions can also be created by a function expression.Such a function can be **anonymous**; it does not have to have a name. For example, the function square could have been defined as:

```
    var square = function (number) {
        return number * number;
    }
    var x = square(5); // 25
```

##### Calling functions
Defining a function does not execute it. Defining the function simply names the function and specifies what to do when the function is called.To execute a function u need to call it with parameters
```
    square(5);
```

### Function scope
1. Variables defined inside the function can't be accessed anywhere outside the function, because the variable is defined only in the scope of function.
2. function can access all the variable and functions defined inside the scope in which it is defined.
3. A function defined inside another function can also access all the variable of its parent.

```
    //variables defined in global scope

    var num = 20,
        num2 = 10,
        num3 = 30;

    // This function is defined in the global scope
    function sum() {
        return(num + num2 + num3)
    }
    sum(); // Return 60

    // A nested function example
        function getScore() {
            var num = 3,
            num2 = 2;
            function add() {
                return num + num2;
            }
            add(); //Return 5
        }

```
### Nested functions and closures
You can nest a function inside a function. Nested function in private to its containing(outer) function.It also forms a closure.
 A closure is an expression (typically a function) that can have free variables together with an environment that binds those variables

 **To summarize**
 1. The inner function can be accessed only from statements in the outer function
 2. The inner function forms a closure: the inner function can use the arguments and variables of the outer function, while the outer function cannot use the arguments and variables of the inner function.
 ```
    const addSquare = (a,b) => {
        const square = x => x*x;
        return square(a) + square(b);
    }
    addSquare(2,2)// Return 8
 ```

 #### Preservation of variables
```
const outside = x => {
    const inside = y => x + y;
  return inside;
 }
 fn_inside = outside(5);
 result = fn_inside(5);
 result1 = outside(3)(5);

```
>Notice how x is preserved when inside is returned. A closure must preserve the arguments and variables in all scopes it references.
The memory can be freed only when the returned inside is no longer accessible.

## Closures
 JavaScript allows for the nesting of functions and grants the inner function full access to all the variables and functions defined inside the outer function.
 However, the outer function does not have access to the variables and functions defined inside the inner function.
 Since the inner function has access to the scope of the outer function, the variables and functions defined in the outer function will live longer than the duration of the inner function execution, if the inner function manages to survive beyond the life of the outer function.
 ***So when  closure is created***
A closure is created when the inner function is somehow made available to any scope outside the outer function.
```
var createPet = function(name) {
  var sex;

  return {
    setName: function(newName) {
      name = newName;
    },

    getName: function() {
      return name;
    },

    getSex: function() {
      return sex;
    },

    setSex: function(newSex) {
      if(typeof newSex === 'string' && (newSex.toLowerCase() === 'male' ||
        newSex.toLowerCase() === 'female')) {
        sex = newSex;
      }
    }
  }
}

var pet = createPet('Vivie');
pet.getName();                  // Vivie

pet.setName('Oliver');
pet.setSex('male');
pet.getSex();                   // male
pet.getName();                  // Oliver
```
