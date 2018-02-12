# Conditional statements
A conditional statement is a set of commands that executes if a specified condition is true. JavaScript supports two conditional statements: if...else and switch.

### if-else statements
Use the if statement to execute a statement if a logical condition is true. Use the optional else clause to execute a statement if the condition is false
>if (condition) {
    statement_1;
} else {
  statement_2;
}

***Here the condition can be any expression that evaluates to true or false***

##### Falsy values
* false
* undefined
* 0
* null
* NaN
* the empty string("")

>All other values, including all objects, evaluate to true when passed to a conditional statement.

**Do not confuse the primitive boolean values true and false with the true and false values of the Boolean object. For example:**

```Javascript
    var b = new Boolean(false);
    if (b) // this condition evaluates to true
    if (b == true) // this condition evaluates to false
```

### switch statement
A switch statement allows a program to evaluate an expression and attempt to match the expression's value to a case label. If a match is found, the program executes the associated statement.
```Javascript
switch(expression) {
    case label_1:
        statement_1:
        [break;]
    case label_2:
        statement_2:
        [break;]
        ...
    default:
    statements_def
    [break;]
}
```
