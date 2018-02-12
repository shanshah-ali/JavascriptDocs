# This
In JavaScript the thing that called this is object that owns the Javascript code.
The value of this when used in function is the object that owns the function.
The value of this when used in the object is the object itself.

>When used outside of the object this refers to global object.
and also this in the web browser is equal to window
```javascript
console.log(this === window) //true
this.a = 37
console.log(window.a) // 37
```

In function if the value of this is not set by the call this will default to the global object for instance

```javascript
function f1() {
return this;
}
console.log(f1() === window) //true
```

#### But in 'strict mode'
The value of this remain at whatever was set to when enterting the execution context.
```javascript
function f1() {
'use strict'
return this;
}
console.log(f1() === window) //false
```

## Apply Methods
When a function uses the this keyword in its body its value can be bound to particular object in the Call using ***Apply*** or ***Call*** methods

```Javascript
function add(c,d) {
return this.a + this.b + c + d;
}

var o = {a:1, b:3};
add.call(o, 5, 7); //16
add.apply(o, [5, 7]);
```
#### 1. Call
The first parameter of the call is the ***object to use as this*** and other parameters are passed in as an ***argumets in the function call***. So we are going to set ***this to o*** so in function add ***this.a*** has a value of 1 and ***this.b*** has a value of 3.

### 2. apply
apply is almost just like call the main difference is that call accepts an argument list
while apply accepts a single array of arguments

## Bind Method
When you call bind method on a function and pass in an object it creates a new function with the same body in scope as the orignal function.But where this occures in the orignal function in the new function it is permanently bound to the first argument of bind.
This will make more sense with an example.
```Javascript
// we are going to figure out what this is going to refer to
function f() {
return this;
}
/*we created a new variable and set it equal to function f.
But we are going to bind the context of this. And we are going
to pass in the object where a equals to evive. So function f will
return evive
*/
const g = f.bind({a: 'evive'});
const h = g.bind({a: 'health'}); /*won't work a second time because you
can't call bind again on something you've already treated with bind */
const obj = {a: 8, f: f, g: g, h: h};
console.log(o.f(), o.g(), o.h()); // 8 evive evive
/*
1.so o.f(). in function f this in now going to refer to the context of
object obj so a = 8
2. o.g() g has bound this to something else
g has bound a to evive. so instead getting a from obj it will log evive.
That was simple but then what's about h

3. It's not gonna bind second time so it's not going bind health to h
*/
```
### So let's see how this works in arrow functions
>With arrow function. This is bound to the enclosing scope at the creating time and cannot be changes with. ***So the new operator bind call and apply hvae no effect on this.***

```Javascript
const o = {
traditionalFunc: function() {
console.log('TraditionalFunc this === o?' this === o);
},
arrowFunc: () => {
console.log('ArrowFunc this === o?' this === o);
/*The arrow function attached to o was created in the scope of window and
run in the scope of o.
So this arrow function is forever bound to the scope of window where it
was created*/
console.log('ArrowFunc this === window?' this === window);
}
}
o.traditionalFunc(); //true
o.arrowFunc();// false, true
```

## One last thing with *this* keyword
>When a function is called as a method of an object it's this is set to the object the method is called on.
```Javascript
let o = {
value: 'evive',
f: function() {
return this.value;
}
console.log(o.value()) //evive
o = {value: 'evive'};
function independent() {
return this.value;
}
o.f = independent;
console.log(o.f())// evive

```
