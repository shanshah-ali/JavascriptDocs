

## var

 - var keyword assigns a function scope to the variable.

## let

 - The let keyword declares a variable that is strictly scoped to the current block, statement or expression where it is defined.
 
 ```
var a = 1;
{
let b = 2;
console.log(b); // 2
}
console.log(a); // 1
console.log(b); // ReferenceError, b is undefined
```
## const

 - Constants are immutable variables i.e., variables which cannot be re-assigned new content. 
 ```
const foo = 'foo';
foo = 'bar'; // TypeError: Assignment to constant variable.
```
    
 -  This only makes the variable itself immutable, not its assigned content (for instance, in case the content is an object, this means the object itself can still be altered).
 ```
 const foo = {a: 1};
 console.log(foo.a); // 1
foo.a = 2;
console.log(foo.a); // 2
 ```

 - A constant requires an initializer. This means constants must be initialized during its declaration.
## Arrow Functions

 - Functions that are not bound to an identifier (function name) are called as *anonymous functions* and *Arrow functions*(Lamda functions) are a concise mechanism to represent anonymous functions.
 - There are 3 parts to a Arrow function −

	 - Parameters − A function may optionally have parameters.

	 - The fat arrow notation (=>): It is also called as the goes to operator.

	 - Statements − Represents the function’s instruction set.
	 

 - Examples: 

	 - When the arrow function body is a **single expression** it is implicitly returned.

		``var add = (a,b) => a+b;``
		
	- When the arrow function has only **one argument** the parenthesis around the parameters can be omitted.

		```
		var materials = [
		  'Hydrogen',
		  'Helium',
		  'Lithium',
		  'Beryllium'
		];
		materials.map(material => console.log(material)); 
		/* Output: 
			"Hydrogen"
			"Helium"
			"Lithium"
			"Beryllium"
		*/

	- When the arrow function has **no arguments** you need an empty parenthesis ().
	`` var random = () => Math.random();``
	- When the arrow function body has **multiple expressions** then they must be wrapped in {} and the return statement may not be omitted.
		```
		var shout = s => {
			s = s.toUpperCase();
			s = s + '!';
			return s;
        }
		```

	

## Destructuring

 Destructuring is a convenient way of extracting multiple values from data stored in (possibly nested) objects and Arrays. 
 
  **Object Destructuring**
	   

 - The following example, we use destructuring in a variable declaration (line (A)). It declares the variables f and l and assigns them the values 'Jane' and 'Doe'.
  ```
  let obj = { first: 'Jane', last: 'Doe' };
let { first: f, last: l } = obj; //(A)
    // f = 'Jane'; l = 'Doe'
  ```

 - A shorthand syntax can be used when the desired local variable names are the same as the object keys in the data. This has the benefit of not having to name target keys twice .
```
var data = {
  foo: 'foo',
  bar: 'bar'
};

var {foo,bar} = data;

foo; // 'foo'
bar; // 'bar'
```
**Array Destructuring**
```
var data = ['foo','bar',['baz']];

var [foo,bar,[baz]] = data;

foo; // 'foo'
bar; // 'bar'
baz; // 'baz'
```

## Spread Operator

 - The spread operator ... can be used to destructure arrays, other iterables and objects. It is used to catch remaining properties not already picked off by the destructuring pattern, ie.,capture all remaining parameters passed  and expose them as an array. 

```
const array = [1, 2, 3, 4];
const [first, ...theRest] = array;
console.log(first, theRest); // 1 [2,3,4]
```

 - The spread operator ... can be used to unpack an array into its elements in order to be passed into a function as individual arguments.
 ```
 function f (a,b,c) {
  console.log(a,b,c); // 1 2 3
};

var values = [1,2,3];
f(...values); 
 ```

 - Spread parameters can also be mixed and matched with normal function parameters.
```
function f (a,b,c,d) {
  console.log(a,b,c,d); // 1 2 3 4
};

var values = [2,3];
f(1,...values,4); 
```
## Template Literals

 - Template literals allow embedded expressions.
 - Template literals are enclosed by the back-tick ``   instead of double or single quotes.
 - Template Literals can contain placeholders for string substitution using the ${ } syntax, as demonstrated below:

```
var name = "Brendan";
console.log(`Yo, ${name}!`); // "Yo, Brendan!"
```

 - For multiline strings: 
  ```
 console.log(`string text line 1
string text line 2`);
// "string text line 1
// string text line 2"
```
 - Embed expressions using template literals : 
 ```
 var a = 5;
var b = 10;
console.log(`Result is:  ${a + b}`); // "Result is 15"
 ```

